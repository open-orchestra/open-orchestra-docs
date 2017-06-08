Client Javascript
=================

Le Back office d'Open Orchestra est réalisé intégralement en JavaScript, plus précisément
en `ECMAScript 6 <http://es6-features.org/#Constants>`_,
avec le framework `Backbone.js <http://backbonejs.org/>`_

Application
-----------

Open Orchestra est composé d'une application principale et de sous-application qui apportent des
fonctionnalités supplémentaires comme par exemple la gestion de la médiathèque.

Application principale
^^^^^^^^^^^^^^^^^^^^^^

L'application principale est le point d'entrée du Back office, elle est représentée par l'objet ``Application``
se trouvant dans ``BackofficeBundle/Resources/public/ecmascript/OpenOrchestra/Application/Application.js``.

Afin de démarrer l'application, il suffit de faire appel à la méthode ``run()`` de cet objet qui
va initialiser les différents éléments nécessaires.

.. code-block:: javascript

    // BackofficeBundle/Resources/public/ecmascript/OpenOrchestra/Application/Application.js

    class Application
    {
        // ...

        /**
         * Run Application
         */
        run() {
            // Initialisation des paramètres de configuration
            // de l'application
            this._initConfiguration();

            // ...

            // Initialisation des différents routeurs Backbone
            this._initRouter();

            // Événement lancé avant le démarrage de l'application
            Backbone.Events.trigger('application:before:start');

            // Initialisation des layouts de l'application (menu, header, etc)
            this._initLayoutView();

            // Démarrage de l'application
            Backbone.history.start();

            // Événement lancé après le démarrage de l'application
            Backbone.Events.trigger('application:after:start');
        }

        // ...
    }

Sous-application
^^^^^^^^^^^^^^^^

Open Orchestre est découpé en différents bundles Symfony qui apportent chacun leur lot de fonctionnalités.
Ainsi, chaque bundle peut posséder une sous-application Javascript pour ajouter des fonctionnalités
à l'application principale.

Pour instancier une sous-application, il suffit d'utiliser l'événement ``application:before:start`` qui est
lancé juste avant le démarrage de l'application principale.

.. code-block:: javascript

   // src/AppBundle/Resources/public/main.js

   // Objet représentant la sous-application
   import AppSubApplication from './Application/AppSubApplication'

   $(() => {
        Backbone.Events.on('application:before:start', () => {
           // Démarrage de la sous-application (router, ajout de configuration, etc)
           AppSubApplication.run();
        });
   });

Structure
^^^^^^^^^

L'application principale et les sous-applications d'Open Orchestra présentes dans le dossier ``Ressources\public``
des bundles utilisent la même structure.


.. code-block:: yaml

    ├── Ressources/public
        │
        ├── config  # Fichiers json de configuration de l'application (menu, etc)
        │
        ├── ecmascript # Classe Javascript es6 de l'application
        │   │
        │   ├── OpenOrchestra # "Namespace"
        │       │
        │       ├── Application
        │       │    ├── Collection # Collections backbone
        │       │    ├── Model      # Models backbone
        │       │    ├── Router     # Routeurs backbone
        │       │    ├── Views      # Vue Backbones
        │       │
        │       ├── Service # Classes génériques,
        │       │           # utilisées par différents éléments de l'application
        │       │
        │       ├── main.js # Démarrage de l'application ou sous-application
        │
        ├── template # template underscore

Backbone.js
-----------

.. caution::

    Cette section considère que vous maîtrisez `Backbone.js <http://backbonejs.org/>`_

ECMAScript 6
^^^^^^^^^^^^

En ECMAScript 6, il n'est pas possible de définir des propriétés de classe en dehors des méthodes.
Or les différents composants de Backbone.js (View, Model) doivent définir divers propriétés de classe
(tagName, className).

Ainsi, les différents composants de Backbone.js on été étendus afin d'ajouter une méthode ``preinitialize``
pour définir ces propriétés.

    .. code-block:: javascript

        class CustomView extends Backbone.View {

            preinitialize() {
                this.tagName = "li";
                this.className = "custom-class";
            }

            initialize() {
                //...
            }

            render() {
                //...
            }
        }


    .. note::

        L'ajout de la méthode ``preinitialize`` est une `fonctionnalité <https://github.com/jashkenas/backbone/pull/3827>`_
        qui sera ajoutée dans la version 1.4 de Backbone.js

Composants Backbone.js
^^^^^^^^^^^^^^^^^^^^^^

Les différents composants de Backbone.js on été étendus afin d'ajouter
des comportements spécifiques à Open Orchestra
(rendu de template dans les vues, gestion des erreurs lors des appels API, ...).


Ainsi lorsque vous désirez créer un *model*, *router*, *collection*, *view*,  il est préférable
d'étendre les composants Open Orchestra.


.. code-block:: javascript

    // src/AppBundle/Resources/public/MyApp/Application/View/AppView.js
    import OrchestraView from '../../../../OpenOrchestra/Application/View/OrchestraView'
    class AppView extends OrchestraView {}

    // src/AppBundle/Resources/public/MyApp/Application/Router/AppRouter.js
    import OrchestraView from '../../../../OpenOrchestra/Application/Router/OrchestraRouter'
    class AppRouter extends OrchestraRouter {}

    // src/AppBundle/Resources/public/MyApp/Application/Collection/AppCollection.js
    import OrchestraView from '../../../../OpenOrchestra/Application/Collection/OrchestraCollection'
    class AppCollection extends OrchestraCollection {}

    // src/AppBundle/Resources/public/MyApp/Application/Model/AppModel.js
    import OrchestraView from '../../../../OpenOrchestra/Application/Model/OrchestraModel'
    class AppModel extends OrchestraModel {}

Routes Symfony
--------------

Pour faciliter l'utilisation de l'API, au sein de l'application JavaScript,
vous pouvez accéder aux routes Symfony grâce au bundle `FOSJsRoutingBundle <https://symfony.com/doc/current/bundles/FOSJsRoutingBundle/index.html>`_

.. note ::

    La génération des routes en JSON est géré par Open Orchestra
    grâce à une tâche Grunt.

.. caution ::

    Afin que le bundle prenne en compte les routes des contrôleurs celles-ci doivent posséder l'option ``expose = true``,
    plus d'informations dans la `documentation <https://symfony.com/doc/current/bundles/FOSJsRoutingBundle/index.html>`_.

Traductions Symfony
-------------------

Pour faciliter, la gestion des traductions dans l'application JavasSript, vous pouvez
utiliser le `composant de traduction de Symfony <https://symfony.com/doc/current/components/translation.html>`_ .

Afin d'accéder aux traductions en Javascript Open Orchestra utilise le bundle
`JsTranslationBundle <https://github.com/willdurand/BazingaJsTranslationBundle/blob/master/Resources/doc/index.md>`_

.. note ::

    Le domaine de traduction qui est exposé par défaut sur Open Orchestra est ``interface``.


.. note ::

    La génération des traductions en Javascript est géré par Open Orchestra
    grâce à une tâche Grunt.


Template
--------

Au sein des vues, Open Orchestra utilise les `templates Underscore <http://underscorejs.org/#template>`_ .

Pour simplifier le chargement et l'utilisation des différents templates, Open Orchestra met en place
le service ``TemplateManager`` qui permet de récupérer un template underscore à partir de son nom.

.. note ::

    Les différents templates sont automatiquement compilés par une tâche Grunt dans
    la variable ``Orchestra.Template``.

    Pour que vos template soient compilés par Grunt, il faut que celui-ci se trouve dans le dossier
    template des ressources publiques de votre bundle (exemple : ``src/AppBundle/Resources/public/template``)

Le ``TemplateManager`` est directement accessible dans les vues Backbone.Js, si celles-ci étendent bien
``OrchestraView`` grâce à la méthode ``_renderTemplate(templateName, parameters)``.


.. code-block:: javascript

    // src/AppBundle/Resources/public/MyApp/Application/View/AppView.js
    import OrchestraView from '../../../../OpenOrchestra/Application/View/OrchestraView'

    class AppView extends OrchestraView {

        // ...

        render() {
            let template = this._renderTemplate('helloView', {
                name: 'Foo'
            });
            this.$el.append(template);
        }
    }

.. code-block:: text

    <!-- src/AppBundle/Resources/public/template/helloView._tpl.html -->

    <p> Hello <%- name %> </p>


.. note ::

    Lors du rendu d'un template la méthode ``_renderTemplate`` injecte automatiquement le paramètre
    ``renderTemplate`` qui permet d'injecter un template à l'interieur d'un autre template.

    .. code-block:: text

        <!-- src/AppBundle/Resources/public/template/helloView._tpl.html -->

        <p> Hello <%- renderTemplate('otherTemplate') %> </p>


Grunt
-----

Afin de gérer les différentes ressources (JavaScript, CSS) Open Orchestra utilise
`Grunt <https://gruntjs.com/>`_.

Il y a deux tâches Grunt importantes:

La tâche ``css`` qui s'occupe de compiler et
concaténer les fichiers ``less`` des différents bundles se trouvant dans ``/Ressources/public/less``.

Puis la tâche ``javascript`` qui s'occupe de gérer tous les éléments nécessaires pour l'application
JavaScript (compilation des fichiers js, exposition des traductions et des routes, compilation des templates
underscores)

Ces deux tâches ne s'appliquent pas sur tous les bundles/vendors Symfony, il faut spécifier à Grunt les différents
bundles qui doivent être parcourus. Pour cela, il faut les indiquer dans le fichier de configuration ``application.config.js``.

.. code-block:: javascript

    // grunt/targets/application.config.js

    module.exports = {
        application : {
            // Listes des différents bundles qui seront parcourus par les tâches css et javascript
            bundles: [
                'openorchestrabackoffice',
                'openorchestrauseradmin',
                'openorchestragroup',
                'openorchestralog',
                'openorchestraworkflowadmin',
                'openorchestramediaadmin'
            ],
            dest: {
                template : 'web/built/', //web/build/template/template.js
                menu : 'web/built/', //web/build/menu/menu.js
                javascript : 'web/built/openorchestra/' // emplacement ou sera compiler les différents javascript
            }
        }
    };

Ainsi lorsque vous ajoutez une sous-application JavaScript, il faut bien penser à ajouter
le bundle Symfony qui contient votre sous-application à la configuration de Grunt.


Menu de navigation
------------------

Avec Open Orchestra, les différents éléments du menu sont gérés grâce à une configuration JSON.

Cette configuration JSON doit se trouver dans le fichier ``Ressources/public/config/menu.json`` de votre
bundle. Les fichier ``menu.json`` des différents bundles sont rassemblés en un seul fichier (par défaut
``web/build/menu/menu.js``)grâce a une tâche grunt.

Par exemple, voici la configuration pour ajouter une sous-entrée dans le menu ``contribution``:

.. code-block:: javascript

    // src/AppBundle/Resources/public/config/menu.js
    {
      "contribution": { // Nom du menu parent de niveau 1 (contribution, configuration, platform, developer)
        "monMenu": {
          "template": "Menu/Contribution/monMenu",  // Template underscore utilisé pour le rendu
          "rank": 0 // rang du menu par rapport au autre entrée
        },
      }
    }

.. code-block:: text

    <!-- src/AppBundle/Resources/public/template/Menu/contribution/monMenu._tpl.html -->

    <li>
        <a href="#<%- Backbone.history.generateUrl('monMenu') %>" id="navigation-mon_menu">
            Mon menu
        </a>
    </li>


Surcharges
----------

Pour des besoins spécifiques à un projet, il peut être nécessaire de surcharger une classe (Model, View, Router, etc)
JavaScript définis par Open Orchestra.

Afin de surcharger une classe JavaScript sur Open Orchestra, il faut bien comprendre comment sont compilés et concaténés
les différents fichiers de l'application et des sous-applications JavasScript par la tâche Grunt.

Avant de concaténer les différents fichiers la tâche Grunt les copies tous dans
un même dossier (par défaut ``web/built/openorchestra/js``, cf la configuration Grunt).

Par exemple, si l'on prend deux fichiers de deux sous-applications JavaScript différentes

``BackofficeBundle/Resources/public/ecmascript/OpenOrchestra/Application/View/AreaView.js````

et

``MediaAdminBundle/Resources/public/ecmascript/OpenOrchestra/Application/View/MediasView.js``

lors de l'exécution de la tâche Grunt, ils seront tous les deux déplacés dans le même dossier

``web/built/openorchestra/js/OpenOrchestra/Application/View/``

.. note ::

    L'ordre dans lequel les fichiers des applications sont copiés est défini par l'ordre de
    chargement des bundles fourni dans la configuration de Grunt (``grunt/targets/application.config.js``)

Ainsi, si il y a besoin de surcharger un fichier javascript, il suffit de mettre le nouveau fichier
dans la même structure de dossier dans la sous-application et de modifier
la configuration Grunt (``grunt/targets/application.config.js``) pour charger
son bundle après celui que l'on désire surcharger.

Par exemple si l'on veut surcharger
``BackofficeBundle/Resources/public/ecmascript/OpenOrchestra/Application/View/AreaView.js``,
il suffit de créer un fichier ``AreaView.js`` dans la même structure de dossier dans votre sous-application
JavaScript, c'est à dire ``AppBundle/Resources/public/ecmascript/OpenOrchestra/Application/View/AreaView.js``.
