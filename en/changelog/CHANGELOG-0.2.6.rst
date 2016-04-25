CHANGELOG for 0.2.6
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

- Symfony version has been upgraded to 2.7.0

Bug fixes
---------

- Fix broken sitemaps generation

New features
------------

- added DataTable Colvis to Bower and Grunt to enable column choice visibility in dataTable
- added possibility to manage right on content and node change status
- new custom types options can be added in the app/config.yml

Other changes
-------------

- Refacto on the grunt tasks

Deprecated method
-----------------

- The method `eventElligible` from the `AbstractSubscriber` in the `BaseApi` is replaced by `isEventEligible`

Suppressed method
-----------------

Configuration changes
---------------------

The grunt tasks managment has been changed to be more user friendly in case of Open Orchestra updates
and/or application specific modifications. Tasks and configuration are now splitted into multiples
files placed in OpenOrchestraBundle for the generic ones and in CmsBundle for the specific ones. To
be compatible with that change, projects must update their actual grunt files. The gruntfile must be
updated. The folder grunt_tasks must be created and the tasks it's containing must be added. See 
`Pull request #492`_ for more information.

As new npm modules are required, a npm install must also be done.

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.2.5...v0.2.6
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.2.5...v0.2.6
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.2.5...v0.2.6
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.2.5...v0.2.6
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.2.5...v0.2.6
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.2.5...v0.2.6
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v0.2.5...v0.2.6
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.2.5...v0.2.6
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.2.5...v0.2.6
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.2.5...v0.2.6
.. _`Worflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v0.2.5...v0.2.6
.. _`Pull request #492`: https://github.com/open-orchestra/open-orchestra/pull/492
