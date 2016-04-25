CHANGELOG for 0.0.7
===================

Url to see changes:

- `Cms bundle`_
- `Display bundle`_
- `Model bundle`_
- `Model interface`_
- `Front bundle`_
- `Base bundle`_
- `Media bundle`_
- `User bundle`_
- `Theme bundle`_

Possible BC breaker
-------------------

Bug fixes
---------

- Sitemap Generation is operationnal again
- Provisionning fixed
- Keywords are now selectables in form that require it
- Change the block form generation

New features
------------

- Redirection are stored in the database to feed the front router
- Ability to define a template to display a content
- Scheme of sites and pages is now configurable (used only on BO preview for now)

Other changes
-------------

- Back Office > Open sans font familly is now loaded via Bower
- Back Office > In node edition, only allowed blocks for the current site are availables
- Back Office > Mediatheque: thumbnail formats are exploited a new way
- Back Office > Mediatheque: contribution interface is a bit more friendly user
- Back Office > Logs: Add current site name in logs
- Back Office > MediathEque: Remove media preview
- Update to symfony 2.6.4

Deprecated method
-----------------

 - NodeRepositoryInterface::findOneByParendIdAndRoutePatternAndSiteId()
 - PhpOrchestraUrlGenerator::dynamicGenerate()
 - DynamicRoutingManager::getRouteParameterFromRequestPathInfo()
 - DynamicRoutingSubscriber::onKernelException()

Suppressed method
-----------------

 - NodeInterface::getAlias()
 - NodeInterface::setAlias()
 - NodeRepositoryInterface::findOneByParendIdAndAliasAndSiteId()

.. _`Cms bundle`: https://github.com/open-orchestra/phporchestra-cms-bundle/compare/v0.0.6...v0.0.7
.. _`Display bundle`: https://github.com/open-orchestra/phporchestra-display-bundle/compare/v0.0.6...v0.0.7
.. _`Model bundle`: https://github.com/open-orchestra/phporchestra-model-bundle/compare/v0.0.6...v0.0.7
.. _`Model interface`: https://github.com/open-orchestra/phporchestra-model-interface/compare/v0.0.6...v0.0.7
.. _`Front bundle`: https://github.com/open-orchestra/phporchestra-front-bundle/compare/v0.0.6...v0.0.7
.. _`Base bundle`: https://github.com/open-orchestra/phporchestra-base-bundle/compare/v0.0.6...v0.0.7
.. _`Media bundle`: https://github.com/open-orchestra/phporchestra-media-bundle/compare/v0.0.6...v0.0.7
.. _`User bundle`: https://github.com/open-orchestra/phporchestra-user-bundle/compare/v0.0.6...v0.0.7
.. _`Theme bundle`: https://github.com/open-orchestra/phporchestra-theme-bundle/compare/v0.0.6...v0.0.7
