CHANGELOG for 1.1.0-alpha1
==========================

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

Bug fixes
---------

- Each time you update a site, the routes in the database related to this site are updated
- Sorts by attributes in content and content type view are fully functional

New features
------------

- It is now possible to configure the Back Office dashboard and to create new widgets for it.
- Routes stored in the database are now linked to the last published version of a node
- You can now add the author, last contributor and contribution date in the content listing
- 2 new events are availables in the block rendering process: PRE_BLOCK_CREATION and POST_BLOCK_CREATION
- It is now possible to filter a column which contains a type `date` in dataTable
- Transverse block are now created on all transverse nodes
- When you add a language to a website, the transverse node is created with all the transverse blocks

Other changes
-------------

- Bundles are now using the PSR-4 syntax to be loaded, you should update the `Gruntfile` to follow this path modification

Deprecated method
-----------------

- Some method from the `NodeRepositoryInterface` and `ContentRepositoryInterface` `have been deprecated`_
- The method `findByNodeType` has been deprecated

Suppressed method
-----------------

Configuration changes
---------------------

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v1.0.0...v1.1.0-alpha1
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v1.0.0...v1.1.0-alpha1
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v1.0.0...v1.1.0-alpha1
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v1.0.0...v1.1.0-alpha1
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v1.0.0...v1.1.0-alpha1
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v1.0.0...v1.1.0-alpha1
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v1.0.0...v1.1.0-alpha1
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/v1.0.0...v1.1.0-alpha1
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v1.0.0...v1.1.0-alpha1
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v1.0.0...v1.1.0-alpha1
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v1.0.0...v1.1.0-alpha1
.. _`Worflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v1.0.0...v1.1.0-alpha1
.. _`have been deprecated`: https://github.com/open-orchestra/open-orchestra-model-interface/pull/119
