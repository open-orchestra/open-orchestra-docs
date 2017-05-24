CHANGELOG for 0.2.0
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

- Creation of UserAdminBundle
- Creation of MediaAdminBundle

Bug fixes
---------

- Car content type fixtures are functionnal
- AccessToken was linked to the `User` document, it is now linked to the `UserInterface`
- AccessToken was linked to the `ApiClient` document, it is now linked to the `ApiClientInterface`
- Content type with content field which have not options are functionnal

New features
------------

- Possibility of using fullname (bundle:controller:twig) for underscore template in coffee
- Application developpers can now add new custom content attributes

Other changes
-------------

- Content Type List block now have a generic template
- In the back office / mediatheque, the media format tab is shown only for images, not for pdfs or videos
- In the creation of a site form, by default the index parameter and the follow parameter are checked
- Content Type have no status

Deprecated method
-----------------

- In the contentRepositoryInterface, the method findAllNews is deprecated and will be suppressed in 0.2.1
- In the contentTypeRepositoryInterface, the method findOneByContentTypeIdAndVersion is deprecated and will be suppressed in 0.2.1

Suppressed method
-----------------

Configuration changes
---------------------

- Activate new bundles for the backoffice:
  - `new OpenOrchestra\UserAdminBundle\OpenOrchestraUserAdminBundle(),`
  - `new OpenOrchestra\MediaAdminBundle\OpenOrchestraMediaAdminBundle(),`
- Load the routing for those bundles

.. code-block:: yaml

    open_orchestra_user_admin:
        resource: "@OpenOrchestraUserAdminBundle/Controller/Admin"
        type: annotation
        prefix: /admin

    open_orchestra_media_admin:
        resource: "@OpenOrchestraMediaAdminBundle/Controller/Admin"
        type: annotation
        prefix: /admin

    open_orchestra_user_api:
        resource: "@OpenOrchestraUserAdminBundle/Controller/Api"
        type: annotation
        prefix: /api

    open_orchestra_media_api:
        resource: "@OpenOrchestraMediaAdminBundle/Controller/Api"
        type: annotation
        prefix: /api

- Do not use the UserBundle routes
- Add the relation to the `UserInterface` :
  - `Symfony\Component\Security\Core\User\UserInterface: OpenOrchestra\UserBundle\Document\User`
- Add the relation to the `ApiClientInterface` :
  - `OpenOrchestra\UserBundle\Model\ApiClientInterface: OpenOrchestra\UserBundle\Document\ApiClient`
- We use a new bundle to use aggregation query with mongodb, activate the bundle :
  - `new Solution\MongoAggregationBundle\SolutionMongoAggregationBundle(),`

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.1.4...v0.2.0
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.1.4...v0.2.0
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.1.4...v0.2.0
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.1.4...v0.2.0
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.1.4...v0.2.0
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.1.4...v0.2.0
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.1.4...v0.2.0
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.1.4...v0.2.0
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.1.4...v0.2.0
