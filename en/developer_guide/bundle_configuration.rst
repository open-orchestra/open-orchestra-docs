Bundle configuration
====================

Context
-------

As an open source product, Open Orchestra could not entitle you to just one configuration. This file
will describe each configuration parameter for all bundles

Bundles
-------

BaseBundle
~~~~~~~~~~

This bundle will configure the base option for the whole application :

* Language for the administration
* Key to encrypt the preview token
* Alias for the object manager

.. code-block:: yaml

    open_orchestra_base:
        object_manager:       doctrine.odm.mongodb.document_manager
        administration_languages:

            # Defaults:
            - en
            - fr
        encryption_key:       ThisKeyIsNotSecret

BaseApiMongoModelBundle
~~~~~~~~~~~~~~~~~~~~~~~

This bundle will gives you an implementation for the base api document and repository :


* The factory used to create the repositories
* The ``ApiClient`` document and repository
* The ``AccessToken`` document and repository

.. code-block:: yaml

    open_orchestra_base_api_model:
        document:
            api_client:
                class:                OpenOrchestra\BaseApiMongoModelBundle\Document\ApiClient
                repository:           OpenOrchestra\BaseApiMongoModelBundle\Repository\ApiClientRepository
            access_token:
                class:                OpenOrchestra\BaseApiMongoModelBundle\Document\AccessToken
                repository:           OpenOrchestra\BaseApiMongoModelBundle\Repository\AccessTokenRepository


BaseApiBundle
~~~~~~~~~~~~~

This bundle will be used as a base for all the applications api, you will need to configure :

* The controller to handle all the exceptions
* The expiration time for the created tokens

.. code-block:: yaml

    open_orchestra_base_api:
        http_exception_controller:  'OpenOrchestra\BaseApiBundle\Controller\ExceptionController::showAction'
        token_expiration_time:  +1month

ApiBundle
~~~~~~~~~

This bundle will be used in the applications api. You can configure :

* The ``Facade`` returned by the ``API``

.. code-block:: yaml

    open_orchestra_api:
        facades:
            api_client:               OpenOrchestra\ApiBundle\Facade\ApiClientFacade
            api_client_collection:    OpenOrchestra\ApiBundle\Facade\ApiClientCollectionFacade
            area:                     OpenOrchestra\ApiBundle\Facade\AreaFacade
            block:                    OpenOrchestra\ApiBundle\Facade\BlockFacade
            block_collection:         OpenOrchestra\ApiBundle\Facade\BlockCollectionFacade
            content:                  OpenOrchestra\ApiBundle\Facade\ContentFacade
            content_attribute:        OpenOrchestra\ApiBundle\Facade\ContentAttributeFacade
            content_collection:       OpenOrchestra\ApiBundle\Facade\ContentCollectionFacade
            content_type:             OpenOrchestra\ApiBundle\Facade\ContentTypeFacade
            content_type_collection:  OpenOrchestra\ApiBundle\Facade\ContentTypeCollectionFacade
            datatable_translation:    OpenOrchestra\ApiBundle\Facade\DatatableTranslationFacade
            field_type:               OpenOrchestra\ApiBundle\Facade\FieldTypeFacade
            group:                    OpenOrchestra\ApiBundle\Facade\GroupFacade
            group_collection:         OpenOrchestra\ApiBundle\Facade\GroupCollectionFacade
            keyword:                  OpenOrchestra\ApiBundle\Facade\KeywordFacade
            keyword_collection:       OpenOrchestra\ApiBundle\Facade\KeywordCollectionFacade
            link:                     OpenOrchestra\ApiBundle\Facade\LinkFacade
            node:                     OpenOrchestra\ApiBundle\Facade\NodeFacade
            node_collection:          OpenOrchestra\ApiBundle\Facade\NodeCollectionFacade
            node_group_role:          OpenOrchestra\ApiBundle\Facade\NodeGroupRoleFacade
            node_tree:                OpenOrchestra\ApiBundle\Facade\NodeTreeFacade
            redirection:              OpenOrchestra\ApiBundle\Facade\RedirectionFacade
            redirection_collection:   OpenOrchestra\ApiBundle\Facade\RedirectionCollectionFacade
            role:                     OpenOrchestra\ApiBundle\Facade\RoleFacade
            role_collection:          OpenOrchestra\ApiBundle\Facade\RoleCollectionFacade
            role_string:              OpenOrchestra\ApiBundle\Facade\RoleFacade
            role_string_collection:   OpenOrchestra\ApiBundle\Facade\RoleCollectionFacade
            site:                     OpenOrchestra\ApiBundle\Facade\SiteFacade
            site_collection:          OpenOrchestra\ApiBundle\Facade\SiteCollectionFacade
            status:                   OpenOrchestra\ApiBundle\Facade\StatusFacade
            status_collection:        OpenOrchestra\ApiBundle\Facade\StatusCollectionFacade
            template:                 OpenOrchestra\ApiBundle\Facade\TemplateFacade
            theme:                    OpenOrchestra\ApiBundle\Facade\ThemeFacade
            theme_collection:         OpenOrchestra\ApiBundle\Facade\ThemeCollectionFacade
            trash_item:               OpenOrchestra\ApiBundle\Facade\TrashItemFacade
            trash_item_collection:    OpenOrchestra\ApiBundle\Facade\TrashItemCollectionFacade
            translation:              OpenOrchestra\ApiBundle\Facade\TranslationFacade
            ui_model:                 OpenOrchestra\ApiBundle\Facade\UiModelFacade
            widget:                   OpenOrchestra\ApiBundle\Facade\WidgetFacade
            widget_collection:        OpenOrchestra\ApiBundle\Facade\WidgetCollectionFacade

UserBundle
~~~~~~~~~~

This bundle will manage the user's authentification. To display the forms in the best possible way, you need
to configure :

* The base layout
* The form template file

.. code-block:: yaml

    open_orchestra_user:
        base_layout:          'OpenOrchestraUserBundle::baseLayout.html.twig'
        form_template:        'OpenOrchestraUserBundle::form.html.twig'

UserAdminBundle
~~~~~~~~~~~~~~~

This bundle will create the user back-office part of the Open Orchestra project.
You can configure :

* The ``Facade`` returned by the ``API``

.. code-block:: yaml

    open_orchestra_user_admin:
        facades:
            user:                 OpenOrchestra\UserAdminBundle\Facade\UserFacade
            user_collection:      OpenOrchestra\UserAdminBundle\Facade\UserCollectionFacade

ModelBundle
~~~~~~~~~~~

This bundle provides an implementation of all the interfaces from the ``model-interface`` component for mongoDB.
You can configure :

* Some immutable properties for the contents
* Interfaces for the different fixtures groups
* All documents and repositories class

.. code-block:: yaml

    open_orchestra_model:

        # Immutable properties of the content class
        content_immutable_properties:  []
        fixtures_interface:
            all:

                # Default:
                - Doctrine\Common\DataFixtures\FixtureInterface
            production:

                # Default:
                - OpenOrchestra\ModelInterface\DataFixtures\OrchestraProductionFixturesInterface
            functional:

                # Default:
                - OpenOrchestra\ModelInterface\DataFixtures\OrchestraFunctionalFixturesInterface
        document:
            content:
                class:                OpenOrchestra\ModelBundle\Document\Content
                repository:           OpenOrchestra\ModelBundle\Repository\ContentRepository
            content_attribute:
                class:                OpenOrchestra\ModelBundle\Document\ContentAttribute
            content_type:
                class:                OpenOrchestra\ModelBundle\Document\ContentType
                repository:           OpenOrchestra\ModelBundle\Repository\ContentTypeRepository
            node:
                class:                OpenOrchestra\ModelBundle\Document\Node
                repository:           OpenOrchestra\ModelBundle\Repository\NodeRepository
            area:
                class:                OpenOrchestra\ModelBundle\Document\Area
            block:
                class:                OpenOrchestra\ModelBundle\Document\Block
            site:
                class:                OpenOrchestra\ModelBundle\Document\Site
                repository:           OpenOrchestra\ModelBundle\Repository\SiteRepository
            route_document:
                class:                OpenOrchestra\ModelBundle\Document\RouteDocument
                repository:           OpenOrchestra\ModelBundle\Repository\RouteDocumentRepository
            site_alias:
                class:                OpenOrchestra\ModelBundle\Document\SiteAlias
            template:
                class:                OpenOrchestra\ModelBundle\Document\Template
                repository:           OpenOrchestra\ModelBundle\Repository\TemplateRepository
            field_option:
                class:                OpenOrchestra\ModelBundle\Document\FieldOption
            field_type:
                class:                OpenOrchestra\ModelBundle\Document\FieldType
            status:
                class:                OpenOrchestra\ModelBundle\Document\Status
                repository:           OpenOrchestra\ModelBundle\Repository\StatusRepository
            embed_status:
                class:                OpenOrchestra\ModelBundle\Document\EmbedStatus
            theme:
                class:                OpenOrchestra\ModelBundle\Document\Theme
                repository:           OpenOrchestra\ModelBundle\Repository\ThemeRepository
            role:
                class:                OpenOrchestra\ModelBundle\Document\Role
                repository:           OpenOrchestra\ModelBundle\Repository\RoleRepository
            redirection:
                class:                OpenOrchestra\ModelBundle\Document\Redirection
                repository:           OpenOrchestra\ModelBundle\Repository\RedirectionRepository
            keyword:
                class:                OpenOrchestra\ModelBundle\Document\Keyword
                repository:           OpenOrchestra\ModelBundle\Repository\KeywordRepository
            embed_keyword:
                class:                OpenOrchestra\ModelBundle\Document\EmbedKeyword
            translated_value:
                class:                OpenOrchestra\ModelBundle\Document\TranslatedValue
            trash_item:
                class:                OpenOrchestra\ModelBundle\Document\TrashItem
                repository:           OpenOrchestra\ModelBundle\Repository\TrashItemRepository

MediaBundle
~~~~~~~~~~~

This bundle gives you a way to display medias in blocks, contents, ... . You can configure :

* The media domain

.. code-block:: yaml

    open_orchestra_media:
        media_domain:         ''

MediaModelBundle
~~~~~~~~~~~~~~~~

This bundle provides an implementation for all the interfaces defined in the MediaBundle. You can configure :

* The ``Media`` and ``MediaFolder`` document and repository

.. code-block:: yaml

    open_orchestra_media_model:
        document:
            media:
                class:                OpenOrchestra\MediaModelBundle\Document\Media
                repository:           OpenOrchestra\MediaModelBundle\Repository\MediaRepository
            media_folder:
                class:                OpenOrchestra\MediaModelBundle\Document\MediaFolder
                repository:           OpenOrchestra\MediaModelBundle\Repository\FolderRepository

MediaAdminBundle
~~~~~~~~~~~~~~~~

This bundle gives you a way to display medias in blocks, contents, ... . You can configure :

* The upload temporary directory
* Width, height and compression quality for each available image formats
* The default thumbnail for each media type
* The ``Facade`` returned by the ``API``

.. code-block:: yaml

    open_orchestra_media_admin:
        tmp_dir:              /tmp
        thumbnail:
            max_width:            117
            max_height:           117
            compression_quality:  75
        alternatives:
            image:
                formats:
                    fixed_height:
                        max_height:           100
                        compression_quality:  75
                    fixed_width:
                        max_width:            100
                        compression_quality:  75
                    rectangle:
                        max_width:            100
                        max_height:           70
                        compression_quality:  75
            default:
                thumbnail:            orchestra-media-thumbnail-default.png
            audio:
                thumbnail:            orchestra-media-thumbnail-audio.png
        facades:
            media:                OpenOrchestra\MediaAdminBundle\Facade\MediaFacade
            media_collection:     OpenOrchestra\MediaAdminBundle\Facade\MediaCollectionFacade

WorkflowFunctionModelBundle
~~~~~~~~~~~~~~~~~~~~~~~~~~~

This bundle provides an implementation for all the interfaces defined in the WorkflowBundle. You can configure :

* All documents and repositories class

.. code-block:: yaml

    open_orchestra_workflow_function_model:
        document:
            workflow_function:
                class:                OpenOrchestra\WorkflowFunctionModelBundle\Document\WorkflowFunction
                repository:           OpenOrchestra\WorkflowFunctionModelBundle\Repository\WorkflowFunctionRepository
            workflow_right:
                class:                OpenOrchestra\WorkflowFunctionModelBundle\Document\WorkflowRight
                repository:           OpenOrchestra\WorkflowFunctionModelBundle\Repository\WorkflowRightRepository
            authorization:
                class:                OpenOrchestra\WorkflowFunctionModelBundle\Document\Authorization
            reference:
                class:                OpenOrchestra\WorkflowFunctionModelBundle\Document\Reference

WorkflowFunctionAdminBundle
~~~~~~~~~~~~~~~~~~~~~~~~~~~

This bundle will create the workflow functions back-office part of the Open Orchestra project.
You can configure :

* The ``Facade`` returned by the ``API``

.. code-block:: yaml

    open_orchestra_workflow_function_admin:
        facades:
            workflow_function:             OpenOrchestra\WorkflowFunctionAdminBundle\Facade\WorkflowFunctionFacade
            workflow_function_collection:  OpenOrchestra\WorkflowFunctionAdminBundle\Facade\WorkflowFunctionCollectionFacade

BackofficeBundle
~~~~~~~~~~~~~~~~

This bundle will create the Back Office of the Open Orchestra project. You can configure :

* The language from the front installation
* The blocks that you created
* The fixed attributes from the block (shared through all blocks)
* The front roles, that can be added to the front pages
* The field type and options for the content (specific to your project)
* The color available for the Back Office

.. code-block:: yaml

    open_orchestra_backoffice:

        # Add the available languages in the Front Office, default (en, fr, de)
        front_languages:

            # Prototype
            key:                  ~

        # Set the available block types for this application
        blocks:

            # Defaults:
            - footer
            - language_list
            - menu
            - sub_menu
            - content_list
            - content
            - configurable_content
            - tiny_mce_wysiwyg
            - video
            - gmap
            - add_this
            - audience_analysis
            - contact

        # Add the global block attributes
        fixed_attributes:     []

        # Role than can be given to the user on the Front websites
        front_roles:          []

        # Array of content attributes (for content types)
        field_types:

            # Prototype
            field_name:
                label:                ~ # Required
                type:                 ~ # Required
                default_value:
                    type:                 ~
                    options:
                        label:                ~
                        required:             true
                options:

                    # Prototype
                    option_name:
                        default_value:        ~ # Required

        # Array of content attributes options
        options:

            # Prototype
            option_name:
                type:                 ~ # Required
                label:                ~ # Required
                required:             true

        # List of the color available, in the status for instance
        available_color:

            # Prototype
            key:                  ~

        # List of widgets presented on the dashboard
        dashboard_widgets:

            # Defaults:
            - last_nodes
            - draft_nodes
            - last_contents
            - draft_contents

LogBundle
~~~~~~~~~

This bundle will create the log back-office part of the Open Orchestra project.
You can configure :

* The ``Facade`` returned by the ``API``

.. code-block:: yaml

    open_orchestra_log:
        facades:
            log:                  OpenOrchestra\LogBundle\Facade\LogFacade
            log_collection:       OpenOrchestra\LogBundle\Facade\LogCollectionFacade

FrontBundle
~~~~~~~~~~~

This bundle creates the base part for the Front Office installation. You can configure :

* The devices name
* The device type field name
* The routing type

.. code-block:: yaml

    open_orchestra_front:
        devices:

            # Prototype
            name:
                parent:               null
        device_type_field:    x-ua-device
        routing_type:         ~ # One of "file"; "database"

ThemeBundle
~~~~~~~~~~~

This bundle will add the different assets (js and css files) to the different files. You can configure :

* The different stylesheet groups

.. code-block:: yaml

    open_orchestra_theme:
        themes:

            # Prototype
            id:
                name:                 ~ # Required
                stylesheets:          []
                javascripts:          []

.. _`field type`: /en/developer_guide/field_type.rst
