CHANGELOG for 0.3.0
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

- Add four methods in ``ContentRepositoryInterface`` :
  - ``getDefaultListable()``
  - ``addDefaultListable($name, $value)``
  - ``removeDefaultListable($name)``
  - ``setDefaultListable(array $defaultListable)``

Bug fixes
---------

New features
------------

- Possibility to hide the default columns in the dataTable
- Content attributes from other format than string can be display on datatable thanks to transformer

Other changes
-------------

- site 1 (front site) is removed of fixtures

Deprecated method
-----------------

Suppressed method
-----------------

- ``AddLinearize`` method and ``linearize`` attribute from ``ContentFacade`` are removed

Configuration changes
---------------------

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.2.12...v0.3.0
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.2.12...v0.3.0
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.2.12...v0.3.0
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.2.12...v0.3.0
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.2.12...v0.3.0
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.2.12...v0.3.0
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v0.2.12...v0.3.0
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.2.12...v0.3.0
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.2.12...v0.3.0
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.2.12...v0.3.0
.. _`Worflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v0.2.12...v0.3.0
