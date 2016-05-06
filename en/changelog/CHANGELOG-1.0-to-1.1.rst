CHANGELOG from 1.0 to 1.1
=========================

Url to see changes:

- `Cms bundle`_
- `Display bundle`_
- `BBCode bundle`_
- `Model bundle`_
- `Model interface`_
- `Front bundle`_
- `Base bundle`_
- `Base api bundle`_
- `Base api model bundle`_
- `Media bundle`_
- `User bundle`_
- `Theme bundle`_
- `Workflow function bundle`_
- `Media admin bundle`_
- `Orchestra libs`_
- `Orchestra Mongo libs`_
- `Media file bundle`_
- `Elastica bundle`_

------------

Changelog 1.0.0 to 1.1.0-alpha1
-------------------------------

New features
------------

- It is now possible to configure the Back Office dashboard and to create new widgets for it.
- Routes stored in the database are now linked to the last published version of a node
- You can now add the author, last contributor and contribution date in the content listing
- 2 new events are availables in the block rendering process: PRE_BLOCK_CREATION and POST_BLOCK_CREATION
- It is now possible to filter a column which contains a type `date` in dataTable
- Transverse block are now created on all transverse nodes
- When you add a language to a website, the transverse node is created with all the transverse blocks

Bug fixes
---------

- Each time you update a site, the routes in the database related to this site are updated
- Sorts by attributes in content and content type view are fully functional

Other changes
-------------

- Bundles are now using the PSR-4 syntax to be loaded, you should update the `Gruntfile` to follow this path modification

Deprecated method
-----------------

- Some method from the `NodeRepositoryInterface` and `ContentRepositoryInterface` `have been deprecated`_
- The method `findByNodeType` has been deprecated

------------

Changelog 1.1.0-alpha1 to 1.1.0-alpha2
--------------------------------------

New features
------------

- Replace the media upload GUI with a new component allowing multi-upload
- Adding roles for nodes (CREATE, UPDATE, MOVE, DELETE)
- Adding roles for content types (CREATE, UPDATE, DELETE)
- Adding roles for keywords (CREATE, UPDATE, DELETE)
- Adding roles for redirections (CREATE, UPDATE, DELETE)
- Adding roles for trashcan (RESTORE)
- Adding roles for api accesses (CREATE, UPDATE, DELETE)
- Adding roles for contents (CREATE, UPDATE, DELETE)
- Adding roles for medias (CREATE, UPDATE, DELETE)
- Adding roles for roles (CREATE, UPDATE, DELETE)
- Adding roles for sites (CREATE, UPDATE, DELETE)
- Adding roles for users (CREATE, UPDATE, DELETE)
- Adding roles for transverse nodes (UPDATE)
- Adding roles for workflow status (CREATE, UPDATE, DELETE)
- Adding roles for workflow functions (CREATE, UPDATE, DELETE)

Possible BC breaker
-------------------

- The name of `OpenOrchestra\BackofficeBundle\Form\Type\AreaType` is now `oo_area`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\BlockChoiceType` is now `oo_block_choice`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\BlockType` is now `oo_block`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\ExistingBlockChoiceType` is now `oo_existing_block`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\NodeType` is now `oo_node`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\ApiClientType` is now `oo_api_client`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\AbstractOrchestraGroupType` is deleted and replaced by `OpenOrchestra\BackofficeBundle\Form\Type\AbstractGroupChoiceType`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\OrchestraColorPickerType` is deleted and replaced by `OpenOrchestra\BackofficeBundle\Form\Type\ColorPickerType`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\OrchestraChoicesOption` is deleted and replaced by `OpenOrchestra\BackofficeBundle\Form\Type\Component\ChoicesOptionType`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\OrchestraContentTypeChoiceType` is deleted and replaced by `OpenOrchestra\BackofficeBundle\Form\Type\Component\ContentTypeChoiceType`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\OrchestraDateWidgetOption` is deleted and replaced by `OpenOrchestra\BackofficeBundle\Form\Type\Component\DateWidgetOptionType`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\OrchestraFieldChoice` is deleted and replaced by `OpenOrchestra\BackofficeBundle\Form\Type\Component\FieldChoiceType`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\OrchestraKeywordsType` is deleted and replaced by `OpenOrchestra\BackofficeBundle\Form\Type\Component\KeywordsChoiceType`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\OrchestraNodeChoiceType` is deleted and replaced by `OpenOrchestra\BackofficeBundle\Form\Type\Component\NodeChoiceType`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\OrchestraRoleChoiceType` is deleted and replaced by `OpenOrchestra\BackofficeBundle\Form\Type\Component\RoleChoiceType`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\OrchestraSiteChoiceType` is deleted and replaced by `OpenOrchestra\BackofficeBundle\Form\Type\Component\SiteChoiceType`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\OrchestraThemeChoiceType` is deleted and replaced by `OpenOrchestra\BackofficeBundle\Form\Type\Component\ThemeChoiceType`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\OrchestraVideoType` is deleted and replaced by `OpenOrchestra\BackofficeBundle\Form\Type\VideoType`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\ContentType` is now `oo_content`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\ContentTypeType` is now `oo_cont ent_type`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\FieldOptionType` is now `oo_field_option`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\FieldTypeType` is now `oo_field_type`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\GroupType` is now `oo_group`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\KeywordType` is now `oo_keyword`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\RedirectionType` is now `oo_redirection`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\RoleType` is now `oo_role`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\SiteAliasType` is now `oo_site_alias`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\SiteType` is now `oo_site`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\StatusType` is now `oo_status`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\TemplateType` is now `oo_template`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\ThemeType` is now `oo_theme`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\TinymceType` is now `oo_tinymce`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\TranslatedValueCollectionType` is now `oo_translated_value_collection`
- The name of `OpenOrchestra\BackofficeBundle\Form\Type\TranslatedValueType` is now `oo_translated_value`
- The class `OpenOrchestra\BackofficeBundle\Form\Type\OrchestraGroupType` is deleted and replaced by `OpenOrchestra\GroupBundle\Form\Type\GroupDocumentType`
- The name of `OpenOrchestra\MediaAdminBundle\Form\Type\FolderType` is now `oo_folder`
- The name of `OpenOrchestra\MediaAdminBundle\Form\Type\MediaCropType` is now `oo_media_crop`
- The name of `OpenOrchestra\MediaAdminBundle\Form\Type\MediaMetaType` is now `oo_media_meta`
- The name of `OpenOrchestra\MediaAdminBundle\Form\Type\MediaType` is now `oo_media`
- The class `OpenOrchestra\MediaAdminBundle\Form\DataTransformer\OrchestraMediaTransformer` is deleted and replaced by `OpenOrchestra\MediaAdminBundle\Form\DataTransformer\MediaChoiceTransformer`
- The class `OpenOrchestra\MediaAdminBundle\Form\Type\OrchestraMediaType` is deleted and replaced by `OpenOrchestra\MediaAdminBundle\Form\Type\Component\MediaChoiceType`
- The class `OpenOrchestra\MediaAdminBundle\Form\Type\OrchestraSiteForFolderChoiceType` is deleted and replaced by `OpenOrchestra\MediaAdminBundle\Form\Type\SiteForFolderChoiceType`
- The class `OpenOrchestra\ModelBundle\Form\Type\OrchestraRoleType` is deleted and replaced by `OpenOrchestra\ModelBundle\Form\Type\WorkflowRoleChoiceType`
- The class `OpenOrchestra\ModelBundle\Form\Type\OrchestraSiteType` is deleted and replaced by `OpenOrchestra\ModelBundle\Form\Type\GroupSiteChoiceType`
- The class `OpenOrchestra\ModelBundle\Form\Type\OrchestraStatusType` is deleted and replaced by `OpenOrchestra\ModelBundle\Form\Type\StatusChoiceType`
- The class `OpenOrchestra\ModelBundle\Form\Type\OrchestraThemeType` is deleted and replaced by `OpenOrchestra\ModelBundle\Form\Type\SiteThemeChoiceType`
- The class `OpenOrchestra\ModelInterface\Form\Type\AbstractOrchestraRoleType` is deleted and replaced by `OpenOrchestra\ModelInterface\Form\Type\AbstractWorkflowRoleChoiceType`
- The class `OpenOrchestra\ModelInterface\Form\Type\AbstractOrchestraSiteType` is deleted and replaced by `OpenOrchestra\ModelInterface\Form\Type\AbstractGroupSiteChoiceType`
- The class `OpenOrchestra\ModelInterface\Form\Type\AbstractOrchestraStatusType` is deleted and replaced by `OpenOrchestra\ModelInterface\Form\Type\AbstractStatusChoiceType`
- The class `OpenOrchestra\ModelInterface\Form\Type\AbstractOrchestraThemeType` is deleted and replaced by `OpenOrchestra\ModelInterface\Form\Type\AbstractSiteThemeChoiceType`
- The name of `OpenOrchestra\AdminBundle\Form\Type\RegistrationUserType` is now `oo_registration_user`
- The name of `OpenOrchestra\AdminBundle\Form\Type\UserType` is now `oo_user`
- The name of `OpenOrchestra\UserBundle\Form\Type\ChangePasswordUserType` is now `oo_user_change_password`
- The class `OpenOrchestra\WorkflowFunctionAdminBundle\Form\Type\AuthorizationType` is deleted and replaced by `OpenOrchestra\WorkflowFunctionAdminBundle\Form\Type\Component\AuthorizationType`
- The class `OpenOrchestra\WorkflowFunctionAdminBundle\Form\Type\OrchestraWorkflowFunctionType` is deleted and replaced by `OpenOrchestra\WorkflowFunctionAdminBundle\Form\Type\Component\WorkflowFunctionChoiceType`
- The name of `OpenOrchestra\WorkflowFunctionAdminBundle\Form\Type\WorkflowRightType` is now `oo_workflow_right`
- The name of `OpenOrchestra\WorkflowFunctionAdminBundle\Form\Type\WorkflowFunctionType` is now `oo_workflow_function`

Bug fixes
---------

- User is now able to delete a media folder when the last media is deleted, without having to refresh the page.
- When creating a new media folder, menu is now automatically refreshed.


Other changes
-------------

- In differents dataTable, the global search is disabled. To reactivate it, you can use the data attribute ``display-global-search=true`` in the link in navigation panel.
- Every repository that should be paginated are now implementing `OpenOrchestra\Pagination\Configuration\PaginationRepositoryInterface`
- The version of Symfony is updated to 2.7.6
- Module php5-ffmpeg is replaced by `PHP driver PHP-FFMpeg`_

Deprecated method
-----------------

- The method `findByAuthor` has been deprecated in both NodeRepository and ContentRepository
- The class `OpenOrchestra\ModelInterface\Repository\PaginateRepositoryInterface` has been replaced by
  `OpenOrchestra\Pagination\Configuration\PaginationRepositoryInterface`

------------

Changelog 1.1.0-alpha2 to 1.1.0-alpha3
--------------------------------------

Possible BC breaker
-------------------

- Plugin ``Colvis`` of DataTable is replaced by the ``Buttons extension``
- ``UploadedFileManager`` is moved from ``MediaBundle`` to ``MediaFileBundle``
- Class of ``BBcode`` folder are moved from ``MediaBundle`` folder to ``Media`` folder
- Service ``open_orchestra_media.manager.uploaded_media`` is renamed by ``open_orchestra_media_file.manager.storage``
- Application ``open-orchestra-media-demo`` no longer requires this bundles :
  - ``DoctrineMongoDBBundle``
  - ``OpenOrchestraBaseBundle``
  - ``OpenOrchestraMediaModelBundle``
  - ``OpenOrchestraMongoBundle``
  - ``OpenOrchestraModelBundle``
  - ``SolutionMongoAggregationBundle``
- Application ``open-orchestra-media-demo`` requires `MediaFileBundle``
- Route ``open_orchestra_media_get`` is now in ``MediaController`` in ``MediaFileBundle``
- Class moved from ``MediaBundle`` to ``MediaAdminBundle`` :
  - ``FolderEvent``
  - ``ImagickEvent``
  - ``MediaEvent``
  - `DeleteMediaSubscriber``
  - ``GenerateImageSubscriber``
  - ``UploadImageSubscriber``
  - ``FolderEvents``
  - ``OrchestraImagick``
  - ``OrchestraImagickFactory``
  - ``OrchestraImagickFactoryInterface``
  - ``OrchestraImagickInterface``
  - ``ImageResizerManager``
  - ``MediaEvents``
  - ``ImageToThumbnailManager``
  - ``PdfToImageManager``
  - ``VideoToImageManager``
  - ``ThumbnailInterface``
  - ``ThumbnailManager``
  - ``FFmpegVideoManager``
  - ``VideoManagerInterface``
  - ``SaveMediaManager``
  - ``SaveMediaManagerInterface``

New features
------------

- Possibility to add custom fields for search in the DataTable, further information in `documentation`_
- New Backbone view generic ``DataTableView`` for create a list with DataTable, used by ``TableViewCollection``
- The build of the full project has been moved to the travis container build
- Every facades returned by the API are now configurable and can be defined in bundles configuration, further
  `information in documentation`_
- The `RoleCollector` has been split into a collector for the front office and the backoffice
- To prevent `Status` suppression, the `StatusUsageFinder` has been created to check in every document using `Status` if
  they are using it
- Install smartadmin Datepicker
- Datatable preferences saving
- Add embedded entity to content attributs
- New bundle MediaFileBundle used to managed media files with Gaufrette
- Adding of upload stategies to manage all alternatives of media like thumbnail, `futher information in the documentation`_

Bug fixes
---------

- The node drag'n'drop has been updated to wait for user's confirmation before sending datas
- Fix errors on template creating
- Clean redirection and route on unpublished node
- Fixes on Dashboard, action buttons, order ...

Other changes
-------------

- DataTable is updated to version 1.1.0.
  In your `bower.json` file replace lines :

.. code-block:: javascript

   "datatables": "~1.10.2",
   "datatables-colvis": "~1.1.2",
   "datatables-bootstrap3": "*",

  by

.. code-block:: javascript

   "datatables.net-buttons-bs": "1.1.0",

- Version of doctrine/cache is fixed to 1.5.*
- Version of doctrine/commmon is fixed to 2.5.*

Deprecated method
-----------------

- `NodeGroupRoleVoter` has been moved in the `Backoffice` folder
- `GroupSiteVoter` has been moved in the `Backoffice` folder
- The `AuthorizeEditionManager` has been deprecated, and all strategies has been transformed has roles
- The `VersionableSaver` has been moved in the `Saver` folder
- The role constant `ROLE_ACCESS_GENERAL_NODE` has been replaced by `ROLE_ACCESS_TREE_GENERAL_NODE`

------------

Changelog 1.1.0-alpha3 to 1.1.0-alpha4
--------------------------------------

New features
------------

- You can specify your bower and npm dependencies directly in the composer.json, futher information in the `assets documentation`_
- Selector version of node tranverse is removed
- Duplicate button of node tranverse is removed
- Delete button of node tranverse is removed
- An `Elastica` implementation has been created to index all the `content` in an indexor

Bug fixes
---------

- The Back Office is compatible again with Internet Explorer 9. See Configurations changes for more info
- Fix a bug when a site declared in Apache conf but not in Orchestra was accessed by a client

Possible BC breaker
-------------------

- ``NodeGroupRoleTransformer`` implements now ``TransformerWithGroupInterface``
- Method ``reverseTransform`` of ``NodeGroupRoleTransformer`` is removed and replaced by ``reverseTransformWithGroup``
- Before ``composer install|update`` it's recommanded to removed ``nodes_modules`` and ``bower_components``
  folders of your application and ``bower.json`` and ``package.json`` files. Remove also symlink in ``web/fonts``
- You can move your bower and npm dependencies in ``composer.json`` of your project or bundle
- Datatable configuration have been moved from the `data` tag to a `yaml` configuration
- `Grunt` configuration has been modified to be more handled by the bundles

Other changes
-------------

- PHP requirement has been updated to 5.5
- Version of ``symfony/symfony`` is updated to 2.8.1
- Version of ``twig/twig`` is updated to ~1.23
- Version of ``friendsofsymfony/http-cache-bundle`` is updated to 1.3.6
- Flow.js dependency has been moved from CmsBundle to MediaAdminBundle
- Media alternatives files (mainly images) have new auto-generated names
- Deprecation of the `ContainerAware` class have been suppressed
- Nodes can have a new options for the theme : use the website default theme
- Abstract test classes have been created to help free the memory used in the tests

Configuration changes
---------------------

- ``pace.js`` is removed and replace by a custom component ``OpenOrchestra.AjaxLoader.AjaxLoaderView``
- To get the Back Office compatible again with Internet Explorer 9, some grunt tasks have been rewrote. Be
  sure to update your Open Orchestra tasks according to `these Pull Request`_
- ``gridstack.js`` is removed
- ``lodash.js`` is removed
- Npm package ``grunt-js-test`` is added to composer.json of ``CmsBundle``

------------

Changelog 1.1.0-alpha4 to 1.1.0-beta
------------------------------------

Configuration changes
---------------------

- Adding bundle ``MongoDBMigrationsBundle`` `#853`_
- Dependencies versions are fixed in cms bundle: ``merge ~1.2.0``, ``backbone ~1.2.3``, ``jquery-minicolors ~2.2.3``, ``backbone.wreqr ~1.3.5``. `#1397`_
- Bower dependency ``underscore`` is removed, this package is included by ``backbone`` `#1397`_
- Dependencies versions are fixed in admin bundle: ``merge ~1.2.0``, ``backbone ~1.2.3``, ``backbone.wreqr ~1.3.5``. `#136`_
- Add migration script for update of user groups collection,  futher documation about migration in http://open-orchestra.readthedocs.org/en/latest/hosting_guide/migration.html `#531`_

Bug fixes
---------

- Refresh template when edit template form is submitted `#1534`_
- fix error on role delete `#1530`_
- Fix error 404 in the form keyword choice type when you create a new keyword `#1520`_
- The children direction now can be  specified in nodes `#1519`_
- Fix translation labels of defaultListable field in content type form `#1509`_
- The event ``ContentTypeEvents::CONTENT_TYPE_UPDATE`` is dispatched only when content type form is valid `#1505`_
- fix the display of the media block icon `#1502`_
- Fix TinyMCE content display after form submission `#1500`_
- disallow roles with same from and to status `#1498`_
- Fix searchable option of content type field `#1491`_
- Make the color picker working in all contexts `#1488`_
- Fix css ie11 template and node contribution `#1486`_
- fix indent after hide preview button on global pages `#1484`_
- Fix prototype bug `#1482`_
- Refresh navigation menu after a new element has been created in a list `#1479`_
- Don't display the transverse blocks in the blocks panel when editing a transverse node `#1474`_
- Field choice with option multiple disabled `#1472`_
- hide the preview button on global pages (transverse) `#1471`_
- Fix custom field selection on content type creation `#1460`_
- In navigation panel, a root menu is hidden if these submenus aren't visible `#1459`_
- Remove native media option in tinymce context menu `#1455`_
- Nodes with dynamic route pattern can't be added in menus `#1450`_
- Published nodes can be moved `#1443`_
- Fix several bugs for IE9 in the Back Office `#1427`_
- Condition transformer does not use constructor anymore but setter `#1422`_
- Datepicker in content forms `#1406`_
- Suppress multiple load in panel context `#1404`_
- Pass the 'disabled' option to the block form strategy when required `#1399`_
- Fix error 404 Jcrop.gif when a picture is cropped `#1398`_
- Activate tinyMce in collection prototype context `#1396`_
- Fix jarvis widget header style in BackOffice `#1388`_
- disable load dataparemeter in modal context `#1386`_
- When a node is duplicated there's no more node group role creation `#1385`_
- Fix error type of property ``updateAt`` in content type schema `#24`_
- Media references are correctly placed `#186`_
- Fix breadcrumb form in media modal `#182`_
-  Fix display media upload with short window `#180`_
- Fix resize with picture ratio lower than 1 `#178`_
- fix missed translation (open_orchestra_media_admin.block.display_media.title) `#162`_
- A super admin user can view all sites when he creates a new form `#160`_
- Fix media selection in tinyMce `media-admin#158`_
- Media events are not properly dispatched `#156`_
- Allow recursive merge on tinyMce Stfalcon parameters `#142`_
- Status of contents containing a media field can now be changed `#138`_
- Remove media management in blocks when form is disabled `#137`_
- Fix access denied error on published node access `#524`_
- Fix broken varnish 4 vcl `#29`_
- As the pixel developer google chrome is not more accessible, I have suppressed the selenium role from our provisioning `#27`_
- Fix back-to-list buttons on top in modal upload `media-admin#172`_

New features
------------

- Block menu caches are invalidated when a node is removed, moved, restore and the status of a node changes . `#1531`_
- add voter on role usage `#1530`_
- increase ergo fo group form `#1522`_
- When a content type is deleted, navigation menu is refreshed `#1521`_
- When a website is created, an homepage for this site is also created. `#1518`_
- refresh the page after website creation to show it in the fixed top nav list `#1515`_
- fix save & back-to-list buttons on top `#1499`_
- Move template menu entry from Editorial to Administration `#1485`_
- allow to extend js form's behavior `#1473`_
- add loader in group tab view `#1467`_
- change new link to button `#1466`_
- Add sortable option to the datatable `#1451`_
- add boolean expression in keywords form type filter `#1442`_
- Remove max length option on email field type `#1439`_
- Datatable action buttons are disabled if the user hasn't the rights `#1438`_
- add notification colors `#1433`_
- Media roles gestion for each folders are available in the group panel `#1416`_
- Allow published node deletion `#1405`_
- add break line in tooltip helper (\n) `#1400`_
- allow published node delete `#1384`_
- auto-select type of search in datatable for content field type `#1382`_
- activate content list block in front `display#202`_
- Node cache-control policy differs with or without ESI support `#193`_
- allow end user to format boolean condition in keywords filter `#41`_
- Media can be filtered on type when displayed from media folder `#179`_
- Media library: applications can now describe their own specific alternatives image formats `#144`_
- Add a "Back to list" button on the media upload form in a modal context `#133`_
- Media selection integrates now the alternative selector `#132`_
- Published flag feature `#529`_

Deprecated
----------

- ``initializeNewNode``  is deprecated and replaced by ``initializeNode`` in class ``OpenOrchestra\Backoffice\Manager\NodeManager``. this method will be removed in 1.2.0 `#1518`_
- rename class ``UpdateNodeRedirectionSubscriber`` to ``UpdateRedirectionNodeSubscriber`` `#1503`_
- ``OpenOrchestra\Backoffice\Form\DataTransformer\ChoiceArrayToStringTransformer`` is now deprecated will be removed in 1.2.0 `#1472`_
- ``OpenOrchestra\Backoffice\Form\DataTransformer\ChoiceStringToArrayTransformer`` is now deprecated will be removed in 1.2.0 `#1472`_
- ``FolderRepository:findAllRootFolder`` method in ``OpenOrchestra\MediaModelBundle\Repository`` namespace has been deprecated  use ``findAllRootFolderBySiteId`` `#177`_
- Update the media twig functions `#168`_

Possible BC breaker
-------------------

- include string indexation of site alias in error pages path. `#1503`_
- ``DisplayBundle/DisplayBlock/Strategies/AbstractStrategy:getCacheTags()`` is now abstract and must therefore be explicitally implemented on each display strategy `#1457`_
- Move form from backofficeBundle `#1425`_
- Move Model and repository from BackofficeBundle `#1424`_
- Move BackofficeBundle manager `#1423`_
- Move BackofficeBundle subscribers `#1422`_
- Move BackofficeBundle listener `#1421`_
- Move Backoffice display block folder `#1417`_
- Move Backoffice display icon folder `#1417`_
- Move Backoffice initializer folder `#1417`_
- change way to load dataparameter in refresh menu context `#1386`_
- DisplayBundle/DisplayBlock/Strategies/AbstractStrategy:getCacheTags() is now abstract and must therefore be explicitally implemented on each display strategy `display#200`_
- Disable multi website in media folder `#185`_
- Fixtures for production are cleaned `#530`_
- In the front, the nodes should have the published flag to be displayed `#529`_

Other changes
-------------

- New Bundle : MediaAdminModelBundle `#831`_
- Upgrade to symfony 2.8.3 `#72`_
- Role ``ROLE_ACCESS_MOVE_NODE`` is renamed to ``ROLE_ACCESS_MOVE_TREE`` and is now a global role `#1480`_
- Deleted nodes order is -1 `#1440`_
- Redirect to the user edit form after user creation `#1408`_
- Refacto const display strategies name `#1407`_
- Replace strings ``elastica_search`` and ``elastica_list`` by class constant `#21`_
- Get master request in method where it is used and not in a constructor `#150`_
- Add the robots meta in the page header `FrontBundle#138`_
- Unskip a MediaStorageManager unit test `#8`_
- Node order validator don't checks deleted nodes `#526`_
- Add findByNodeAndSiteSortedByVersion() request in NodeRepository `#514`_
- Suppression of install of nodeJS by the provisioning, it is now installed by ``composer-extra-assets``. use now ``./bin/grunt`` for grunt and not ``./node_modules/.bin/grunt`` `#34`_

------------

Changelog 1.1.0-beta to 1.1.0-RC
--------------------------------


New features
------------

- Test on mandatory main alias in site form `#1542`_
- Remove permanently an entity in trash can `#1539`_
- Enhance area form in template, node and area `#1537`_
- When a content is deleted, it's removed from elastica index `#25`_
- When a content is restored, it's added from elastica index `#25`_
- A media root folder is created when a new website is created `#190`_

Bug fixes
---------

- Fix position of property `validationGroups` in method `isValid` of `BaseApiBundle/Controller/BaseController` `#76`_
- Fix transform area from another site as the current site `#1544`_
- Unused blocks are now definitely suppressed from DB when deleted from a node and used no more `#1540`_
- Fix error type of property ``updateAt`` in content type schema `#24`_
- A required oo_media_choice form type is now correctly handled `#195`_
- Remove link constraint on media display block `#194`_
- Method ``testUniquenessInContext`` is now based on ``nodeId`` and not ``name`` `#543`_
- Demo fixtures are updated to present block usage references `#542`_
- Path on node is updated only if node is not deleted `#541`_

Other changes
-------------

- Get master request in method where it is used and not in a constructor `#150`_

Possible BC breaker
-------------------

- The `TrashItem` document has a new property `type`
- The `TrashItemInterface` has a new property `type`
- The `TrashItemRepositoryInterface` has a new method `findByEntity($entityId)`

Manual changes
--------------
- The `BlockContainerInterface` has a new method: `removeBlockWithKey`

------------

Changelog 1.1.0-RC to 1.1.0
---------------------------

New features
------------

- **[open-orchestra]** updating fixtures console command to allow user choose the type of fixtures to load and add a dev environment `#888 <https://github.com/open-orchestra/open-orchestra/pull/888>`_ (*djamnazi*)
- **[open-orchestra-base-bundle]** Update requirement ``symfony/symfony`` to ``~2.8.4`` `#81 <https://github.com/open-orchestra/open-orchestra-base-bundle/pull/81>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** It is no longer possible to delete a block of global page if it is used `#1599 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1599>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Adding attribute ``boLabel`` on Node , used to generate tree in the Back Office `#1586 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1586>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Remove delete button on edit modal view and deplace it #near edit button `#1581 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1581>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** Remove choice groups  in edit user if the user is super admin `#1572 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1572>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Remove role super admin of user admin in production fixture `#1572 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1572>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Remove edit button for tranverse page `#1569 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1569>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** When a content is deleted or his status is updated tag ``'contentId-' . $contentId`` is invalidate. `#1568 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1568>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** When a content type is deleted or updated tag ``''contentType-' . $contentType`` is invalidate. `#1568 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1568>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** ``openOrchestra\Backoffice\Form\Type\ComponentRoleChoiceType`` can display roles of multiple role collector `#1567 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1567>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** In navigation panel, The global page is directly accessible. `#1561 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1561>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Add modification date for versions into global page and node. `#1559 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1559>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** Remove full screen for jarvis widget `#1558 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1558>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** The role parameter to create an navigation strategy is no longer required `#1556 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1556>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Adding voter to forbid removing node root `#1555 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1555>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Add role ``acess``, ``update``, ``create`` for error nodes. `#1549 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1549>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** add content search widget in configurable content block `#1548 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1548>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Move actions buttons to the ribbon `#1545 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1545>`_ (*djamnazi*)
- **[open-orchestra-cms-bundle]** test on mandatory main alias in site form `#1542 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1542>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Remove permanently a entity in trash can `#1539 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1539>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** enhance area form in template, node and area `#1537 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1537>`_ (*itkg-nanne*)
- **[open-orchestra-elastica-bundle]** When a content is deleted, it's removed to elastica index `#25 <https://github.com/open-orchestra/open-orchestra-elastica-bundle/pull/25>`_ (*alavieille*)
- **[open-orchestra-elastica-bundle]** When a content is restored, it's added to elastica index `#25 <https://github.com/open-orchestra/open-orchestra-elastica-bundle/pull/25>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** Message in form ``oo_media_choice`` when no image is selected is translated `#202 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/202>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** A root folder is created when a new website is created `#190 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/190>`_ (*alavieille*)
- **[open-orchestra-media-bundle]** Add default strategy to display media `#183 <https://github.com/open-orchestra/open-orchestra-media-bundle/pull/183>`_ (*alavieille*)
- **[open-orchestra-media-file-bundle]** Add expires attribute into the header of HTTP request. `#14 <https://github.com/open-orchestra/open-orchestra-media-file-bundle/pull/14>`_ (*KevinArtus*)
- **[open-orchestra-model-bundle]**  Add script migration to rename role  ROLE_ACCESS_MOVE_NODE by ROLE_ACCESS_MOVE_TREE `#563 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/563>`_ (*alavieille*)
- **[open-orchestra-model-bundle]** Add migration for attribute ``boLabel`` `#561 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/561>`_ (*alavieille*)
- **[open-orchestra-model-bundle]** Create HomePage by load fixtures `#549 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/549>`_ (*djamnazi*)
- **[open-orchestra-workflow-function-bundle]** Remove link right form in edit user if the user is super admin `#99 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/99>`_ (*alavieille*)
- **[open-orchestra-workflow-function-bundle]** Add voter to check workflow state of statusable document `#97 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/97>`_ (*alavieille*)

Possible BC breaker
-------------------

- **[open-orchestra-cms-bundle]** ``OpenOrchestra\GroupBundle\EventListener\AbstractNodeGroupRoleListener`` is replaced by ``OpenOrchestra\GroupBundle\EventSubscriber\AbstractNodeGroupRoleSubscriber`` `#1582 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1582>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** ``OpenOrchestra\GroupBundle\EventListener\AddNodeGroupRoleForGroupListener`` is replaced by ``OpenOrchestra\GroupBundle\EventSubscriber\NodeGroupRoleForGroupSubscriber`` `#1582 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1582>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** ``OpenOrchestra\GroupBundle\EventListener\AddNodeGroupRoleForNodeListener`` is replaced by ``OpenOrchestra\GroupBundle\EventSubscriber\NodeGroupRoleForNodeSubscriber`` `#1582 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1582>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Deleted PageConfigurationButtonView.coffee `#1581 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1581>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** `` OpenOrchestra\UserAdminBundle\Event\UserFacadeEvent`` take a new argument `user` which is the user transformed `#1572 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1572>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** ``openOrchestra\Backoffice\Form\Type\ComponentRoleChoiceType`` take an array of role collector in parameter. `#1567 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1567>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** ``OpenOrchestra\Backoffice\NavigationPanel\Strategies\GeneralNodesPanelStrategy`` is renamed by ``OpenOrchestra\Backoffice\NavigationPanel\Strategies\TransverseNodePanelStrategy`` `#1561 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1561>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** The class ``OpenOrchestra\Backoffice\NavigationPanel\Strategies\AbstractNavigationPanelStrategy`` is deprecated and will be removed in 1.2.0 use ``OpenOrchestra\Backoffice\NavigationPanel\Strategies\AbstractNavigationStrategy`` `#1556 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1556>`_ (*alavieille*)
- **[open-orchestra-media-bundle]** Twig of method displayMedia in all display strategy are moved of ``OpenOrchestraMediaBundle:BBcode/FullDisplay`` to ``OpenOrchestraMediaBundle:DisplayMedia/FullDisplay`` `#183 <https://github.com/open-orchestra/open-orchestra-media-bundle/pull/183>`_ (*alavieille*)
- **[open-orchestra-model-bundle]** The `TrashItem` document has a new property `type` `#541 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/541>`_ (*alavieille*)
- **[open-orchestra-model-interface]** The `TrashItemInterface` has a new property `type` `#172 <https://github.com/open-orchestra/open-orchestra-model-interface/pull/172>`_ (*alavieille*)
- **[open-orchestra-model-interface]** The `TrashItemRepositoryInterface` has a new method `findByEntity($entityId)` `#172 <https://github.com/open-orchestra/open-orchestra-model-interface/pull/172>`_ (*alavieille*)

Bug fixes
---------

- **[open-orchestra-base-api-bundle]** Fix position of property `validationGroups` in method `isValid` of `BaseApiBundle/Controller/BaseController` `#76 <https://github.com/open-orchestra/open-orchestra-base-api-bundle/pull/76>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix error on field default value if field type is changed in content type form `#1602 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1602>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** When you save multiple tinymce, there are saved correctly `#1601 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1601>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** create user with media folder access and create role for functional test `#1595 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1595>`_ (*djamnazi*)
- **[open-orchestra-cms-bundle]** Fix access denied when edit node without ``role_access_site`` `#1593 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1593>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix error access denied when select an other version node `#1592 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1592>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Refresh node view when edit form of node  is submitted `#1591 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1591>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix bug updating status of node with the update role of node of other type `#1590 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1590>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** add constraints for email user unicity `#1587 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1587>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Add label option into group FormType `#1585 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1585>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** Activate subform content search in content type form context `#1583 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1583>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** When a group is updated model group roles are correctly set `#1582 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1582>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Add constraint Unique on group `#1565 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1565>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix transform correctly a type double in a string value. `#1564 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1564>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Remove cursor move of dashboard widgets `#1563 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1563>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix transform area from another site as the current site `#1544 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1544>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Unused blocks are now definitivly suppressed from DB when deleted from a node and used no more `#1540 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1540>`_ (*itkg-ngilain*)
- **[open-orchestra-display-bundle]** set shared max age if ESI cash is supported `#209 <https://github.com/open-orchestra/open-orchestra-display-bundle/pull/209>`_ (*djamnazi*)
- **[open-orchestra-elastica-bundle]** Fix error type of property ``updateAt`` in content type schema `#24 <https://github.com/open-orchestra/open-orchestra-elastica-bundle/pull/24>`_ (*alavieille*)
- **[open-orchestra-front-bundle]** Fix generate url command site map generate `#158 <https://github.com/open-orchestra/open-orchestra-front-bundle/pull/158>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** fix folder update error when user don't has the update role `#208 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/208>`_ (*djamnazi*)
- **[open-orchestra-media-admin-bundle]** In a content, the selection of a media with no alternative is now correctly stored `#207 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/207>`_ (*itkg-ngilain*)
- **[open-orchestra-media-admin-bundle]** Rename descriptions for roles media and folders. `#206 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/206>`_ (*KevinArtus*)
- **[open-orchestra-media-admin-bundle]** hide edit button if user don't have update role in media folder `#204 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/204>`_ (*djamnazi*)
- **[open-orchestra-media-admin-bundle]** If an user hasn't role ``ROLE_ACCESS_UPDATE_MEDIA``, he can't edit a media `#201 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/201>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** A required oo_media_choice form type is now correctly handled `#195 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/195>`_ (*itkg-ngilain*)
- **[open-orchestra-media-admin-bundle]** Remove link constraint on media display block `#194 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/194>`_ (*itkg-ngilain*)
- **[open-orchestra-model-bundle]** Re-activate site search by alias domain `#560 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/560>`_ (*itkg-nanne*)
- **[open-orchestra-model-bundle]** use currentlyPublished tag to display menu and footer `#546 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/546>`_ (*itkg-nanne*)
- **[open-orchestra-model-bundle]** method ``hasOtherNodeWithSameParentAndOrder```of ``NodeRepository`` check only on default nodes `#545 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/545>`_ (*alavieille*)
- **[open-orchestra-model-bundle]** method ``testUniquenessInContext`` is now based on ``nodeId`` and not ``name`` `#543 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/543>`_ (*alavieille*)
- **[open-orchestra-model-bundle]** Demo fixtures are updated to present block usage references `#542 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/542>`_ (*itkg-ngilain*)
- **[open-orchestra-model-bundle]** Path on node is updated only if node isn't deleted `#541 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/541>`_ (*alavieille*)
- **[open-orchestra-model-interface]** Fix type ``nodeId`` in php doc of ``NodeInterface`` and ``ReadNodeInterface`` `#176 <https://github.com/open-orchestra/open-orchestra-model-interface/pull/176>`_ (*alavieille*)

Other changes
-------------

- **[open-orchestra-cms-bundle]** Corrected translation. `#1600 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1600>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** Rename navigation menu status and Role `#1589 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1589>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** Hide addpage button if no root page `#1560 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1560>`_ (*djamnazi*)
- **[open-orchestra-front-bundle]** Get master request in method where it is used and not in a constructor `#150 <https://github.com/open-orchestra/open-orchestra-front-bundle/pull/150>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** Migration scripts to explain in the changelog (main configuration changes + migration configuration) `#200 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/200>`_ (*itkg-ngilain*)
- **[open-orchestra-media-admin-bundle]** Remove MediaInterface::MEDIA_PREFIX `#198 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/198>`_ (*itkg-ngilain*)
- **[open-orchestra-model-bundle]** Remove "published to draft' role for production fixtures. `#548 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/548>`_ (*KevinArtus*)
- **[open-orchestra-workflow-function-bundle]** corrected translations. `#104 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/104>`_ (*KevinArtus*)
- **[open-orchestra-workflow-function-bundle]** Rename navigation menu workflow `#102 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/102>`_ (*KevinArtus*)
- **[open-orchestra-workflow-function-bundle]** Remove "published to draft' role for validator on fixtures. `#95 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/95>`_ (*KevinArtus*)

Deprecated
----------

- **[open-orchestra-cms-bundle]** class ``OpenOrchestra\Backoffice\EventSubscriber\ChangeContentStatusSubscriber`` s deprecated in 1.1.0 and will be removed in 1.2.0, it is replace by ContentUpdateCacheSubscriber `#1568 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1568>`_ (*alavieille*)

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/1.0...v1.1.0
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/1.0...v1.1.0
.. _`BBCode bundle`: https://github.com/open-orchestra/open-orchestra-bbcode-bundle/compare/1.0...v1.1.0
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/1.0...v1.1.0
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/1.0...v1.1.0
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/1.0...v1.1.0
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/1.0...v1.1.0
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/1.0...v1.1.0
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/1.0...v1.1.0
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/1.0...v1.1.0
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/1.0...v1.1.0
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/1.0...v1.1.0
.. _`Workflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/1.0...v1.1.0
.. _`Media admin bundle`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/compare/1.0...v1.1.0
.. _`Orchestra libs`: https://github.com/open-orchestra/open-orchestra-libs/compare/1.0...v1.1.0
.. _`Orchestra Mongo libs`: https://github.com/open-orchestra/open-orchestra-mongo-libs/compare/1.0...v1.1.0
.. _`Media file bundle`: https://github.com/open-orchestra/open-orchestra-media-file-bundle/compare/1.0...v1.1.0
.. _`Elastica bundle`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/compare/1.0...v1.1.0
.. _`have been deprecated`: https://github.com/open-orchestra/open-orchestra-model-interface/pull/119
.. _`PHP driver PHP-FFMpeg`: https://github.com/PHP-FFMpeg/PHP-FFMpeg
.. _`documentation`:../developer_guide/entity_list_ajax_pagination.html
.. _`information in documentation`:../developer_guide/bundle_configuration.html
.. _`futher information in the documentation`:../developer_guide/media_gaufrette.html
.. _`assets documentation`:../developer_guide/assets_bower_npm.html
.. _`these Pull Request`: https://github.com/open-orchestra/open-orchestra/pull/791/files
.. _`#853`: https://github.com/open-orchestra/open-orchestra/pull/853
.. _`#1397`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1397
.. _`#136`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/136
.. _`#531`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/531
.. _`#1534`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/534
.. _`#1520`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1520
.. _`#1519`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1519
.. _`#1509`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1509
.. _`#1505`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1505
.. _`#1502`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1502
.. _`#1500`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1500
.. _`#1498`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1498
.. _`#1491`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1491
.. _`#1488`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1488
.. _`#1486`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1486
.. _`#1484`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1484
.. _`#1482`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1482
.. _`#1479`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1479
.. _`#1474`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1474
.. _`#1471`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1471
.. _`#1460`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1460
.. _`#1459`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1459
.. _`#1455`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1455
.. _`#1450`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1450
.. _`#1443`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1443
.. _`#1427`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1427
.. _`#1406`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1406
.. _`#1404`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1404
.. _`#1399`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1399
.. _`#1398`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1398
.. _`#1396`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1396
.. _`#1388`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1388
.. _`#1385`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1385
.. _`#24`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/pull/24
.. _`#186`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/186
.. _`#182`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/182
.. _`#180`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/180
.. _`#178`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/178
.. _`#162`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/162
.. _`#160`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/160
.. _`media-admin#158`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/158
.. _`#156`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/156
.. _`#142`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/142
.. _`#138`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/138
.. _`#137`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/137
.. _`#524`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/524
.. _`#29`: https://github.com/open-orchestra/open-orchestra-provision/pull/29
.. _`#27`: https://github.com/open-orchestra/open-orchestra-provision/pull/27
.. _`media-admin#172`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/172
.. _`#1531`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1531
.. _`#1530`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1530
.. _`#1522`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1522
.. _`#1521`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1521
.. _`#1515`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1515
.. _`#1499`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1499
.. _`#1485`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1485
.. _`#1473`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1473
.. _`#1467`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1467
.. _`#1466`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1466
.. _`#1451`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1451
.. _`#1442`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1442
.. _`#1439`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1439
.. _`#1438`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1438
.. _`#1433`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1433
.. _`#1416`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1416
.. _`#1405`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1405
.. _`#1400`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1400
.. _`#1384`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1384
.. _`#1382`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1382
.. _`display#202`: https://github.com/open-orchestra/open-orchestra-display-bundle/pull/202
.. _`#193`: https://github.com/open-orchestra/open-orchestra-display-bundle/pull/193
.. _`#41`: https://github.com/open-orchestra/open-orchestra-libs/pull/41
.. _`#179`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/179
.. _`#144`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/144
.. _`#133`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/133
.. _`#132`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/132
.. _`#1518`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1518
.. _`#1472`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1472
.. _`#177`: https://github.com/open-orchestra/open-orchestra-media-bundle/pull/177
.. _`#168`: https://github.com/open-orchestra/open-orchestra-media-bundle/pull/168
.. _`#1503`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1503
.. _`#1457`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1457
.. _`#1425`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1425
.. _`#1424`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1424
.. _`#1423`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1423
.. _`#1422`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1422
.. _`#1421`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1421
.. _`#1417`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1417
.. _`#1386`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1386
.. _`display#200`: https://github.com/open-orchestra/open-orchestra-display-bundle/pull/200
.. _`#185`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/185
.. _`#530`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/530
.. _`#529`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/529
.. _`#831`: https://github.com/open-orchestra/open-orchestra/pull/831
.. _`#72`: https://github.com/open-orchestra/open-orchestra-base-bundle/pull/72
.. _`#1480`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1480
.. _`#1440`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1440
.. _`#1408`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1408
.. _`#1407`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1407
.. _`#21`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/pull/21
.. _`#150`: https://github.com/open-orchestra/open-orchestra-front-bundle/pull/150
.. _`FrontBundle#138`: https://github.com/open-orchestra/open-orchestra-front-bundle/pull/138
.. _`#8`: https://github.com/open-orchestra/open-orchestra-media-file-bundle/pull/8
.. _`#526`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/526
.. _`#514`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/514
.. _`#34`: https://github.com/open-orchestra/open-orchestra-provision/pull/34
