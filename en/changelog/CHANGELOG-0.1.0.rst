CHANGELOG for 0.1.0
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

- All bundles have been renamed

Bug fixes
---------

- Fix blocks Carrousel, youtube, search and addThis if id wasn't contributed
- Return ContentNotFoundEcxeption if there are no nodeId in the url for blockContent
- Fix Configurable Content block
- Modify Block list in siteType
- I can use radio button
- Templates can now be deleted

New features
------------

- You can access https pages in https only
- Multiple alias preview
- Merge dailymotion, youtube and vimeo blocks into video block
- sitemap.xml & robots.txt have their own rewrite rules
- New empty Dashboard to fix problem in certain circumstances
- WebSite id is now unique and you can't modify it
- You can define the template you want to display a content in the list

Other changes
-------------

- Add doc describing Front integration of blocks
- BO > Crop > Remove black borders on rectangle format
- Display save button on the modal footer if there is a delete button

Deprecated method
-----------------

Suppressed method
-----------------

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.0.7...v0.1.0
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.0.7...v0.1.0
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.0.7...v0.1.0
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.0.7...v0.1.0
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.0.7...v0.1.0
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.0.7...v0.1.0
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.0.7...v0.1.0
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.0.7...v0.1.0
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.0.7...v0.1.0
