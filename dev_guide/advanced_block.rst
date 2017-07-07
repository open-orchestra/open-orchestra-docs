Bloc, utilisation avancée
=========================

Présentation des concepts
-------------------------

Suite à la documentation sur les blocs, nous allons revenir sur un certain nombre de
fonctionnalités importantes de ces derniers.

getBlockParameter
^^^^^^^^^^^^^^^^^
Chaque bloc a un rendu en front indépendant. Or, il peut avoir besoin d'un certain nombre
d'informations pour réaliser ce rendu, la query string, la route ayant réclamé son rendu, les
données postées... Nous allons voir comment spécifier et envoyer ces données nécessaires.

Imaginons un bloc ayant besoin de l'ip du client. Nous allons ajouter la methode getBlockParameter
à ``Acme\Bundle\FrontBundle\DisplayBlock\HelloStrategy`` (vu dans la documentation sur les blocs)
et arbitrairement choisir le nom ``ip`` pour indiquer son besoin.

.. code-block:: php
    // ...

    /**
     * @return array
     */
    public function getBlockParameter()
    {
        return array('ip');
    }

Maintenant, nous allons créer la stratégie qui interceptera cette définition de besoin et retournera
les données attendues.

.. code-block:: php

    // src/Acme/Bundle/FrontBundle/Subquery/Strategies/IpSubQueryStrategy.php

    namespace Acme\Bundle\FrontBundle\Subquery\Strategies;

    use OpenOrchestra\FrontBundle\SubQuery\Strategies\AbstractRequestSubQueryStrategy;

    /**
     * Class IpSubQueryStrategy
     */
    class IpSubQueryStrategy extends AbstractRequestSubQueryStrategy
    {
        /**
         * @param string $blockParameter
         *
         * @return bool
         */
        public function support($blockParameter)
        {
            return 'ip' === $blockParameter;
        }

        /**
         * @param string $blockParameter
         *
         * @return array
         */
        public function generate($blockParameter)
        {
            $request = $this->requestStack->getMasterRequest();

            return $request->request->getClientIp();
        }

        /**
         * @return string
         */
        public function getName()
        {
            return 'ip';
        }
    }

Nous allons enregistrer cette stratégie auprès de
``OpenOrchestra\FrontBundle\SubQuery\SubQueryGeneratorManager`` en définissant un service
taggué ``open_orchestra_front.sub_query.strategy`` :

.. code-block:: yaml

    # src/Acme/Bundle/FrontBundle/Resources/config/services.yml

    services:
        acme_front.sub_query.ip:
            class: Acme\Bundle\FrontBundle\Subquery\Strategies\IpSubQueryStrategy
            arguments:
                - '@request_stack'
            tags:
                - { name: open_orchestra_front.sub_query.strategy }

Dorénavant la valeur de l'IP est disponible dans la request pour la méthode ``showAction`` du controller
``OpenOrchestra\FrontBundle\Controller\BlockController`` à l'index ``ip``.

getRequiredUriParameter
^^^^^^^^^^^^^^^^^^^^^^^
Un bloc peut avoir besoin de paramètres spécifiques pour pouvoir s'afficher. Ces paramètres
seront contenus dans l'url du node et envoyés au bloc. La pattern url du node doit donc être
formatée d'une façon particulière (voir les nodes) et le bloc indiquer qu'il attend ces paramètres
dans la pattern. Cette indication se fait grâce à la méthode ``getRequiredUriParameter`` dans la
stratégie de formulaire backoffice.
Un exemple d'utilisation est disponible dans
``OpenOrchestra\Backoffice\GenerateForm\Strategies\ContentStrategy`` qui indique qu'il doit trouver
un paramètre ``contentId`` dans la pattern qui devra donc contenir le fragment ``/{contentId}`` dont
la valeur sera déduite lors du "matching" de la route.

getDefaultConfiguration
^^^^^^^^^^^^^^^^^^^^^^^
Nous avons vu que certains blocs nécessitaient une contribution de la part de l'utilisateur. Il peut
être nécessaire de spécifier des valeurs par défaut pour ces contributions. Cela se fait également
au niveau de la stratégie de formulaire grâce à la méthode ``getDefaultConfiguration``.
Un exemple d'utilisation est disponible dans
``OpenOrchestra\Backoffice\GenerateForm\Strategies\ContentListStrategy`` qui indique la valeur par
défaut pour les champs ``contentNodeId`` et ``characterNumber`` dans la méthode
``getDefaultConfiguration``. Au niveau du manager
``OpenOrchestra\BackofficeBundle\StrategyManager\GenerateFormManager``, cette configuration est mergé avec
le paramétrage envoyé au constructeur, voir le paramètre
``open_orchestra_backoffice.block_default_configuration`` dans la documentation sur les blocs.

getCacheTags
^^^^^^^^^^^^
Open Orchestra tire parti de la puissance des blocs ESI pour optimiser le rendu des pages et augmenter les
performances. Les blocs ESI sont un moyen de fractionner le rendu d'une page en différents éléments qui seront
obtenus dans des requêtes séparées par le serveur Web. Ce comportement permet à l'application d'appliquer le cache
HTTP à certaines parties de la page et d'actualiser uniquement les parties nécessaires.

Dans l'application Front Office, chaque bloc est rendu dans un bloc ESI à l'aide de la fonction twig ``render_esi()``.
Les blocs seront donc mis en cache par un cache HTTP, sauf si la méthode
``OpenOrchestra\DisplayBundle\DisplayBlockDisplayBlockInterface::isPublic()`` renvoie false.
La méthode ``OpenOrchestra\DisplayBundle\DisplayBlockDisplayBlockInterface::getCacheTags(ReadBlockInterface $block)``
permet de spécifier les tags utilisés pour la signature du bloc ESI et donc les tags à utiliser pour rendre le cache
du bloc obsolète. Cette opération se fait à l'aide de
``OpenOrchestra\DisplayBundle\Manager\CacheableManager::invalidateTags(array $tags)``.

Un exemple de la création de ces tags est disponible dans
``OpenOrchestra\DisplayBundle\DisplayBlock\Strategies\ConfigurableContentStrategy``. Les tags sont ici utilisés pour
permettre en cas de changement du contenu affiché par le bloc ou du type de contenu de ce contenu de rendre obsolète
le cache de ce bloc. Par exemple, l'invalidation pour le contenu se trouve dans
``OpenOrchestra\Backoffice\EventSubscriber\ContentUpdateCacheSubscriber``.






getCacheTags
