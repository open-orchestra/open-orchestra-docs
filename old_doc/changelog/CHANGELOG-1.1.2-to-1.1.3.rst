CHANGELOG from 1.1.2 to 1.1.3
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

Bug fixes
---------

- **[open-orchestra-cms-bundle]** Removing boLabel of the error nodes `#1828 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1828>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Radio button `Link to the current site` is only available when you create a content `#1827 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1827>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix elements count in content pagination. `#1825 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1825>`_ (*itkg-canne*)
- **[open-orchestra-cms-bundle]** Fix currently published when a published content is duplicate `#1824 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1824>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix fill label block form `#1806 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1806>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix dependency of modelBundle in class fieldTypeType `#1805 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1805>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fixing of category of item template in the right form `#1796 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1796>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Change the appConfigurationView creation order `#1784 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1784>`_ (*ngilain*)
- **[open-orchestra-libs]** Fix xml and yaml reader of search metadata `#62 <https://github.com/open-orchestra/open-orchestra-libs/pull/62>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** MediaTransformer need now a instance of TranslationChoiceManagerInterface instead of TranslationChoiceManager `#269 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/269>`_ (*alavieille*)
- **[open-orchestra-workflow-function-bundle]** Prevents the deletion of workflow function if it used by an user `#135 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/135>`_ (*alavieille*)

Deprecated
----------

- **[open-orchestra-cms-bundle]** ContentRepository::countByContentTypeInLastVersion method is deprecated since version 1.1.3 and will be removed in 2.0, it is replace by ContentRepository::countByContentTypeAndSiteInLastVersion method. `#1825 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1825>`_ (*alavieille*)
- **[open-orchestra-model-bundle]** `ContentRepository::countByContentTypeInLastVersionWithFilter` method is deprecated since version 1.1.3 and will be removed in 1.3.0, it is replace by `ContentRepository::countByContentTypeAndSiteInLastVersionWithFilter` method. `#613 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/613>`_ (*itkg-canne*)
- **[open-orchestra-model-bundle]** `ContentRepository::countByContentTypeInLastVersion` method is deprecated since version 1.1.3 and will be removed in 1.3.0, it is replace by `ContentRepository::countByContentTypeAndSiteInLastVersion` method. `#613 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/613>`_ (*itkg-canne*)
- **[open-orchestra-model-interface]** ContentRepositoryInterface::countByContentTypeInLastVersion method is deprecated since version 1.1.3 and will be removed in 2.0, it is replace by ContentRepository::countByContentTypeAndSiteInLastVersion method. `#212 <https://github.com/open-orchestra/open-orchestra-model-interface/pull/212>`_ (*alavieille*)

Other changes
-------------

- **[open-orchestra-cms-bundle]** optimize route generation on node update `#1819 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1819>`_ (*itkg-nanne*)

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v1.1.2...v1.1.3
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v1.1.2...v1.1.3
.. _`BBCode bundle`: https://github.com/open-orchestra/open-orchestra-bbcode-bundle/compare/v1.1.2...v1.1.3
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v1.1.2...v1.1.3
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v1.1.2...v1.1.3
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v1.1.2...v1.1.3
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v1.1.2...v1.1.3
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v1.1.2...v1.1.3
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/v1.1.2...v1.1.3
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v1.1.2...v1.1.3
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v1.1.2...v1.1.3
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v1.1.2...v1.1.3
.. _`Workflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v1.1.2...v1.1.3
.. _`Media admin bundle`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/compare/v1.1.2...v1.1.3
.. _`Orchestra libs`: https://github.com/open-orchestra/open-orchestra-libs/compare/v1.1.2...v1.1.3
.. _`Orchestra Mongo libs`: https://github.com/open-orchestra/open-orchestra-mongo-libs/compare/v1.1.2...v1.1.3
.. _`Media file bundle`: https://github.com/open-orchestra/open-orchestra-media-file-bundle/compare/v1.1.2...v1.1.3
.. _`Elastica bundle`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/compare/v1.1.2...v1.1.3
