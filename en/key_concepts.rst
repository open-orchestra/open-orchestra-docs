Key concepts
============

This document will explain the most important concepts to start with Open Orchestra.

Nodes
-----

Nodes are mainly pages that the visitors can see on the website, they are containers for zones and blocks.
There are two types of nodes in Open Orchestra:
* Nodes that represent pages of the website
* The transverse node (which is unique) containing the transverse blocks (blocks that are common to multiple pages of a website, for instance the menu block).

The nodes are multilingual, versionned and have a validation workflow.

See also the documentation page about `node parameters`_.

Content types
-------------

Content types are a way to create new kinds of content that will be available to contribution.
Creating a content type allows to define the fields available in the future contents.

For instance, a 'news' content will have differents fields from an 'article' content,
so there would be two distinct content types for these objects : one for the news contents and another for the article contents.

See also `Presentation of the Content Types`_.

Contents
--------

With Open Orchestra, contents are used to display contributed information (articles, news, etc.).
The contents are defined by a content type.
Like nodes, contents are multilingual, versionned and have a validation workflow.

See also `Presentation of contents`_.

Templates
---------

Templates are used to preconfigure pages by setting zones that are commonly used accross pages.
Open Orchestra let the user start with a template when creating a node.

See also `configuring a template`_.

Zones
---------

Zones are the way to organize the architecture of the page.
They are embedded in the nodes and can contain other zones or blocks.

See also `configuring a zone`_.

Blocks
---------

A block is the base brick representing any visible element on a page.
Aggregating blocks found in the nodes will lead to the construction of the pages.

See also the `list of blocks`_ available.

Transverses blocks
------------------

Transverses blocks are defined inside the transverse node, they can be shared by several nodes of a website.
All blocks can be transverse, as long as they are added to the transverse node.
Transverse blocks can only be conigured in the transverse node.

Themes
------

A theme represents the visual identity of a website, the  CSS and JavaScript files
that work together in order to render the websites in a certain way.

See how to add a `theme`_.

Websites
--------

Open Orchestra is multisite and allows to create several websites from the same Back Office application.

See also how to configure a `website`_.

Devices
-------

Open Orchestra is multi-device and is able to display, on the Front Office,
different templates depending on the device of the visitor.

See also `multi-devices`_.

Keywords
--------

Keywords can be created in the Back Office, and then be used to tag contents and medias.

Users
-----

Users represent people that can connect to the Open Orchestra Back Office and make contributions.
They also are the Front Office users who can access to the private pages of a website.
It's also possible to assign groups to users.

See also how to configure a `user`_.

Roles
-----

Roles allow to define authorization in the Back Office.

See also how to create a `role`_.

Groups
-----------

Groups combine roles (this combination depends on the website) and are assigned to users.
Groups can have several roles.

See also how to create a `group`_.

Bundles
-----------

Open Orchestra is built on Symfony so the code is split into different bundles.

Open Orchestra's bundles :

 * open-orchestra-base-bundle contains some transverse classes common to Back Office and Front Office.
 * open-orchestra-cms-bundle is the application logic for the Back Office.
 * open-orchestra-front-bundle is the application logic for the Front Office.
 * open-orchestra-display-bundle contains all the block display strategies for the Front Office.
 * open-orchestra-model-interface is a full description of the model classes used by other bundles.
 * open-orchestra-model-bundle contains the database access logic (doctrinemongodb).
 * open-orchestra-media-bundle contains the media functionnalities.
 * open-orchestra-user-bundle groups all user logic.

In order to use another database system one should had a new bundle which classes will implement
the interfaces defined in open-orchestra-model-interface.

.. _rôle:
.. _site:
.. _thème:
.. _groupe:
.. _utilisateur:
.. _multi-devices:
.. _liste des blocs:
.. _configuration d'une zone:
.. _Présentation des contenus:
.. _Les paramètres d'un noeud:
.. _configuration d'un template:
.. _Présentation des types de contenus:
