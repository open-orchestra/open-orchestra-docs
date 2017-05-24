Install OpenOrchestra in a clean symfony installation
=====================================================

Open Orchestra is composed of three projects:

- *open-orchestra* which is the CMS Back Office;
- *open-orchestra-front-demo* which is the Front Office part that display sites and pages
  created in the CMS Back Office;
- *open-orchestra-media-demo* which render the media via the CMS Back Office.

Each projects is composed of different bundles that can be used,
these bundles can be used in an existing Symfony application.

Before using an Open Orchestra bundle, you should check that your server meet the
`requirement <../hosting_guide/requirements.html>`_. Also it needs some `configurations <../hosting_guide/configuration.html>`_ (varnish vcl,
cron, ...) according to the components used.

This documentation explain the steps (composer, configuration, ...) to add Open Orchestra bundles
in your application.

Bundles used in Back Office
---------------------------

Install the Bundles via Composer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Add the bundles used by the Back Office in your ``composer.json``

.. code-block:: javascript

    "require": {
        // others dependencies
        "open-orchestra/open-orchestra-cms-bundle": "~1.1.0",
        "open-orchestra/open-orchestra-workflow-function-bundle": "~1.1.0",
        "open-orchestra/open-orchestra-media-admin-bundle": "~1.1.0",
        "open-orchestra/open-orchestra-model-bundle": "~1.1.0",
        "open-orchestra/open-orchestra-base-api-mongo-model-bundle": "~1.1.0",
        "open-orchestra/open-orchestra-elastica-bundle": "~1.1.0"

        "innocead/captcha-bundle": "@dev",
        "friendsofsymfony/user-bundle": "@dev"
    },

Run composer update in your Symfony application.

.. code-block:: bash

    composer update

Enable the bundles
~~~~~~~~~~~~~~~~~~

Register the bundles in ``AppKernel``

.. code-block:: php

    class AppKernel extends Kernel
    {
        // ...

        public function registerBundles()
        {
            $bundles = array(
                // ...

                new Symfony\Bundle\AsseticBundle\AsseticBundle(),
                new Doctrine\Bundle\MongoDBBundle\DoctrineMongoDBBundle(),

                new JMS\SerializerBundle\JMSSerializerBundle(),
                new FOS\UserBundle\FOSUserBundle(),
                new FOS\HttpCacheBundle\FOSHttpCacheBundle(),
                new Stof\DoctrineExtensionsBundle\StofDoctrineExtensionsBundle(),

                new Braincrafted\Bundle\BootstrapBundle\BraincraftedBootstrapBundle(),

                new OpenOrchestra\BaseBundle\OpenOrchestraBaseBundle(),
                new OpenOrchestra\BaseApiMongoModelBundle\OpenOrchestraBaseApiMongoModelBundle(),
                new OpenOrchestra\BaseApiBundle\OpenOrchestraBaseApiBundle(),
                new OpenOrchestra\UserBundle\OpenOrchestraUserBundle(),
                new OpenOrchestra\ModelBundle\OpenOrchestraModelBundle(),
                new OpenOrchestra\MongoBundle\OpenOrchestraMongoBundle(),
                new OpenOrchestra\MediaBundle\OpenOrchestraMediaBundle(),
                new OpenOrchestra\MediaModelBundle\OpenOrchestraMediaModelBundle(),
                new OpenOrchestra\WorkflowFunctionModelBundle\OpenOrchestraWorkflowFunctionModelBundle(),
                new OpenOrchestra\WorkflowFunctionBundle\OpenOrchestraWorkflowFunctionBundle(),

                new OpenOrchestra\ApiBundle\OpenOrchestraApiBundle(),
                new OpenOrchestra\DisplayBundle\OpenOrchestraDisplayBundle(),
                new OpenOrchestra\BBcodeBundle\OpenOrchestraBBcodeBundle(),
                new OpenOrchestra\BackofficeBundle\OpenOrchestraBackofficeBundle(),
                new OpenOrchestra\GroupBundle\OpenOrchestraGroupBundle(),
                new OpenOrchestra\LogBundle\OpenOrchestraLogBundle(),
                new OpenOrchestra\UserAdminBundle\OpenOrchestraUserAdminBundle(),
                new OpenOrchestra\MediaAdminBundle\OpenOrchestraMediaAdminBundle(),
                new OpenOrchestra\MediaAdminModelBundle\OpenOrchestraMediaAdminModelBundle(),
                new OpenOrchestra\MediaFileBundle\OpenOrchestraMediaFileBundle(),
                new OpenOrchestra\WorkflowFunctionAdminBundle\OpenOrchestraWorkflowFunctionAdminBundle(),

                new Stfalcon\Bundle\TinymceBundle\StfalconTinymceBundle(),
                new Knp\Bundle\GaufretteBundle\KnpGaufretteBundle(),
                new Solution\MongoAggregationBundle\SolutionMongoAggregationBundle(),
                new OpenOrchestra\ModelLogBundle\OpenOrchestraModelLogBundle(),
                new OpenOrchestra\ElasticaBundle\OpenOrchestraElasticaBundle(),
                new OpenOrchestra\ElasticaAdminBundle\OpenOrchestraElasticaAdminBundle(),
                new AntiMattr\Bundle\MongoDBMigrationsBundle\MongoDBMigrationsBundle(),
            );

            // ...
        }
    }

Configure the Bundles
~~~~~~~~~~~~~~~~~~~~~

Add the configuration for the different bundles

.. code-block:: yaml

    # config.yml

    # FOSUserBundle
    fos_user:
        db_driver: mongodb
        firewall_name: main
        user_class: OpenOrchestra\UserBundle\Document\User
        group:
            group_class: OpenOrchestra\GroupBundle\Document\Group

    # Doctrine mongodb
    doctrine_mongodb:
        connections:
            default:
                server: "mongodb://127.0.0.1:27017"
                options: {}
        default_database: "open_orchestra_%kernel.environment%"
        resolve_target_documents:
            FOS\UserBundle\Model\GroupInterface: OpenOrchestra\GroupBundle\Document\Group
        document_managers:
            default:
                auto_mapping: true

    # FOSHttpCacheBundle
    fos_http_cache:
        proxy_client:
            varnish:
                servers: "127.0.0.1:6081"
                base_url: "%router.request_context.host%:6081"
            default: varnish

    # Gaufrette
    knp_gaufrette:
        adapters:
            media_storage:
                local:
                    directory: /var/uploaded-files
                    create: true
        filesystems:
            media_storage:
                adapter: media_storage
                alias: media_storage_filesystem

    # Assetic bundle
    assetic:
        debug:          "%kernel.debug%"
        use_controller: false
        bundles:
            - OpenOrchestraBackofficeBundle
            - OpenOrchestraMediaAdminBundle
            - OpenOrchestraDisplayBundle
            - OpenOrchestraUserBundle
        filters:
            cssrewrite: ~

    # BraincraftedBootstrapBundle
    braincrafted_bootstrap:
        auto_configure:
            assetic: false
            knp_menu: false
            knp_paginator: false
            twig: false

    # Open Orchestra media
    open_orchestra_media:
        media_domain: media.openorchestra.1-1.dev

    # Open Orchestra elastica
    open_orchestra_elastica:
        host: 127.0.0.1


Configure the routing

.. code-block:: yaml

    # routing.yml
    open_orchestra_backoffice:
        resource: "@OpenOrchestraBackofficeBundle/Controller"
        type: annotation
        prefix: /admin

    open_orchestra_user_admin:
        resource: "@OpenOrchestraUserAdminBundle/Controller/Admin"
        type: annotation
        prefix: /admin

    open_orchestra_media_admin:
        resource: "@OpenOrchestraMediaAdminBundle/Controller/Admin"
        type: annotation
        prefix: /admin

    open_orchestra_workflow_admin:
        resource: "@OpenOrchestraWorkflowFunctionAdminBundle/Controller/Admin"
        type: annotation
        prefix: /admin

    open_orchestra_api_oauth2:
        resource: "@OpenOrchestraBaseApiBundle/Resources/config/oauth2_routing.yml"

    open_orchestra_api:
        resource: "@OpenOrchestraApiBundle/Controller"
        type: annotation
        prefix: /api

    open_orchestra_user_api:
        resource: "@OpenOrchestraUserAdminBundle/Controller/Api"
        type: annotation
        prefix: /api

    open_orchestra_media_api:
        resource: "@OpenOrchestraMediaAdminBundle/Controller/Api"
        type: annotation
        prefix: /api

    open_orchestra_workflow_api:
        resource: "@OpenOrchestraWorkflowFunctionAdminBundle/Controller/Api"
        type: annotation
        prefix: /api

    open_orchestra_log:
        resource: "@OpenOrchestraLogBundle/Controller"
        type: annotation
        prefix: /api

    open_orchestra_media_file:
        resource: "@OpenOrchestraMediaFileBundle/Controller"
        type: annotation
        prefix: /media

    fos_user:
        resource: "@FOSUserBundle/Resources/config/routing/all.xml"

    root:
        path: /
        methods: ['GET']
        defaults:
            _controller: FrameworkBundle:Redirect:urlRedirect
            path: /admin
            permanent: true

    open_orchestra_base:
        resource: "@OpenOrchestraBaseBundle/Resources/config/routing.yml"

Configure the security

.. code-block:: yaml

    # security.yaml
    encoders:
        FOS\UserBundle\Model\UserInterface: sha512

    role_hierarchy:
        ROLE_ADMIN:       ROLE_USER
        ROLE_SUPER_ADMIN: [ROLE_USER, ROLE_ADMIN, ROLE_ALLOWED_TO_SWITCH]

    providers:
        fos_userbundle:
            id: fos_user.user_provider.username

    access_decision_manager:
        strategy: unanimous

    firewalls:
        dev:
            pattern:  ^/(_(profiler|wdt)|css|images|js)/
            security: false
        api:
            pattern: ^/api/
            oauth2: ~
            anonymous: false
            security: true
            context: openorchestra
        main:
            pattern: ^/
            form_login:
                provider: fos_userbundle
                csrf_provider: security.csrf.token_manager
            anonymous: true
            context: openorchestra
            logout:
                path:   /logout
                target: /admin

    access_control:
        - { path: ^/login$, role: IS_AUTHENTICATED_ANONYMOUSLY }
        - { path: ^/admin/, role: ROLE_USER }
        - { path: ^/api/, role: ROLE_USER }


Manage assets
~~~~~~~~~~~~~

Configure grunt to generate all assets used by Open Orchestra

First, download grunt task folder of repository `open-orchestra/open-orchestra <https://github.com/open-orchestra/open-orchestra/tree/master/grunt>`_

You can use subversion to export grunt folder in your folder application:

.. code-block:: bash

    svn export https://github.com/open-orchestra/open-orchestra/trunk/grunt

After, create the file ``Gruntfile.js`` in the root folder of your application

.. code-block:: javascript

    module.exports = function(grunt) {
      var appConfig = require('./grunt/app_config.js');
      var GruntConfigBuilder = require(appConfig.GruntConfigBuilder);

      GruntConfigBuilder.init(grunt, appConfig);
    };

Finally, run the grunt command to generate all assets

.. code-block:: bash

    ./bin/grunt

Load the fixtures
-----------------

Open Orchestra needs some fixtures to work (an admin user, a website, ...).

.. code-block:: bash

    $ php app/console orchestra:mongodb:fixtures:load --type=production --env=prod


Bundles used in Front Application
---------------------------------

Install the Bundles via Composer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Add the bundles used by the Back Office in your ``composer.json``

.. code-block:: javascript

    "require": {
        // others dependencies
        "open-orchestra/open-orchestra-front-bundle": "1.1.*",
        "open-orchestra/open-orchestra-media-bundle": "1.1.*",
        "open-orchestra/open-orchestra-model-bundle": "1.1.*",
        "open-orchestra/open-orchestra-elastica-bundle": "1.1.*",
        "innocead/captcha-bundle": "@dev"
    },

Run composer update in your Symfony application.

.. code-block:: bash

    composer update

Enable the bundles
~~~~~~~~~~~~~~~~~~

Register the bundles in ``AppKernel``

.. code-block:: php

    class AppKernel extends Kernel
    {
        // ...

        public function registerBundles()
        {
            $bundles = array(
                // others bundles
                new Doctrine\Bundle\MongoDBBundle\DoctrineMongoDBBundle(),
                new FOS\HttpCacheBundle\FOSHttpCacheBundle(),
                new Symfony\Cmf\Bundle\RoutingBundle\CmfRoutingBundle(),
                new Symfony\Bundle\AsseticBundle\AsseticBundle(),

                new OpenOrchestra\BaseBundle\OpenOrchestraBaseBundle(),
                new OpenOrchestra\ThemeBundle\OpenOrchestraThemeBundle(),
                new OpenOrchestra\ModelBundle\OpenOrchestraModelBundle(),
                new OpenOrchestra\MongoBundle\OpenOrchestraMongoBundle(),
                new OpenOrchestra\MediaBundle\OpenOrchestraMediaBundle(),
                new OpenOrchestra\MediaModelBundle\OpenOrchestraMediaModelBundle(),
                new OpenOrchestra\DisplayBundle\OpenOrchestraDisplayBundle(),
                new OpenOrchestra\BBcodeBundle\OpenOrchestraBBcodeBundle(),
                new OpenOrchestra\FrontBundle\OpenOrchestraFrontBundle(),

                new Solution\MongoAggregationBundle\SolutionMongoAggregationBundle(),
                new Innocead\CaptchaBundle\InnoceadCaptchaBundle(),
                new OpenOrchestra\ElasticaBundle\OpenOrchestraElasticaBundle(),
                new OpenOrchestra\ElasticaFrontBundle\OpenOrchestraElasticaFrontBundle(),
            );

            // ...
        }
    }

Configure the Bundles
~~~~~~~~~~~~~~~~~~~~~

Add the configuration for the different bundles

.. code-block:: yaml

    # config.yml

    # Doctrine mongodb
    doctrine_mongodb:
        connections:
            default:
                server: "mongodb://127.0.0.1:27017"
                options: {}
        default_database: "open_orchestra_%kernel.environment%"
        resolve_target_documents:
            OpenOrchestra\ModelInterface\Model\TranslatedValueInterface: OpenOrchestra\ModelBundle\Document\TranslatedValue
        document_managers:
            default:
                auto_mapping: true

    # FOSHttpCacheBundle
    fos_http_cache:
        proxy_client:
            varnish:
                servers: "127.0.0.1:6081"
                base_url: "%router.request_context.host%:6081"
            default: varnish

    # Assetic bundle
    assetic:
        debug:          "%kernel.debug%"
        use_controller: false
        bundles:
            - OpenOrchestraFrontBundle
            - OpenOrchestraDisplayBundle
        filters:
            cssrewrite: ~

    # Framework
    framework:
        esi:             { enabled: true }
        serializer:
            enabled: true

    # Innocead Captcha Bundle
    innocead_captcha:
        width: 150
        height: 30
        max_chars: 6
        min_chars: 5
        bg_transparent: false
        bg_red: 255
        bg_green: 255
        bg_blue: 255

    # Open Orchestra Front Bundle
    open_orchestra_front:
        devices:
            web: ~
            tablet:
                parent: web
            phone:
                parent: web
            android:
                parent: phone

    # Open Orchestra media
    open_orchestra_media:
        media_domain: media.openorchestra.1-1.dev

    # Open Orchestra elastica
    open_orchestra_elastica:
        host: 127.0.0.1

Configure routing

.. code-block:: yaml

    # routing.yml
    open_orchestra_front:
        resource: "@OpenOrchestraFrontBundle/Controller"
        type: annotation

    open_orchestra_display:
        resource: "@OpenOrchestraDisplayBundle/Resources/config/routing.yml"

    open_orchestra_front_preview:
        resource: "@OpenOrchestraFrontBundle/Resources/config/preview_routing.yml"

    open_orchestra_media_get:
        path: /media/{key}

Bundles used in Media Application
---------------------------------

Install the Bundles via Composer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Add the bundles used by the Back Office in your ``composer.json``

.. code-block:: javascript

    "require": {
        // others dependencies
        "open-orchestra/open-orchestra-media-file-bundle": "1.1.*"
    },

Run composer update in your Symfony application.

.. code-block:: bash

    composer update

Enable the bundles
~~~~~~~~~~~~~~~~~~

Register the bundles in ``AppKernel``

.. code-block:: php

    class AppKernel extends Kernel
    {
        // ...

        public function registerBundles()
        {
            $bundles = array(
                // ...
                new OpenOrchestra\MediaFileBundle\OpenOrchestraMediaFileBundle(),
                new Knp\Bundle\GaufretteBundle\KnpGaufretteBundle(),
            );

            // ...
        }
    }

Configure the Bundles
~~~~~~~~~~~~~~~~~~~~~

Add the configuration for the different bundles

.. code-block:: yaml

    # config.yml

    knp_gaufrette:
        adapters:
            media_storage:
                local:
                    directory: /var/uploaded-files
                    create: true
        filesystems:
            media_storage:
                adapter: media_storage
                alias: media_storage_filesystem

Configure the routing

.. code-block:: yaml

    # routing.yml
    app:
        resource: "@OpenOrchestraMediaFileBundle/Controller"
        type: annotation
        prefix: /media
