API
===
Open Orchestra fournit une API REST pour accéder aux différentes entités du CMS (pages, contenus, sites, etc).
Afin de découpler le stockage des données et leur exposition dans l'API, Open Orchestra implémente
le `design pattern facade <https://en.wikipedia.org/wiki/Facade_pattern>`_.

Le design pattern *facade* se découpe en deux parties: Tout d'abord les *facades* qui sont des objets avec
différent attributs qui seront ceux exposés par l'API;
puis les *transformer*, qui à partir des données provenant de la base de données remplissent une *facade*.

Les *transformer* permettent aussi de retourner une entité,
qui pourra être stockée, depuis les données d'une *facade*.

.. image:: /images/api/pattern_facade.png
    :align: center
    :alt: Pattern facade

Exposer une entité
------------------

Supposons que vous construisiez une application `todo list` qui devra afficher
différentes tâches. Vous disposez d'une classe `Task` qui représente et stocke les données
d'une tâche.

.. code-block:: php

    // src/AppBundle/Entity/Task.php
    namespace AppBundle\Entity;

    class Task
    {
        protected $title;
        protected $dueDate;

        // ... getters
        // ... setters
    }

Dans un premier temps, il faut créer la classe qui représente la *facade*. Celle-ci doit
implémenter ``OpenOrchestra\BaseApi\Facade\FacadeInterface`` afin d'être reconnue par Open Orchestra
comme étant une *facade*.

.. code-block:: php

    // src/AppBundle/Facade/TaskFacade.php
    namespace AppBundle\Facade;

    use OpenOrchestra\BaseApi\Facade\FacadeInterface;

    class TaskFacade implements FacadeInterface
    {
        public $title;
        public $dueDate;
    }

Afin de remplir cette *facade* à partir des données de l'entité ``AppBundle\Entity\Task``, il faut créer
le *transformer* qui doit étendre la classe abstraite ``OpenOrchestra\BaseApi\Transformer\AbstractTransformer``.

.. code-block:: php

    // src/AppBundle/Transformer/TaskTransformer.php
    namespace AppBundle\Transformer;

    use OpenOrchestra\BaseApi\Transformer\AbstractTransformer;

    class TaskTransformer extends AbstractTransformer
    {
        // Rempli les différents attributs de la facade
        // avec ceux stockés dans la tâche ($task)
        public function transform($task)
        {
            $facade = new TaskFacade();
            $facade->title = $task->getTitle();
            $facade->dueDate = $task->getDueDate();

            return $facade;
        }

        // Créé une tâche à partir des données de la facade
        public function reverseTransform($taskFacade)
        {
            $task = new Task();
            $task->setTitle($taskFacade->title);
            $task->setDueDate($taskFacade->dueDate);

            return $task;
        }

        // Nom du transformer afin de l'identifier lors de son utilisation
        public function getName()
        {
            return 'task_transformer';
        }
    }

Afin de limiter les dépendances et faciliter l'utilisation des *transformer*
dans le reste de l'application, il faut enregistrer le *transformer* en tant que
service *taggé*.


.. code-block:: yaml

    app_bundle.transformer.task:
        class: AppBundle\Transformer\TaskTransformer
        tags:
            - { name: open_orchestra_api.transformer.strategy }

Le *transformer* ``TaskTransformer`` peut être maintenant appelé en utilisant le
``TransformerManager``.

Le ``TransformerManager`` est un service qui connaît tous les *transformer* de l'application.
Cela permet de simplifier les appels à ces derniers.

.. code-block:: php

    // src/AppBundle/Controller/Api/TaskController.php
    namespace AppBundle\Controller;

    class TaskController extends Controller
    {
        public function showAction()
        {
            // Création d'un object tâche
            // celui-ci pourrais aussi provenir d'une base de données
            $task = new Task();
            $task->setTitle('test');

            // Transformation de l'object Task en facade
            // en utilisant le transformer manager
            //
            // task_transformer est le nom du transformer défini par la
            // méthode getName de AppBundle\Transformer\TaskTransformer
            $facade = $this
                ->get('open_orchestra_api.transformer_manager')
                ->get('task_transformer')
                ->transformer($task);
        }
    }

Sérialisation
-------------

Afin de retourner une réponse JSON, la *facade* doit être sérialisée. Pour cela Open Orchestra
utilise le bundle `JMSSerializerBundle <http://jmsyst.com/bundles/JMSSerializerBundle>`_.

Afin de sérialiser la *facade*, il faut indiquer à ``JMSSerializerBundle`` le type des différentes propriétés.


.. code-block:: php

    // src/AppBundle/Facade/TaskFacade.php
    namespace AppBundle\Facade;

    use OpenOrchestra\BaseApi\Facade\FacadeInterface;
    use JMS\Serializer\Annotation\Type;

    class TaskFacade implements FacadeInterface
    {
        /**
         * @Type("string")
         */
        public $title;

        /**
         * @Type("DateTime")
         */
        public $dueDate;
    }

.. caution::

    Les annotations sont mises en cache. Il faut donc vider ce dernier après modification des annotations
    d'une *facade*.

.. tip::

    L'utilisation des `annotations <http://jmsyst.com/libs/serializer/master/reference/annotations>`_
    n'est pas obligatoire. ``JMSSerializerBundle`` supporte aussi la configuration
    en `YAML <http://jmsyst.com/libs/serializer/master/reference/yml_reference>`_
    ou `XML <http://jmsyst.com/libs/serializer/master/reference/xml_reference>`_.

Une fois la configuration effectuée, nous pouvons utiliser le service ``jms_serializer`` afin de sérialiser
la *facade* en JSON.

.. code-block:: php

    // src/AppBundle/Controller/Api/TaskController.php
    namespace AppBundle\Controller;

    class TaskController extends Controller
    {
        public function showAction()
        {
            $task = new Task();
            $task->setTitle('test');

            $facade = $this
                ->get('open_orchestra_api.transformer_manager')
                ->get('task_transformer')
                ->transformer($task);

            // appel au service JMSSerializerBundle
            $serializer = $container->get('jms_serializer');

            // sérialisation de la *facade* en JSON
            $content = $serializer->serialize($facade, 'json');

            // Création d'une réponse Symfony
            return  new Response(
                serializer
                200,
                array('content-type' => 'application/json')
            )
        }
    }

.. tip::

    Open Orchestra propose de créer automatiquement une `Response` JSON à partir d'
    une *facade* retournée par une action de `Controller` grâce à l'annotation
    ``OpenOrchestra\BaseApiBundle\Controller\Annotation\serialize``.

    .. code-block:: php

        // src/AppBundle/Controller/Api/TaskController.php
        namespace AppBundle\Controller;

        use OpenOrchestra\BaseApiBundle\Controller\Annotation as Api;

        class TaskController extends Controller
        {
            /**
             * @Api\Serialize()
             */
            public function showAction()
            {
                $task = new Task();
                $task->setTitle('test');

                $facade = $this
                    ->get('open_orchestra_api.transformer_manager')
                    ->get('task_transformer')
                    ->transformer($task);

                return $facade;
            }
        }

    Si l'annotation est placée directement sur la classe alors tous les retours des actions du `Controller`
    seront sérialisés.

Contexte de sérialisation
-------------------------

Lorsque l'API d'une application Open Orchestra devient conséquente, il peut être intéressant
de sérialiser/transformer suivant le contexte de l'action uniquement certains éléments d'une *facade*.

Pour cela, Open Orchestra fournit l'annotation ``OpenOrchestra\BaseApiBundle\Controller\Annotation\Groups``
qui permet de spécifier un groupe de contexte pour l'action courante.


    .. code-block:: php

        // src/AppBundle/Controller/Api/TaskController.php
        namespace AppBundle\Controller;

        use OpenOrchestra\BaseApiBundle\Controller\Annotation as Api;

        class TaskController extends Controller
        {
            /**
             * @Api\Serialize()
             *
             * Indique que l'action "show" a pour contexte le groupe SHOW
             * @Api\Groups({"show_dueDate"})
             */
            public function showAction()
            {
                // ...
            }
        }

.. tip::

    Pour simplifier et centraliser les différents contextes de l'API, il est conseillé d'utiliser
    des constantes.

    .. code-block:: php

        /**
         * @Api\Serialize()
         *
         * @Api\Groups({"AppBundle\Context\ApiContext::SHOW_DUE_DATE"})
         */
        public function showAction()
        {
            // ...
        }

Le contexte d'une action peut être utilisé dans les *transformer* grâce à la méthode ``hasGroup($group)``

.. code-block:: php

    // src/AppBundle/Transformer/TaskTransformer.php
    namespace AppBundle\Transformer;

    use OpenOrchestra\BaseApi\Transformer\AbstractTransformer;

    class TaskTransformer extends AbstractTransformer
    {
        // Rempli les différents attributs de la facade
        // avec ceux stockés dans la tâche ($task)
        public function transform($task)
        {
            $facade = new TaskFacade();
            $facade->title = $task->getTitle();

            // l'attribut dueDate sera ajouté à la facade uniquement
            // si l'action qui demande la transformation appartient au groupe
            // show_dueDate sinon il ne sera pas ajouté à la facade et donc ne
            // sera pas sérialisé
            if ($this->hashGroup("show_dueDate")) {
                $facade->dueDate = $task->getDueDate();
            }

            return $facade;
        }

        // ...
    }

Désérialisation
---------------

L'API permet aussi d'effectuer des modifications sur les entités à partir de données JSON fournies par
l'application Javascript.

Pour cela, il faut utiliser la méthode `deserialize`` du service `jms_serializer`, afin de remplir une
*facade* à partir des données d'une requête.

Ensuite, afin d'obtenir une entité à partir de la *facade* nous pouvons utiliser la méthode `reverseTransform`
des *transformers*.

.. code-block:: php

    // src/AppBundle/Controller/Api/TaskController.php
    namespace AppBundle\Transformer;

    class TaskController extends Controller
    {
        public function editAction(Request $request)
        {
            // Désérialisation du contenu de la requête
            // dans la facade TaskFacade
            $facade = $this
                ->get('jms_serializer')
                ->deserialize(
                    $request->getContent(),
                    'AppBundle\Facade\TaskFacade',
                    $request->get('_format', 'json')
                );

            // Utilisation du transformer manager pour récupérer
            // le transformer task
            // @see AppBundle\Transformer\TaskTransfomer
            $task = $this
                ->get('open_orchestra_api.transformer_manager')
                ->get('task_transformer')
                ->reverseTransform($facade);

            // ...
            // Validation de l'entité task
            // Sauvegarde de l'entité
        }
    }
