CHANGELOG for 0.2.2
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

- The ApiBundle has been split in ApiBundle and BaseApiBundle

Bug fixes
---------

- Blocks js & css files are now correctly loaded
- Missing BO assets are fixed

New features
------------

- In the BackOffice, adding new form type (choice, hidden, money and date) for the contentType.
- Content type fields list can now be extended in app config
- The content type field definition has changed

Other changes
-------------

- In the BackOffice, we modified the way we interact with the blocks and area (js and css modification only). 
- In the Backoffice, all the display strategies should be tagged with `open_orchestra_backoffice.display_block.strategy`

Deprecated method
-----------------

- The `VersionnableInterface` and `Versionnable` trait have been renamed to `VersionableInterface` and
  `Versionable` respectively

Suppressed method
-----------------

- The following class have been removed from the ApiBundle : 
  - GroupContext
  - Annotation\Serializer
  - Annotation\Group
  - BaseController
  - TransformerManaer
  - AbstractTransformer
  - TransformerInterface
  - AbstractFacade
  - FacadeInterface
  - ApiException
  - HttpException\ApiException

Configuration changes
---------------------

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.2.1...v0.2.2
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.2.1...v0.2.2
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.2.1...v0.2.2
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.2.1...v0.2.2
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.2.1...v0.2.2
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.2.1...v0.2.2
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.2.1...v0.2.2
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.2.1...v0.2.2
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.2.1...v0.2.2
