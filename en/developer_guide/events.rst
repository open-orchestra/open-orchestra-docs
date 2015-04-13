Events available in Open Orchestra
==================================

Open Orchestra dispatches lots of events in different places of the code,
a lot of them being used for logging the website's activity.
This pages lists the events than can be subscribed to during execution.

Categories of events
--------------------

Nodes
~~~~~

These events are defined in the class ``OpenOrchestra\ModelInterface\NodeEvents`` and inherit ``OpenOrchestra\ModelInterface\Event\NodeEvent``.

* NodeEvent
    * Node creation : NODE_CREATION
    * Node removal : NODE_DELETE
    * Node update  : NODE_UPDATE
    * Node duplication : NODE_DUPLICATE
    * Adding a language to a node : NODE_ADD_LANGUAGE
    * Status update for a node : NODE_CHANGE_STATUS
    * Path update for a node : PATH_UPDATED

* NodeEvent : Area
    * Area update : NODE_UPDATE_AREA
    * Area removal : NODE_DELETE_AREA

* NodeEvent : Block
    * Block update : NODE_UPDATE_BLOCK
    * Block position update : NODE_UPDATE_BLOCK_POSITION
    * Block removal : NODE_DELETE_BLOCK

Template
~~~~~~~~

These events are defined in the class ``OpenOrchestra\ModelInterface\TemplateEvents`` and inherit ``OpenOrchestra\ModelInterface\Event\TemplateEvent``.

* TemplateEvent
    * Template creation : TEMPLATE_CREATE
    * Template removal : TEMPLATE_DELETE
    * Template update : TEMPLATE_UPDATE
    * Area removal in template : TEMPLATE_AREA_DELETE
    * Area update in template : TEMPLATE_AREA_UPDATE

Media
~~~~~

These events are defined in the classes ``OpenOrchestra\Media\MediaEvents`` and ``OpenOrchestra\Media\FolderEvents``
and inherit ``OpenOrchestra\Media\Event\MediaEvent`` and ``OpenOrchestra\Media\Event\FolderEvent`` respectively.

* FolderEvent
    * Folder creation : FOLDER_CREATE
    * Folder removal : FOLDER_DELETE
    * Folder update : FOLDER_UPDATE

* MediaEvent
    * Image upload : ADD_IMAGE
    * Image removal : MEDIA_DELETE
    * Image cropping : MEDIA_CROP

* ImagickEvent
    * Image resizing : RESIZE_IMAGE

Content
~~~~~~~

These events are defined in the class ``OpenOrchestra\ModelInterface\ContentEvents`` and inherit ``OpenOrchestra\ModelInterface\Event\ContentEvent``.

* ContentEvent
    * Content creation : CONTENT_CREATION
    * Content removal : CONTENT_DELETE
    * Content update : CONTENT_UPDATE
    * Content duplication : CONTENT_DUPLICATE
    * Content status update : CONTENT_CHANGE_STATUS

Administration
--------------

Content types
~~~~~~~~~~~~~

These events are defined in the class ``OpenOrchestra\ModelInterface\ContentTypeEvents`` and inherit ``OpenOrchestra\ModelInterface\Event\ContentTypeEvent``.

* ContentTypeEvent
    * Content type creation : CONTENT_TYPE_CREATE
    * Content type removal :  CONTENT_TYPE_DELETE
    * Content type update : CONTENT_TYPE_UPDATE

Keyword
~~~~~~~

These events are defined in the class ``OpenOrchestra\ModelInterface\KeywordEvents`` and inherit ``OpenOrchestra\ModelInterface\Event\KeywordEvent``.

* KeyWordEvent
    * Keyword creation : KEYWORD_CREATE
    * Keyword removal : KEYWORD_DELETE

Redirection
~~~~~~~~~~~

These events are defined in the class ``OpenOrchestra\ModelInterface\RedirectionEvents`` and inherit ``OpenOrchestra\ModelInterface\Event\RedirectionEvent``.

* RedirectionEvent
    * Redirection creation : REDIRECTION_CREATE
    * Redirection removal : REDIRECTION_DELETE
    * Redirection update : REDIRECTION_UPDATE

Roles
~~~~~

These events are defined in the class ``OpenOrchestra\ModelInterface\RoleEvents`` and inherit ``OpenOrchestra\ModelInterface\Event\RoleEvent``.

* RoleEvent
    * Role creation : ROLE_CREATE
    * Role removal : ROLE_DELETE
    * Role update : ROLE_UPDATE

Sites
~~~~~

These events are defined in the class ``OpenOrchestra\ModelInterface\SiteEvents`` and inherit ``OpenOrchestra\ModelInterface\Event\SiteEvent``.

* SiteEvent
    * Site creation : SITE_CREATE
    * Site removal : SITE_DELETE
    * Site update : SITE_UPDATE

Status
~~~~~~

These events are defined in the class ``OpenOrchestra\ModelInterface\StatusEvents`` and inherit ``OpenOrchestra\ModelInterface\Event\StatusEvent``.

* StatusEvent
    * Création d'un status creation : STATUS_CREATE
    * Status removal : STATUS_DELETE
    * Status update: STATUS_UPDATE

* StatusableEvent
    * Status change : STATUS_CHANGE

StatusableEvent is use when changing status of a node, content or media reference.

Themes
~~~~~~

These events are defined in the class ``OpenOrchestra\ModelInterface\ThemeEvents`` and inherit ``OpenOrchestra\ModelInterface\Event\ThemeEvent``.

* ThemeEvent
    * Theme creation : THEME_CREATE
    * Theme removal : THEME_DELETE
    * Theme update : THEME_UPDATE

Users
~~~~~

These events are defined in the class ``OpenOrchestra\UserBundle\GroupEvents`` and ``OpenOrchestra\UserBundle\UserEvents``
and inherit ``OpenOrchestra\UserBundle\Event\GroupEvent`` and ``OpenOrchestra\UserBundle\Event\UserEvent`` respectively.

* GroupEvent
    * Group creation : GROUP_CREATE
    * Group removal : GROUP_DELETE
    * Group update : GROUP_UPDATE

* UserEvent
    * User creation : USER_CREATE
    * User removal : USER_DELETE
    * User update : USER_UPDATE

Exemple of event dispatching
----------------------------

You can easily dispatch your own events or Open Orchestra events as you would normally do with Symfony.

.. code-block:: php

    $this->get('event_dispatcher')->dispatch(NodeEvents::NODE_UPDATE, new NodeEvent($node));
