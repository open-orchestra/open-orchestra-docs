CHANGELOG for 1.1.0-beta
========================

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
- `Worflow function bundle`_
- `Media admin bundle`_
- `Orchestra libs`_
- `Orchestra Mongo libs`_
- `Media file bundle`_
- `Elastica bundle`_

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
- Fix media selection in tinyMce `#158`_
- Media events are not properly dispatched `#156`_
- Allow recursive merge on tinyMce Stfalcon parameters `#142`_
- Status of contents containing a media field can now be changed `#138`_
- Remove media management in blocks when form is disabled `#137`_
- Fix access denied error on published node access `#524`_
- Fix broken varnish 4 vcl `#29`_
- As the pixel developer google chrome is not more accessible, I have suppressed the selenium role from our provisioning `#27`_
- Fix back-to-list buttons on top in modal upload `#172`_

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
- activate content list block in front `#202`_
- Node cache-control- `Cms bundle`_
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
- `Worflow function bundle`_
- `Media admin bundle`_
- `Orchestra libs`_
- `Orchestra Mongo libs`_
- `Media file bundle`_
- `Elastica bundle`_
 policy differs with or without ESI support `#193`_
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
- DisplayBundle/DisplayBlock/Strategies/AbstractStrategy:getCacheTags() is now abstract and must therefore be explicitally implemented on each display strategy `#200`_
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
- Add the robots meta in the page header `#138`_
- Unskip a MediaStorageManager unit test `#8`_
- Node order validator don't checks deleted nodes `#526`_
- Add findByNodeAndSiteSortedByVersion() request in NodeRepository `#514`_
- Suppression of install of nodeJS by the provisioning, it is now installed by ``composer-extra-assets``. use now ``./bin/grunt`` for grunt and not ``./node_modules/.bin/grunt `` `#34`_

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`BBCode bundle`: https://github.com/open-orchestra/open-orchestra-bbcode-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Workflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Media admin bundle`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Orchestra libs`: https://github.com/open-orchestra/open-orchestra-libs/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Orchestra Mongo libs`: https://github.com/open-orchestra/open-orchestra-mongo-libs/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Media file bundle`: https://github.com/open-orchestra/open-orchestra-media-file-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`Elastica bundle`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/compare/v1.1.0-alpha4...v1.1.0-beta
.. _`#853`: https://github.com/open-orchestra/open-orchestra/pull/853
.. _`#1397`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1397
.. _`#136`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/136
.. _`#531`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/531
.. _`#1534`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/534
.. _`#1530`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1530
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
.. _`#1472`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1472
.. _`#1471`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1471
.. _`#1460`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1460
.. _`#1459`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1459
.. _`#1455`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1455
.. _`#1450`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1450
.. _`#1443`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1443
.. _`#1427`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1427
.. _`#1422`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1422
.. _`#1406`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1406
.. _`#1404]`: (https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1404
.. _`#1399`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1399
.. _`#1398`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1398
.. _`#1396`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1396
.. _`#1388`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1388
.. _`#1386`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1386
.. _`#1385`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1385
.. _`#24`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/pull/24
.. _`#186`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/186
.. _`#182`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/182
.. _`#180`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/180
.. _`#178`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/178
.. _`#162`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/162
.. _`#160`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/160
.. _`#158`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/158
.. _`#156`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/156
.. _`#142`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/142
.. _`#138`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/138
.. _`#137`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/137
.. _`#524`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/524
.. _`#29`: https://github.com/open-orchestra/open-orchestra-provision/pull/29
.. _`#27`: https://github.com/open-orchestra/open-orchestra-provision/pull/27
.. _`#172`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/172
.. _`#1531`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1531
.. _`#1530`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1530
.. _`#1522`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1522
.. _`#1521`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1521
.. _`#1518`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1518
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
.. _`#202`: https://github.com/open-orchestra/open-orchestra-display-bundle/pull/202
.. _`#193`: https://github.com/open-orchestra/open-orchestra-display-bundle/pull/193
.. _`#41`: https://github.com/open-orchestra/open-orchestra-libs/pull/41
.. _`#179`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/179
.. _`#144`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/144
.. _`#133`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/133
.. _`#132`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/132
.. _`#529`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/529
.. _`#1518`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1518
.. _`#1503`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1503
.. _`#1472`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1472
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
.. _`#1417`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1417
.. _`#1417`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1417
.. _`#1386`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1386
.. _`#200`: https://github.com/open-orchestra/open-orchestra-display-bundle/pull/200
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
.. _`#138`: https://github.com/open-orchestra/open-orchestra-front-bundle/pull/138
.. _`#8`: https://github.com/open-orchestra/open-orchestra-media-file-bundle/pull/8
.. _`#526`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/526
.. _`#514`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/514
.. _`#34`: https://github.com/open-orchestra/open-orchestra-provision/pull/34
