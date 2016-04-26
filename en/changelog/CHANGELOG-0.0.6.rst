CHANGELOG for 0.0.6
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

- Modify the way route are created and analyzed
- The website has multiple alias
- Each website alias can provide an url prefix

Bug fixes
---------

- BO left menu is now operationnal after an automatic refresh
- The crop preview is now disable

New features
------------

- Validation on the routePattern creation
- Display the site name in the log table
- Start to use Wreqr to dispatch event in Js

Other changes
-------------

- Apc is not anymore required by baseBundle

Deprecated method
-----------------

- NodeRepositoryInterface: findOneByParendIdAndAliasAndSiteId

.. _`Cms bundle`: https://github.com/open-orchestra/phporchestra-cms-bundle/compare/v0.0.5...v0.0.6
.. _`Display bundle`: https://github.com/open-orchestra/phporchestra-display-bundle/compare/v0.0.5...v0.0.6
.. _`Model bundle`: https://github.com/open-orchestra/phporchestra-model-bundle/compare/v0.0.5...v0.0.6
.. _`Model interface`: https://github.com/open-orchestra/phporchestra-model-interface/compare/v0.0.5...v0.0.6
.. _`Front bundle`: https://github.com/open-orchestra/phporchestra-front-bundle/compare/v0.0.5...v0.0.6
.. _`Base bundle`: https://github.com/open-orchestra/phporchestra-base-bundle/compare/v0.0.5...v0.0.6
.. _`Media bundle`: https://github.com/open-orchestra/phporchestra-media-bundle/compare/v0.0.5...v0.0.6
.. _`User bundle`: https://github.com/open-orchestra/phporchestra-user-bundle/compare/v0.0.5...v0.0.6
.. _`Theme bundle`: https://github.com/open-orchestra/phporchestra-theme-bundle/compare/v0.0.5...v0.0.6
