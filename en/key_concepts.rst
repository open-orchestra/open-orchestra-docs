Key concepts
============

This document will explain the most important concepts to start with Open Orchestra.

Pages
-----

Nodes
~~~~~

In the Open Orchestra project, a page is identified as a node. They are containers for zones and blocks.
The nodes are multilingual, versioned and have a validation workflow.

There are two types of nodes in Open Orchestra:

* Nodes that represent pages of the website
* The transverse node containing the transverse blocks (blocks that can be used in other pages, for instance the menu block).
  This node is not versioned, and there can only be one transverse node in each language of the site.


See also the documentation page about `node parameters`_.

Zones
~~~~~

Zones are the way to organize the architecture of the page.
They are embedded in the nodes and can contain other zones or blocks exclusively.

See also `configuring a zone`_.

Blocks
~~~~~~

A block is the base brick representing any visible element on a page.
Aggregating blocks found in the nodes will lead to the construction of the pages.

See also the `list of blocks`_ available.

Transverses blocks
~~~~~~~~~~~~~~~~~~

Transverses blocks are defined inside the transverse node, they can be shared by several nodes of a website.
All blocks can be transverse, as long as they are added to the transverse node.
Transverse blocks can only be conigured in the transverse node.

Templates
~~~~~~~~~

Templates are used to preconfigure nodes by setting zones that are commonly used accross pages.
Open Orchestra let the user start with a template when creating a node.

See also `configuring a template`_.

Summary
~~~~~~~

This scheme represents how those different part are related to one another.

.. image:: ../../images/drag_block.png

Contents
--------

Contents
~~~~~~~~

In Open Orchestra, contents are used to display contributed information (articles, news, etc.).
The contents are defined by a content type.
Like nodes, contents are multilingual, versionned and have a validation workflow.

See also `Presentation of contents`_.

Content types
~~~~~~~~~~~~~

Content types are a way to create new kinds of content that will be available to contribution.
Creating a content type allows to define the fields available in the future contents.

For instance, a 'news' content will have differents fields from an 'article' content,
so there would be two distinct content types for these objects : one for the news contents
and another for the article contents.

See also `Presentation of the Content Types`_.

Medias
~~~~~~

If you use the full Open Orchestra installation, you will be able to upload and managed different kind
of medias.

The medias can be used in ``Contents`` or in ``Blocks``.

See also the `Media presentation`_.

Keywords
~~~~~~~~

Keywords can be created in the Back Office, and then be used to tag contents and medias.

See also how to work with `keywords'_.

Sites
-----

Themes
~~~~~~

A theme represents the visual identity of a website, the  CSS and JavaScript files
that work together in order to render the websites the way you desire.

See how to add a `theme`_.

Websites
~~~~~~~~

Open Orchestra is multisite and allows to create several websites from the same Back Office application.

See also how to configure a `website`_.

Devices
-------

Open Orchestra is multi-device and is able to display, on the Front Office,
different templates depending on the device of the visitor.

See also `multi-devices`_.

Users
-----

Users
~~~~~

Users represent people that can connect to the Open Orchestra Back Office and make contributions.
They also are the Front Office users who can access to the private pages of a website.
It's also possible to assign groups to users.

See also how to configure a `user`_.

Roles
~~~~~

Roles allow to define authorization in the Back Office.

See also how to create a `role`_.

Groups
~~~~~~

Groups combine roles (this combination depends on the website) and are assigned to users.
Groups can have several roles.

See also how to create a `group`_.

Bundles
-------

Open Orchestra is a set of different Symfony bundles directly accessible

Open Orchestra's bundles :

 * open-orchestra-base-bundle contains some transverse classes common to Back Office and Front Office.
 * open-orchestra-cms-bundle is the application logic for the Back Office.
 * open-orchestra-front-bundle is the application logic for the Front Office.
 * open-orchestra-display-bundle contains all the block display strategies for the Front Office.
 * open-orchestra-model-interface is a full description of the model classes used by other bundles.
 * open-orchestra-model-bundle contains implements the interfaces for a mongodb database.
 * open-orchestra-media-bundle contains the media functionnalities.
 * open-orchestra-user-bundle groups all user logic.

In order to use another database system one should had a new bundle which classes will implement
the interfaces defined in open-orchestra-model-interface.


.. _role: /en/user_guide/role.rst
.. _site: /en/user_guide/website_creation.rst
.. _user: /en/user_guide/user.rst
.. _theme:
.. _group:
.. _website: /en/user_guide/website_creation.rst
.. _keywords: /en/user_guide/keyword_management.rst
.. _multi-devices: /en/user_guide/media.rst
.. _list of blocks: /en/user_guide/block_list.rst
.. _node parameters: /en/user_guide/node.rst
.. _Media presentation: /en/user_guide/media.rst
.. _configuring a zone:
.. _configuring a template:
.. _Presentation of contents: /en/user_guide/content.rst
.. _Presentation of the Content Types: /en/user_guide/content_type.rst
