CHANGELOG for 0.1.2
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

- All interfaces have been split into Interfaces and ReadInterfaces

Bug fixes
---------

- Status creation

New features
------------

- Concerned caches banned on Node/Content status changes
- Multi devices
- Blocks cache are tagged according their content
- Check twig syntax error in contents templates
- Add new specific tags to blocks
- Oauth2 authentication on the api
- Translate media's title and alt

Other changes
-------------

- Rename Editorial/template.html.twig into form.html.twig
- Move blocks constants into blocks strategies

Deprecated method
-----------------


Suppressed method
-----------------

Configuration modification
--------------------------

- The interface split modify the `resolve_target_documents`, you need to put the new read interfaces instead
- `Change the firewall configuration`_ for the api connexion

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.1.1...v0.1.2
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.1.1...v0.1.2
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.1.1...v0.1.2
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.1.1...v0.1.2
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.1.1...v0.1.2
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.1.1...v0.1.2
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.1.1...v0.1.2
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.1.1...v0.1.2
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.1.1...v0.1.2
.. _`Change the firewall configuration`:https://github.com/open-orchestra/open-orchestra/blob/master/app/Resources/doc/dev/draft/apiConnexion.md
