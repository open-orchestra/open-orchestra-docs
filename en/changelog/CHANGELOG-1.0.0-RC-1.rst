CHANGELOG for 1.0.0-RC-1
========================

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
- `Workflow function bundle`_

Possible BC breaker
-------------------

- ``open_orchestra_model.annotation_reader`` is renamed by ``open_orchestra.annotation_reader``
- ``open_orchestra_base.annotation_search_reader`` is moved to orchestra-libs and renamed by ``open_orchestra.annotation_search_reader``
- Adding new bundle (OpenOrchestraMongoBundle)
- The parameter ``descriptionEntity`` in ``FinderConfiguration`` is now composed of array (``Array("key" => "", "field" => "", "type" => "")``
  futher information `documentation`_

Bug fixes
---------

- Search with hidden columns in dataTable

New features
------------

- You can describe the mapping for search in Yaml and XMl, `futher information in documentation`_
- A BBcode bundle is introduced to allow you to extend the rich text editor
- A new BBcode tag is available for media
- add new interface and command line to allow all, unit or functionnal tests loading

Other changes
-------------

- Mongo-odm requirement is updated to 1.0.1
- Remove MongoDBMigrationsBundle
- A refacto has been made to simplify the navigation
- Upgrade to mongo-odm 1.0.2, mongo-odm-bundle 3.0.1
- Acces Token no more revoked
- Upgrade to symfony 2.7.4
- Upgrade to twig/extensions 1.3.0
- Upgrade to symfony/assetic-bundle 2.7.0
- Upgrade to friendsofsymfony/http-cache-bundle 1.3.3
- Upgrade to phpunit/phpunit 4.8.8

Deprecated method
-----------------

Suppressed method
-----------------

Configuration changes
---------------------

 - The `LogBundle` has been split for the model, add the `ModelLogBundle` in the `AppKernel`

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.3.4...v1.0.0-RC1
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.3.4...v1.0.0-RC1
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.3.4...v1.0.0-RC1
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.3.4...v1.0.0-RC1
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.3.4...v1.0.0-RC1
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.3.4...v1.0.0-RC1
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v0.3.4...v1.0.0-RC1
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/v0.3.4...v1.0.0-RC1
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.3.4...v1.0.0-RC1
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.3.4...v1.0.0-RC1
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.3.4...v1.0.0-RC1
.. _`Workflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v0.3.4...v1.0.0-RC1
.. _`documentation`:../developer_guide/entity_list_ajax_pagination.html
.. _`futher information in documentation`:../developer_guide/entity_list_ajax_pagination.html
