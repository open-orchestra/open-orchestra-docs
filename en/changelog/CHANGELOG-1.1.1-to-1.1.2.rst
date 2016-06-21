CHANGELOG from 1.1.1 to 1.1.2
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

- **[open-orchestra-cms-bundle]** Fix the display of active tab of translated value form `#1770 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1770>`_ (*djamnazi*)
- **[open-orchestra-cms-bundle]** Fix merge form block strategy with transformer and subscriber `#1768 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1768>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix data normalization when submitting a content form `#1767 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1767>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix popin error when click on button duplicate version `#1766 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1766>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Remove override default value of choice in javascript `#1765 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1765>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix exception on node role list update in group when node contains deleted `#1754 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1754>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Disallow creation of node in a language belonging fronts languages but not current site aliases languages `#1752 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1752>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Fix areas order on local storage decache `#1747 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1747>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Use the site binded to the group when setting a node role instead of the currently selected site `#1738 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1738>`_ (*ngilain*)
- **[open-orchestra-cms-bundle]** Clear the node per node rights when changing the binding between a group and a site `#1737 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1737>`_ (*ngilain*)
- **[open-orchestra-cms-bundle]** Fix some broken input `#1723 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1723>`_ (*ngilain*)
- **[open-orchestra-cms-bundle]** Fix wrong translation on workflow rights in group administration `#1722 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1722>`_ (*ngilain*)
- **[open-orchestra-cms-bundle]** a block only used in a single place can now be moved into another area without being deleted `#1717 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1717>`_ (*ngilain*)
- **[open-orchestra-cms-bundle]** hide add button if user d'ont have create content role `#1716 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1716>`_ (*djamnazi*)
- **[open-orchestra-cms-bundle]** Fix deactivate and re activate tinymce `#1708 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1708>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Fix duplicate model group role when update on model group role `#1704 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1704>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix IE9 padding of area in node and contribution in empty area `#1702 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1702>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** On the node edition page, the node is no more reloaded when clicking on the currently selected language tab `#1697 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1697>`_ (*ngilain*)
- **[open-orchestra-cms-bundle]** Fix submit and content type select `#1695 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1695>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Fix refresh and submit configurable content block form `#1693 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1693>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Throw an exception in UpdateNodeGroupRoleMoveNodeSubscriber if NodeGroupRole is not set `#1692 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1692>`_ (*ngilain*)
- **[open-orchestra-cms-bundle]** A form containing a required oo_content_search now correctly display an error message when trying to submit it without completing the oo_content_search `#1691 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1691>`_ (*ngilain*)
- **[open-orchestra-cms-bundle]** Fix Backoffice/Security/Authorization/Voter/NodeVersionVoter when create a new node `#1689 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1689>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix use contentId instead id in ContentSearchSubscriber `#1683 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1683>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix loop redirection when load template underscore without valid session `#1682 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1682>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix link with media in tinymce, replace tinymce plugin link by plugin orchestra_link `#1671 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1671>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** catch js error on form submission `#1670 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1670>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Fix french translations `#1666 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1666>`_ (*itkg-canne*)
- **[open-orchestra-display-bundle]** Fix display strategy configurable content with attribute contentSearch `#220 <https://github.com/open-orchestra/open-orchestra-display-bundle/pull/220>`_ (*alavieille*)
- **[open-orchestra-display-bundle]** Fix the Language List block when used in an error 404 page `#218 <https://github.com/open-orchestra/open-orchestra-display-bundle/pull/218>`_ (*ngilain*)
- **[open-orchestra-media-admin-bundle]** Fix alternative generation when original image ratio is extreme `#246 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/246>`_ (*ngilain*)
- **[open-orchestra-media-admin-bundle]** correct url for crop submit `#245 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/245>`_ (*itkg-nanne*)
- **[open-orchestra-media-admin-bundle]** fix no selected media on firefox `#235 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/235>`_ (*djamnazi*)
- **[open-orchestra-media-bundle]** custom styles are correctly used in displayMedia `#204 <https://github.com/open-orchestra/open-orchestra-media-bundle/pull/204>`_ (*Thiblef*)
- **[open-orchestra-media-bundle]** fix the document folder validator `#199 <https://github.com/open-orchestra/open-orchestra-media-bundle/pull/199>`_ (*djamnazi*)
- **[open-orchestra-model-bundle]** Fix the bad return type of SiteRepository::findByAliasDomain `#585 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/585>`_ (*ngilain*)
- **[open-orchestra-mongo-libs]** Fix requirement doctrine/mongodb-odm with php 5.5 `#36 <https://github.com/open-orchestra/open-orchestra-mongo-libs/pull/36>`_ (*alavieille*)
- **[open-orchestra-workflow-function-bundle]** Fix authorisation check when several Workflow profiles exist with the same transition `#117 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/117>`_ (*ngilain*)
- **[open-orchestra-front-bundle]** allow overriding logical name in route generating by using  route name `#170 <https://github.com/open-orchestra/open-orchestra-front-bundle/pull/170>`_ (*itkg-nanne*)

Possible BC breaker
-------------------

- **[open-orchestra-cms-bundle]** Constructor of class  ``Backoffice/EventSubscriber/BlockTypeSubscriber`` is changed `#1768 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1768>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Constructor of class ``Backoffice/Form/Type/BlockType`` is changed `#1768 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1768>`_ (*alavieille*)

New features
------------

- **[open-orchestra-model-bundle]** Add a NodeRepository::findOneByNodeAndSite method `#591 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/591>`_ (*ngilain*)

Other changes
-------------

- **[open-orchestra-workflow-function-bundle]** change some translation `#120 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/120>`_ (*itkg-nanne*)

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v1.1.1...v1.1.2
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v1.1.1...v1.1.2
.. _`BBCode bundle`: https://github.com/open-orchestra/open-orchestra-bbcode-bundle/compare/v1.1.1...v1.1.2
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v1.1.1...v1.1.2
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v1.1.1...v1.1.2
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v1.1.1...v1.1.2
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v1.1.1...v1.1.2
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v1.1.1...v1.1.2
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/v1.1.1...v1.1.2
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v1.1.1...v1.1.2
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v1.1.1...v1.1.2
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v1.1.1...v1.1.2
.. _`Workflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v1.1.1...v1.1.2
.. _`Media admin bundle`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/compare/v1.1.1...v1.1.2
.. _`Orchestra libs`: https://github.com/open-orchestra/open-orchestra-libs/compare/v1.1.1...v1.1.2
.. _`Orchestra Mongo libs`: https://github.com/open-orchestra/open-orchestra-mongo-libs/compare/v1.1.1...v1.1.2
.. _`Media file bundle`: https://github.com/open-orchestra/open-orchestra-media-file-bundle/compare/v1.1.1...v1.1.2
.. _`Elastica bundle`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/compare/v1.1.1...v1.1.2
