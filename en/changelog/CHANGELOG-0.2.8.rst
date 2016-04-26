CHANGELOG for 0.2.8
===================

Url to see changes:

- `Cms bundle`_
- `Display bundle`_
- `Model bundle`_
- `Model interface`_
- `Front bundle`_
- `Base bundle`_
- `Base api bundle`_
- `Media bundle`_
- `User bundle`_
- `Theme bundle`_
- `Worflow function bundle`_

Possible BC breaker
-------------------

- Facade which list entities for the DataTable require two additional attributes (recordsTotal and recordsFiltered), recordsTotal
  is total record without filtering and recordsFiltered record after filtering (search).
- The provisioning has been modified, you can now add multiple port for apache and make varnish dispatch the connection between them

Bug fixes
---------

New features
------------

Other changes
-------------

- Gruntfile rewrote to allow developpers to add specific concat tasks in their application
- DataTable use pagination, search and order with Ajax

Deprecated method
-----------------

Suppressed method
-----------------

Configuration changes
---------------------

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.2.7...v0.2.8
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.2.7...v0.2.8
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.2.7...v0.2.8
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.2.7...v0.2.8
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.2.7...v0.2.8
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.2.7...v0.2.8
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v0.2.7...v0.2.8
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.2.7...v0.2.8
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.2.7...v0.2.8
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.2.7...v0.2.8
.. _`Worflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v0.2.7...v0.2.8
