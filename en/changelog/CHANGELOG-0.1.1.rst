CHANGELOG for 0.1.1
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

- Suppress dynamic routing maganement
- Strategies header, mediaList and Gallery have been moved

Bug fixes
---------

- Keywords field opened in a block form is now correctly closed when closing the form
- Media > crop on an image larger than screen now works correctly
- Preview link
- render_esi on blocks fixed when used with varnish
- Blocks Menu and SubMenu deal with dynamic node pattern
- BO > F5 on media edit now works
- Separation of DisplayBundle and MediaBundle

New features
------------

- Route pattern starting with "/" are absolute
- ReverseProxy cache: Open Orchestra now uses httpfoscachebundle
- Blocks can have specific tags used as cache keys
- Node cache has specific tags
- User are related to a group for the right
- Content preview is now handled by a fake object
- You can create users group
- User are now related to groups

Other changes
-------------

- Content can have a personal template
- BO > Mediatheque is redesigned and have a better interface
- Add test behat and provision it
- Provision a cron task
- Add an example of varnish usage
- Add an asterisk if field are required
- Add help for form fields
- DataGrid have bootstrap button
- Block can specify cache management properties
- Move the Group document into a new Group Bundle

Deprecated method
-----------------

Suppressed method
-----------------

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.1.0...v0.1.1
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.1.0...v0.1.1
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.1.0...v0.1.1
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.1.0...v0.1.1
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.1.0...v0.1.1
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.1.0...v0.1.1
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.1.0...v0.1.1
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.1.0...v0.1.1
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.1.0...v0.1.1
