CHANGELOG for 0.1.4
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
- The ContactController in the DisplayBundle has been removed. Therefore there are no more controller in
  this bundle so any reference to it in the routing file should be removed.
- We have moved the FieldAutoGenerableRepositoryInterface from the model-bundle to the model-interface

Bug fixes
---------
- Blocks contentList and configurable content displays the lastest content published in the language considered
- Fix pdf and video media preview

New features
------------
- BO Content Edit forms can now be personalized by Content Type

## Other changes
----------------
- Delete media with gaufrette
- I don't see header in the query string
- UserBundle is now required in FrontDemo
- Suppress cid in widget

Deprecated method
-----------------

Suppressed method
-----------------

Configuration changes
---------------------

- The controller reference under the `open_orchestra_display` key in the routing should not be used
  as there is no more controller in this bundle.

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.1.3...v0.1.4
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.1.3...v0.1.4
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.1.3...v0.1.4
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.1.3...v0.1.4
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.1.3...v0.1.4
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.1.3...v0.1.4
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.1.3...v0.1.4
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.1.3...v0.1.4
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.1.3...v0.1.4
