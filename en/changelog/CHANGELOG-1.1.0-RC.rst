CHANGELOG from 1.1.0-beta to 1.1.0-RC
=====================================

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

- The `TrashItem` document has a new property `type` `#541`_
- The `TrashItemInterface` has a new property `type` `#172`_
- The `TrashItemRepositoryInterface` has a new method `findByEntity($entityId)` `#172`_

Manual changes
--------------
- The `BlockContainerInterface` has a new method: `removeBlockWithKey` `#173`_

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`BBCode bundle`: https://github.com/open-orchestra/open-orchestra-bbcode-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v1.1.0-beta...v1.1.0-RC
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`Workflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`Media admin bundle`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`Orchestra libs`: https://github.com/open-orchestra/open-orchestra-libs/compare/v1.1.0-beta...v1.1.0-RC
.. _`Orchestra Mongo libs`: https://github.com/open-orchestra/open-orchestra-mongo-libs/compare/v1.1.0-beta...v1.1.0-RC
.. _`Media file bundle`: https://github.com/open-orchestra/open-orchestra-media-file-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`Elastica bundle`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/compare/v1.1.0-beta...v1.1.0-RC
.. _`#1542`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1542
.. _`#1539`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1539
.. _`#1537`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1537
.. _`#25`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/pull/25
.. _`#25`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/pull/25
.. _`#190`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/190
.. _`#76`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/pull/76
.. _`#1544`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1544
.. _`#1540`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1540
.. _`#24`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/pull/24
.. _`#195`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/195
.. _`#194`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/194
.. _`#543`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/543
.. _`#542`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/542
.. _`#541`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/541
.. _`#150`: https://github.com/open-orchestra/open-orchestra-front-bundle/pull/150
.. _`#541`: https://github.com/open-orchestra/open-orchestra-model-bundle/pull/541
.. _`#172`: https://github.com/open-orchestra/open-orchestra-model-interface/pull/172
.. _`#172`: https://github.com/open-orchestra/open-orchestra-model-interface/pull/172
.. _`#173`: https://github.com/open-orchestra/open-orchestra-model-interface/pull/173
