CHANGELOG for 1.0.0-RC2
=======================

Url to see changes:

- `Cms bundle`_
- `Display bundle`_
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

Possible BC breaker
-------------------

- In ``NodeManager``, parameter ``siteRepository`` must implement ``ReadSiteRepositoryInterface``
- In ``LanguageListStrategy``, parameter ``siteRepository`` must implement ``ReadSiteRepositoryInterface``
- In ``KernelExceptionSubscriber``, parameter ``siteRepository`` must implement ``ReadSiteRepositoryInterface``
- In ``DatabaseRouteLoader``, parameter ``siteRepository`` must implement ``ReadSiteRepositoryInterface``
- In ``RedirectionLoader``, parameter ``siteRepository`` must implement  ``ReadSiteRepositoryInterface``

Bug fixes
---------

New features
------------

- SaveMediaManager can upload multiple files

Other changes
-------------

- ``SiteRepositoryInterface`` is split in ``SiteRepositoryInterface`` and ``ReadSiteRepositoryInterface``
- The Back Office navigation pannel mechanism has been refactored to allow the creation of level 1 strategies

Deprecated method
-----------------

Suppressed method
-----------------

Configuration changes
---------------------

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v1.0.0-RC1...v1.0.0-RC2
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v1.0.0-RC1...v1.0.0-RC2
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v1.0.0-RC1...v1.0.0-RC2
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v1.0.0-RC1...v1.0.0-RC2
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v1.0.0-RC1...v1.0.0-RC2
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v1.0.0-RC1...v1.0.0-RC2
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v1.0.0-RC1...v1.0.0-RC2
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/v1.0.0-RC1...v1.0.0-RC2
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v1.0.0-RC1...v1.0.0-RC2
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v1.0.0-RC1...v1.0.0-RC2
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v1.0.0-RC1...v1.0.0-RC2
.. _`Worflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v1.0.0-RC1...v1.0.0-RC2
