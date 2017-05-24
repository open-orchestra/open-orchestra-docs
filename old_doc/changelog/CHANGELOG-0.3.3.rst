CHANGELOG for 0.3.3
===================

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

- The api authentication strategies should only return either a `FacadeInterface` or a `ConstraintViolationListInterface` object.
- The serialization of the result is done through the same subscriber every other api request
- Configuration files are rename to snake case. example : ``oauth2routing.yml`` become ``oauth2_routing.yml``
- The backbone router has been refactored to contain only the generation and route matching, every
  route should now be declared separetly
- The backbone view ``FullPagePanelView`` is removed replace by the generic view for tabs ``TabView`` and ``TabElementFormView``

Bug fixes
---------

New features
------------

- You can use the command `orchestra:mongo:fixtures:load` to load only the fixtures implementing the
  interface `OpenOrchestra\ModelInterface\DataFixtures\OrchestraProductionFixturesInterface`.
- You can filter the content attributes in the contents dataTable
- An Api client can now have some base role that will be merged with the user role
- Only last version of node and content can be change now.

Other changes
-------------

- Media use a new thumbnail format to display media

Deprecated method
-----------------

- The `PreventPublishedDocumentSave` has been replaced by the `AuthorizeEdition` constraint.

Suppressed method
-----------------

Configuration changes
---------------------

- Thumbnail configuration is always `max_width` and `max_height` and not `width` and `height` for rectangle
- `object_manager` is defined in ``open-orchestra-base-bundle`` and not in ``base-api-mongo-bundle``

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.3.2...v0.3.3
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.3.2...v0.3.3
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.3.2...v0.3.3
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.3.2...v0.3.3
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.3.2...v0.3.3
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.3.2...v0.3.3
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v0.3.2...v0.3.3
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/v0.3.2...v0.3.3
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.3.2...v0.3.3
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.3.2...v0.3.3
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.3.2...v0.3.3
.. _`Worflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v0.3.2...v0.3.3
