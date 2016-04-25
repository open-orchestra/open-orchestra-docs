CHANGELOG for 0.2.9
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

- In ContentRepositoryInterface and FieldAutoGenerableRepositoryInterface the method testUnicityInContext is rename by testUniquenessInContext

Bug fixes
---------

- Content versions van be naviguated through and created
- Current site can be switched to a site created in the Back Office, not only in the fixtures
- Content type can be deleted
- The deleted contents are not visible in the list
- The media folder are now visible if they are not linked to a website
- The media folder can be editable
- In the content submission, the order in which the transformer are used has been changed (for the reverseTransformation)

New features
------------

- Wysiwyg blocks have a button to add image from Media Library to content
- A content can be linked to the current website
- Some properties and content attributes can be the always the same on all content

Other changes
-------------

- Method findLastPublishedVersionByContentIdAndLanguage of ContentRepositoryInterface is moved in ReadContentRepositoryInterface
- Remove all deprecated calls related to Symfony 2.7

Deprecated method
-----------------

Suppressed method
-----------------

Configuration changes
---------------------

- In the `ModelBundle` the class definition is under the `document` entry

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.2.8...v0.2.9
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.2.8...v0.2.9
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.2.8...v0.2.9
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.2.8...v0.2.9
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.2.8...v0.2.9
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.2.8...v0.2.9
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v0.2.8...v0.2.9
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.2.8...v0.2.9
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.2.8...v0.2.9
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.2.8...v0.2.9
.. _`Worflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v0.2.8...v0.2.9
