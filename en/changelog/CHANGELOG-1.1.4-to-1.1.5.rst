CHANGELOG from 1.1.4 to 1.1.5
=============================

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
- `User bundle`_
- `Theme bundle`_
- `Workflow function bundle`_
- `Media admin bundle`_
- `Orchestra libs`_
- `Orchestra Mongo libs`_
- `Media file bundle`_
- `Elastica bundle`_

Other changes
-------------

- **[open-orchestra-cms-bundle]** Greatly reduce the generation time of some node facades and status facades by muting some expansives attributes when not required by the context of the call `#1923 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1923>`__ (*ngilain*)
- **[open-orchestra-cms-bundle]** Optimization loading of underscore templates for the node and the list view `#1880 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1880>`__ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** Optimize performances on folder creation `#306 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/306>`__ (*ngilain*)

[OO-HOTFIX]
-----------

- **[open-orchestra-cms-bundle]** Temporary disable the possibility to delete a status in order to speed up significantly API responses including status `#1920 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1920>`__ (*ngilain*)

New features
------------

- **[open-orchestra-cms-bundle]** Add GroupRepository::findAllWithSiteId `#1919 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1919>`__ (*ngilain*)
- **[open-orchestra-media-bundle]** Add index folder document `#229 <https://github.com/open-orchestra/open-orchestra-media-bundle/pull/229>`__ (*alavieille*)

Bug fixes
---------

- **[open-orchestra-cms-bundle]** Authorize status update when user is super admin `#1851 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1851>`__ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix cache tag block `#1846 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1846>`__ (*alavieille*)
- **[open-orchestra-cms-bundle]** Optimized access of model group role `#1839 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1839>`__ (*alavieille*)
- **[open-orchestra-display-bundle]** Fix slideshow block in IE11 `#240 <https://github.com/open-orchestra/open-orchestra-display-bundle/pull/240>`__ (*alavieille*)
- **[open-orchestra-libs]** Fix xml and yaml reader of search metadata `#62 <https://github.com/open-orchestra/open-orchestra-libs/pull/62>`__ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** When a media modal is closed, it's correctly removed of DOM `#289 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/289>`__ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** Fix button browse of form media type `#276 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/276>`__ (*alavieille*)

[OO-PERFORMANCE]
----------------

- **[open-orchestra-mongo-libs]** Improve singleHydrateAggregateQuery performance `#51 <https://github.com/open-orchestra/open-orchestra-mongo-libs/pull/51>`__ (*itkg-canne*)

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v1.1.4...v1.1.5
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v1.1.4...v1.1.5
.. _`BBCode bundle`: https://github.com/open-orchestra/open-orchestra-bbcode-bundle/compare/v1.1.4...v1.1.5
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v1.1.4...v1.1.5
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v1.1.4...v1.1.5
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v1.1.4...v1.1.5
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v1.1.4...v1.1.5
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v1.1.4...v1.1.5
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/v1.1.4...v1.1.5
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v1.1.4...v1.1.5
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v1.1.4...v1.1.5
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v1.1.4...v1.1.5
.. _`Workflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v1.1.4...v1.1.5
.. _`Media admin bundle`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/compare/v1.1.4...v1.1.5
.. _`Orchestra libs`: https://github.com/open-orchestra/open-orchestra-libs/compare/v1.1.4...v1.1.5
.. _`Orchestra Mongo libs`: https://github.com/open-orchestra/open-orchestra-mongo-libs/compare/v1.1.4...v1.1.5
.. _`Media file bundle`: https://github.com/open-orchestra/open-orchestra-media-file-bundle/compare/v1.1.4...v1.1.5
.. _`Elastica bundle`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/compare/v1.1.4...v1.1.5
