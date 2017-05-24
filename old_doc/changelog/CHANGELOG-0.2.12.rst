CHANGELOG for 0.2.12
====================

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

- The parameters sent by the `dataTable are changed`_
- The namespace of trait `ListStatus` is now `OpenOrchestra\ApiBundle\Controller\ControllerTrait`
- In ``ContentRepositoryInterface`` :
  - ``findByContentTypeInLastVersionForPaginateAndSearch`` is deleted and replace by ``findByContentTypeAndSiteIdInLastVersionForPaginate``
  - ``findByContentTypeInLastVersionForPaginateAndSearchAndSiteId`` is deleted and replace by ``findByContentTypeInLastVersionForPaginateAndSearchAndSiteId``
  - ``countByContentTypeInLastVersionWithSearchFilter`` is deleted and replace by ``countByContentTypeInLastVersionWithFilter``
- In ``ApiClientRepositoryInterface`` :
  - ``findForPaginateAndSearch`` is deleted and replace by ``findForPaginate``
  - ``countWithSearchFilter`` is deleted and replace by ``countWithFilter``
- In ``WorkflowFunctionRepositoryInterface`` :
  - ``findForPaginateAndSearch`` is deleted and replace by ``findForPaginate``
  - ``countWithSearchFilter`` is deleted and replace by ``countWithFilter``
- In ``PaginateRepositoryInterface`` :
  - ``findForPaginateAndSearch`` is deleted and replace by ``findForPaginate``
  - ``countWithSearchFilter`` is deleted and replace by ``countWithFilter``
- In ``SiteRepositoryInterfaceInterface`` :
  - ``findByDeletedForPaginateAndSearch`` is deleted and replace by ``findByDeletedForPaginate``
  - ``countByDeletedWithSearchFilter`` is deleted and replace by ``countWithSearchFilterByDeleted``
  - ``PaginateAndSearchFilterTrait`` is deleted and replace by ``PaginationTrait``

Bug fixes
---------

- Node preview has been fixed, see configuration changes for more info

New features
------------

Other changes
-------------

Deprecated method
-----------------

- ``ModelBundle/Repository/AbstractRepository`` is deprecated will be removed in 0.3.0
- The trait ``TranslatedValueFilter`` is deprecated will be removed in 0.3.0
- In ``ContentRepositoryInterface`` :
  - ``countByDeletedInLastVersionWithSearchFilter`` replace by ``countNotDeletedInLastVersionWithSearchFilter``
- In ``ContentTypeRepositoryInterface`` :
  - ``findAllByDeletedInLastVersionForPaginateAndSearch`` replace by ``findAllNotDeletedInLastVersionForPaginate``
  - ``countByDeletedInLastVersionWithSearchFilter`` replace by ``countDeletedInLastVersionWithSearchFilter``
  - ``findAllByDeletedInLastVersion`` replace by ``findAllNotDeletedInLastVersion``
- In ``NodeRepositoryInterface`` :
  - ``findOneByNodeIdAndLanguageAndSiteIdAndLastVersion`` replace by ``findOneByNodeIdAndLanguageAndSiteIdInLastVersion``
  - ``findLastVersionByDeletedAndSiteId`` replace by ``findDeletedInLastVersionBySiteId``
  - ``findLastVersionByDeletedAndSiteId``  replace by ``findDeletedInLastVersionBySiteId``
  - ``findChildsByPathAndSiteIdAndLanguage`` replace by ``findChildrenByPathAndSiteIdAndLanguage``
  - ``findByParentIdAndRoutePatternAndNotNodeIdAndSiteId`` replace by ``findByParentIdAndRoutePatternAndNodeIdAndSiteId``
  - ``findOneByNodeIdAndLanguageAndVersionAndSiteId`` replace by ``findOneByNodeIdAndLanguageAndSiteIdAndVersion``
- In ``ReadNodeRepositoryInterface`` :
  - ``findOneByNodeIdAndLanguageWithPublishedAndLastVersionAndSiteId`` replace by ``findOnePublishedByNodeIdAndLanguageAndSiteIdInLastVersion``
- The `linearized_attributes` from the `ContentFacade` are not use anymore

Suppressed method
-----------------

- All the display block classes from the MediaBundle have been removed
- ``ModelInterface/Form/Type/AbstractOrchestraRoleType`` has been removed
- ``ModelInterface/MongoTrait/Versionnable`` has been removed. Replace by ``ModelInterface/MongoTrait/Versionable``
- In ``AreaInterface`` :
  - ``setClasses`` replace by ``setHtmlClass``
  - ``getClasses`` replace by ``getHtmlClass``
- In ``ReadAreaInterface`` : ``getClasses`` replace by ``getHtmlClass``
- In ``ContentTypeRepositoryInterface`` :
  - ``findOneByContentTypeIdAndVersion``
  - ``findOneByContentTypeIdAndVersionfrom``
- In ``ContentRepositoryInterface`` : ``findByContentTypeInLastVersion``
- In ``NodeRepositoryInterface`` : ``findOneByParendIdAndRoutePatternAndSiteId``

Configuration changes
---------------------

- In order to get the new routing conf, Back Office configuration requires to be updated. In app/config/routing.yml of your back application, add the following lines :


.. code-block:: yaml

    open_orchestra_base:
        resource: "@OpenOrchestraBaseBundle/Resources/config/routing.yml"

- The front configuration must also be updated. In app/config/routing.yml of your front application, add the following lines :


.. code-block:: yaml

    open_orchestra_front_preview:
        resource: "@OpenOrchestraFrontBundle/Resources/config/preview_routing.yml"

- A `MediaModelBundle` has been created to store the media document, you should activate the bundle :

.. code-block:: php

    new OpenOrchestra\MediaModelBundle\OpenOrchestraMediaModelBundle(),

- A `BaseApiModelBundle` has been created to store the BaseApi document, you should activate the bundle :


.. code-block:: php

    new OpenOrchestra\BaseApiModelBundle\OpenOrchestraBaseApiModelBundle(),

- A `WorkflowFunctionModelBundle` has been created to store the WorkflowFunction document, you should activate the bundle :

.. code-block:: php

    new OpenOrchestra\WorkflowFunctionModelBundle\OpenOrchestraWorkflowFunctionModelBundle(),

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.2.11...v0.2.12
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.2.11...v0.2.12
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.2.11...v0.2.12
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.2.11...v0.2.12
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.2.11...v0.2.12
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.2.11...v0.2.12
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v0.2.11...v0.2.12
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.2.11...v0.2.12
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.2.11...v0.2.12
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.2.11...v0.2.12
.. _`Worflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v0.2.11...v0.2.12
.. _`dataTable are changed`: ../developer_guide/entity_list_ajax_pagination.html
