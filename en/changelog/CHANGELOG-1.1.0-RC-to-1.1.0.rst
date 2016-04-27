CHANGELOG from 1.1.0-RC to 1.1.0
================================

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

New features
------------

- **[open-orchestra]** updating fixtures console command to allow user choose the type of fixtures to load and add a dev environment `#888 <https://github.com/open-orchestra/open-orchestra/pull/888>`_ (*djamnazi*)
- **[open-orchestra-base-bundle]** Update requirement ``symfony/symfony`` to ``~2.8.4`` `#81 <https://github.com/open-orchestra/open-orchestra-base-bundle/pull/81>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** It is no longer possible to delete a block of global page if it is used `#1599 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1599>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Adding attribute ``boLabel`` on Node , used to generate tree in the Back Office `#1586 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1586>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Remove delete button on edit modal view and deplace it #near edit button `#1581 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1581>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** Remove choice groups  in edit user if the user is super admin `#1572 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1572>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Remove role super admin of user admin in production fixture `#1572 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1572>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Remove edit button for tranverse page `#1569 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1569>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** When a content is deleted or his status is updated tag ``'contentId-' . $contentId`` is invalidate. `#1568 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1568>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** When a content type is deleted or updated tag ``''contentType-' . $contentType`` is invalidate. `#1568 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1568>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** ``openOrchestra\Backoffice\Form\Type\ComponentRoleChoiceType`` can display roles of multiple role collector `#1567 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1567>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** In navigation panel, The global page is directly accessible. `#1561 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1561>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Add modification date for versions into global page and node. `#1559 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1559>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** Remove full screen for jarvis widget `#1558 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1558>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** The role parameter to create an navigation strategy is no longer required `#1556 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1556>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Adding voter to forbid removing node root `#1555 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1555>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Add role ``acess``, ``update``, ``create`` for error nodes. `#1549 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1549>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** add content search widget in configurable content block `#1548 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1548>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Move actions buttons to the ribbon `#1545 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1545>`_ (*djamnazi*)
- **[open-orchestra-cms-bundle]** test on mandatory main alias in site form `#1542 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1542>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Remove permanently a entity in trash can `#1539 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1539>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** enhance area form in template, node and area `#1537 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1537>`_ (*itkg-nanne*)
- **[open-orchestra-elastica-bundle]** When a content is deleted, it's removed to elastica index `#25 <https://github.com/open-orchestra/open-orchestra-elastica-bundle/pull/25>`_ (*alavieille*)
- **[open-orchestra-elastica-bundle]** When a content is restored, it's added to elastica index `#25 <https://github.com/open-orchestra/open-orchestra-elastica-bundle/pull/25>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** Message in form ``oo_media_choice`` when no image is selected is translated `#202 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/202>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** A root folder is created when a new website is created `#190 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/190>`_ (*alavieille*)
- **[open-orchestra-media-bundle]** Add default strategy to display media `#183 <https://github.com/open-orchestra/open-orchestra-media-bundle/pull/183>`_ (*alavieille*)
- **[open-orchestra-media-file-bundle]** Add expires attribute into the header of HTTP request. `#14 <https://github.com/open-orchestra/open-orchestra-media-file-bundle/pull/14>`_ (*KevinArtus*)
- **[open-orchestra-model-bundle]**  Add script migration to rename role  ROLE_ACCESS_MOVE_NODE by ROLE_ACCESS_MOVE_TREE `#563 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/563>`_ (*alavieille*)
- **[open-orchestra-model-bundle]** Add migration for attribute ``boLabel`` `#561 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/561>`_ (*alavieille*)
- **[open-orchestra-model-bundle]** Create HomePage by load fixtures `#549 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/549>`_ (*djamnazi*)
- **[open-orchestra-workflow-function-bundle]** Remove link right form in edit user if the user is super admin `#99 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/99>`_ (*alavieille*)
- **[open-orchestra-workflow-function-bundle]** Add voter to check workflow state of statusable document `#97 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/97>`_ (*alavieille*)

Possible BC breaker
-------------------

- **[open-orchestra-cms-bundle]** ``OpenOrchestra\GroupBundle\EventListener\AbstractNodeGroupRoleListener`` is replaced by ``OpenOrchestra\GroupBundle\EventSubscriber\AbstractNodeGroupRoleSubscriber`` `#1582 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1582>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** ``OpenOrchestra\GroupBundle\EventListener\AddNodeGroupRoleForGroupListener`` is replaced by ``OpenOrchestra\GroupBundle\EventSubscriber\NodeGroupRoleForGroupSubscriber`` `#1582 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1582>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** ``OpenOrchestra\GroupBundle\EventListener\AddNodeGroupRoleForNodeListener`` is replaced by ``OpenOrchestra\GroupBundle\EventSubscriber\NodeGroupRoleForNodeSubscriber`` `#1582 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1582>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Deleted PageConfigurationButtonView.coffee `#1581 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1581>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** `` OpenOrchestra\UserAdminBundle\Event\UserFacadeEvent`` take a new argument `user` which is the user transformed `#1572 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1572>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** ``openOrchestra\Backoffice\Form\Type\ComponentRoleChoiceType`` take an array of role collector in parameter. `#1567 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1567>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** ``OpenOrchestra\Backoffice\NavigationPanel\Strategies\GeneralNodesPanelStrategy`` is renamed by ``OpenOrchestra\Backoffice\NavigationPanel\Strategies\TransverseNodePanelStrategy`` `#1561 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1561>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** The class ``OpenOrchestra\Backoffice\NavigationPanel\Strategies\AbstractNavigationPanelStrategy`` is deprecated and will be removed in 1.2.0 use ``OpenOrchestra\Backoffice\NavigationPanel\Strategies\AbstractNavigationStrategy`` `#1556 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1556>`_ (*alavieille*)
- **[open-orchestra-media-bundle]** Twig of method displayMedia in all display strategy are moved of ``OpenOrchestraMediaBundle:BBcode/FullDisplay`` to ``OpenOrchestraMediaBundle:DisplayMedia/FullDisplay`` `#183 <https://github.com/open-orchestra/open-orchestra-media-bundle/pull/183>`_ (*alavieille*)
- **[open-orchestra-model-bundle]** The `TrashItem` document has a new property `type` `#541 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/541>`_ (*alavieille*)
- **[open-orchestra-model-interface]** The `TrashItemInterface` has a new property `type` `#172 <https://github.com/open-orchestra/open-orchestra-model-interface/pull/172>`_ (*alavieille*)
- **[open-orchestra-model-interface]** The `TrashItemRepositoryInterface` has a new method `findByEntity($entityId)` `#172 <https://github.com/open-orchestra/open-orchestra-model-interface/pull/172>`_ (*alavieille*)

Bug fixes
---------

- **[open-orchestra-base-api-bundle]** Fix position of property `validationGroups` in method `isValid` of `BaseApiBundle/Controller/BaseController` `#76 <https://github.com/open-orchestra/open-orchestra-base-api-bundle/pull/76>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix error on field default value if field type is changed in content type form `#1602 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1602>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** When you save multiple tinymce, there are saved correctly `#1601 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1601>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** create user with media folder access and create role for functional test `#1595 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1595>`_ (*djamnazi*)
- **[open-orchestra-cms-bundle]** Fix access denied when edit node without ``role_access_site`` `#1593 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1593>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix error access denied when select an other version node `#1592 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1592>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Refresh node view when edit form of node  is submitted `#1591 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1591>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix bug updating status of node with the update role of node of other type `#1590 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1590>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** add constraints for email user unicity `#1587 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1587>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** Add label option into group FormType `#1585 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1585>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** Activate subform content search in content type form context `#1583 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1583>`_ (*itkg-nanne*)
- **[open-orchestra-cms-bundle]** When a group is updated model group roles are correctly set `#1582 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1582>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Add constraint Unique on group `#1565 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1565>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix transform correctly a type double in a string value. `#1564 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1564>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Remove cursor move of dashboard widgets `#1563 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1563>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Fix transform area from another site as the current site `#1544 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1544>`_ (*alavieille*)
- **[open-orchestra-cms-bundle]** Unused blocks are now definitivly suppressed from DB when deleted from a node and used no more `#1540 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1540>`_ (*itkg-ngilain*)
- **[open-orchestra-display-bundle]** set shared max age if ESI cash is supported `#209 <https://github.com/open-orchestra/open-orchestra-display-bundle/pull/209>`_ (*djamnazi*)
- **[open-orchestra-elastica-bundle]** Fix error type of property ``updateAt`` in content type schema `#24 <https://github.com/open-orchestra/open-orchestra-elastica-bundle/pull/24>`_ (*alavieille*)
- **[open-orchestra-front-bundle]** Fix generate url command site map generate `#158 <https://github.com/open-orchestra/open-orchestra-front-bundle/pull/158>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** fix folder update error when user don't has the update role `#208 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/208>`_ (*djamnazi*)
- **[open-orchestra-media-admin-bundle]** In a content, the selection of a media with no alternative is now correctly stored `#207 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/207>`_ (*itkg-ngilain*)
- **[open-orchestra-media-admin-bundle]** Rename descriptions for roles media and folders. `#206 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/206>`_ (*KevinArtus*)
- **[open-orchestra-media-admin-bundle]** hide edit button if user don't have update role in media folder `#204 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/204>`_ (*djamnazi*)
- **[open-orchestra-media-admin-bundle]** If an user hasn't role ``ROLE_ACCESS_UPDATE_MEDIA``, he can't edit a media `#201 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/201>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** A required oo_media_choice form type is now correctly handled `#195 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/195>`_ (*itkg-ngilain*)
- **[open-orchestra-media-admin-bundle]** Remove link constraint on media display block `#194 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/194>`_ (*itkg-ngilain*)
- **[open-orchestra-model-bundle]** Re-activate site search by alias domain `#560 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/560>`_ (*itkg-nanne*)
- **[open-orchestra-model-bundle]** use currentlyPublished tag to display menu and footer `#546 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/546>`_ (*itkg-nanne*)
- **[open-orchestra-model-bundle]** method ``hasOtherNodeWithSameParentAndOrder```of ``NodeRepository`` check only on default nodes `#545 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/545>`_ (*alavieille*)
- **[open-orchestra-model-bundle]** method ``testUniquenessInContext`` is now based on ``nodeId`` and not ``name`` `#543 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/543>`_ (*alavieille*)
- **[open-orchestra-model-bundle]** Demo fixtures are updated to present block usage references `#542 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/542>`_ (*itkg-ngilain*)
- **[open-orchestra-model-bundle]** Path on node is updated only if node isn't deleted `#541 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/541>`_ (*alavieille*)
- **[open-orchestra-model-interface]** Fix type ``nodeId`` in php doc of ``NodeInterface`` and ``ReadNodeInterface`` `#176 <https://github.com/open-orchestra/open-orchestra-model-interface/pull/176>`_ (*alavieille*)

Other changes
-------------

- **[open-orchestra-cms-bundle]** Corrected translation. `#1600 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1600>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** Rename navigation menu status and Role `#1589 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1589>`_ (*KevinArtus*)
- **[open-orchestra-cms-bundle]** Hide addpage button if no root page `#1560 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1560>`_ (*djamnazi*)
- **[open-orchestra-front-bundle]** Get master request in method where it is used and not in a constructor `#150 <https://github.com/open-orchestra/open-orchestra-front-bundle/pull/150>`_ (*alavieille*)
- **[open-orchestra-media-admin-bundle]** Migration scripts to explain in the changelog (main configuration changes + migration configuration) `#200 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/200>`_ (*itkg-ngilain*)
- **[open-orchestra-media-admin-bundle]** Remove MediaInterface::MEDIA_PREFIX `#198 <https://github.com/open-orchestra/open-orchestra-media-admin-bundle/pull/198>`_ (*itkg-ngilain*)
- **[open-orchestra-model-bundle]** Remove "published to draft' role for production fixtures. `#548 <https://github.com/open-orchestra/open-orchestra-model-bundle/pull/548>`_ (*KevinArtus*)
- **[open-orchestra-workflow-function-bundle]** corrected translations. `#104 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/104>`_ (*KevinArtus*)
- **[open-orchestra-workflow-function-bundle]** Rename navigation menu workflow `#102 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/102>`_ (*KevinArtus*)
- **[open-orchestra-workflow-function-bundle]** Remove "published to draft' role for validator on fixtures. `#95 <https://github.com/open-orchestra/open-orchestra-workflow-function-bundle/pull/95>`_ (*KevinArtus*)

Deprecated
----------

- **[open-orchestra-cms-bundle]** class ``OpenOrchestra\Backoffice\EventSubscriber\ChangeContentStatusSubscriber`` s deprecated in 1.1.0 and will be removed in 1.2.0, it is replace by ContentUpdateCacheSubscriber `#1568 <https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1568>`_ (*alavieille*)

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v1.1.0-RC...v1.1.0
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v1.1.0-RC...v1.1.0
.. _`BBCode bundle`: https://github.com/open-orchestra/open-orchestra-bbcode-bundle/compare/v1.1.0-RC...v1.1.0
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v1.1.0-RC...v1.1.0
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v1.1.0-RC...v1.1.0
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v1.1.0-RC...v1.1.0
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v1.1.0-RC...v1.1.0
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v1.1.0-RC...v1.1.0
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/v1.1.0-RC...v1.1.0
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v1.1.0-RC...v1.1.0
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v1.1.0-RC...v1.1.0
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v1.1.0-RC...v1.1.0
.. _`Workflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v1.1.0-RC...v1.1.0
.. _`Media admin bundle`: https://github.com/open-orchestra/open-orchestra-media-admin-bundle/compare/v1.1.0-RC...v1.1.0
.. _`Orchestra libs`: https://github.com/open-orchestra/open-orchestra-libs/compare/v1.1.0-RC...v1.1.0
.. _`Orchestra Mongo libs`: https://github.com/open-orchestra/open-orchestra-mongo-libs/compare/v1.1.0-RC...v1.1.0
.. _`Media file bundle`: https://github.com/open-orchestra/open-orchestra-media-file-bundle/compare/v1.1.0-RC...v1.1.0
.. _`Elastica bundle`: https://github.com/open-orchestra/open-orchestra-elastica-bundle/compare/v1.1.0-RC...v1.1.0
