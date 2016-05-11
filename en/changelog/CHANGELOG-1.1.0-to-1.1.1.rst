CHANGELOG from 1.1.0 to 1.1.1
=============================

Url to see changes:

- `Cms bundle`_
- `Display bundle`_
- `BBCode bundle`_
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
- `Media admin bundle`_
- `Orchestra libs`_
- `Orchestra Mongo libs`_
- `Media file bundle`_
- `Elastica bundle`_

Bug fixes
---------

- **[open-orchestra-cms-bundle]** Add boLabel on root node when create a new website `#1654 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1654>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix error index blocks when duplicate a node `#1648 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1648>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix the javascript error on datatable pagination `#1644 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1644>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** maximun version for nodejs is ~4.4.3 `#1641 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1641>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix dependency between BaseApi and ApiBundle, move TransformerParameterTypeException `#1631 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1631>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** fix tinymce issues in collection context `#1629 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1629>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Refresh page when saving a website form after a form error `#1627 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1627>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix block edition right management in global page `#1620 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1620>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Fix default field in content type form `#1616 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1616>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** use dependency injection for BlockToArrayTransformer in BlockType `#1615 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1615>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** replace opacity by display in area toolbar to deactivate involuntary click `#1614 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1614>`_ (*itkg-nanne*)
- **[open-orchestra-media-admin-bundle]** Media reference are set also in draft status and pending status of content and node `#227 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/227>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** Remove browse button if user doesn't have the access to the media management. `#219 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/219>`_ (*djamnazi*)
- **[open-orchestra-user-bundle]** Fix dependency between UserBundle and BackOfficeBundle `#103 <https://github.com/open-orchestra/open-orchestra-user-bundle/pull/103>`_ (*alavieille*)

New features
------------

- **[open-orchestra-cms-bundle]** hide error 403 on redirection after post in user context `#1650 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1650>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Update css style of componement tab view replace class nav-tabs by nav-pills nav-justified `#1628 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1628>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Add a method to find role for node only. `#1626 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1626>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Show node language and version language in title of edit form `#1622 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1622>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** remove image resize in tinyMce `#213 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/213>`_ (*itkg-nanne*)
- **[open-orchestra-media-bundle]** add css style to media bbcode `#192 <https://github.com/open-orchestra/open-orchestra-media-bundle/pull/192>`_ (*itkg-nanne*)
- **[open-orchestra-model-bundle]** Update route in database after site migration and site-alias update `#576 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/576>`_ (*itkg-nanne*)

Deprecated
----------

- **[open-orchestra-cms-bundle]** The ``OpenOrchestra\ApiBundle\Exceptions\TransformerParameterTypeException`` class is deprecated since version 1.2.0 and will be removed in 1.3.0, use ``OpenOrchestra\BaseApi\Exceptions\TransformerParameterTypeException`` `#1631 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1631>`_ (*alavieille*)

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v1.1.0...v1.1.1
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v1.1.0...v1.1.1
.. _`BBCode bundle`: https://github.com/open-orchestra/open-orchestra-bbcode-bundle/compare/v1.1.0...v1.1.1
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v1.1.0...v1.1.1
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v1.1.0...v1.1.1
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v1.1.0...v1.1.1
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v1.1.0...v1.1.1
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v1.1.0...v1.1.1
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/v1.1.0...v1.1.1
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v1.1.0...v1.1.1
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v1.1.0...v1.1.1
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v1.1.0...v1.1.1
.. _`Workflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v1.1.0...v1.1.1
.. _`Media admin bundle`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/compare/v1.1.0...v1.1.1
.. _`Orchestra libs`: https://github.com/open-orchestra/open-orchestra-libs/compare/v1.1.0...v1.1.1
.. _`Orchestra Mongo libs`: https://github.com/open-orchestra/open-orchestra-mongo-libs/compare/v1.1.0...v1.1.1
.. _`Media file bundle`: https://github.com/open-orchestra/open-orchestra-media-file-bundle/compare/v1.1.0...v1.1.1
.. _`Elastica bundle`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/compare/v1.1.0...v1.1.1
