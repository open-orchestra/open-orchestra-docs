CHANGELOG for 0.2.1
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

New features
------------

Other changes
-------------

Deprecated method
-----------------

- The Statusable trait was in the model-bundle, it has been moved to model-interface
- We have moved the following classes from the ApiBundle, they are now deprecated and will be
  removed in the 0.2.2 version: 
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

Suppressed method
-----------------

- The class `OpenOrchestra\ApiBundle\Controller\BaseController` has been removed

Configuration changes
---------------------

- Activate the BaseApiBundle in the AppKernel: 

.. code-block:: php

   new OpenOrchestra\BaseApiBundle\OpenOrchestraBaseApiBundle(),

- There are now only relations on interfaces :

  - OpenOrchestra\ModelInterface\Model\EmbedStatusInterface: OpenOrchestra\ModelBundle\Document\EmbedStatus
  - OpenOrchestra\ModelInterface\Model\RoleInterface: OpenOrchestra\ModelBundle\Document\Role
  - OpenOrchestra\ModelInterface\Model\AreaInterface: OpenOrchestra\ModelBundle\Document\Area
  - OpenOrchestra\ModelInterface\Model\BlockInterface: OpenOrchestra\ModelBundle\Document\Block
  - OpenOrchestra\ModelInterface\Model\StatusInterface: OpenOrchestra\ModelBundle\Document\Status
  - OpenOrchestra\ModelInterface\Model\ThemeInterface: OpenOrchestra\ModelBundle\Document\Theme
  - OpenOrchestra\ModelInterface\Model\SiteAliasInterface: OpenOrchestra\ModelBundle\Document\SiteAlias
  - OpenOrchestra\ModelInterface\Model\ContentAttributeInterface: OpenOrchestra\ModelBundle\Document\ContentAttribute
  - OpenOrchestra\ModelInterface\Model\FieldTypeInterface: OpenOrchestra\ModelBundle\Document\FieldType
  - OpenOrchestra\ModelInterface\Model\FieldOptionInterface: OpenOrchestra\ModelBundle\Document\FieldOption

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.2.0...v0.2.1
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.2.0...v0.2.1
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.2.0...v0.2.1
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.2.0...v0.2.1
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.2.0...v0.2.1
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.2.0...v0.2.1
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.2.0...v0.2.1
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.2.0...v0.2.1
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.2.0...v0.2.1
