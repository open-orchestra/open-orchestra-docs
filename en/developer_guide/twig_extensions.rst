Twig extensions
===============

Some twig extensions have been developed specifically for Open Orchestra and are available for use.

Theme functions
---------------

In Open Orchestra, themes are easily configurable by defining the list of
JavaScript and CSS files used in the configuration of the application for each theme.

In order to render the HTML tags for these files, two functions are available in Twig :

* openOrchestraCss()
* openOrchestraJs()

Each one takes in parameter the string identifier of the theme that should be used on the website.

Tree generation
---------------

A tree structure is the most easy to use when it can be browsed recursively from root to leaves.
However, data is not always formatted in this way, and may be just a flat array of
objects, each one having a property defining its own parent. This is the case of the nodes
that are displayed in a menu block : each one know its parent but they are all
at the same level when they are retrived from the database.

To solve this issue, the ``OpenOrchestra\DisplayBundle\Manager\TreeManager`` class has been created,
with its method ``generateTree()`` being wrapped in the ``tree_formatter()`` Twig function.
Provided an array of ReadNodeInterface, it will return a multi-level array of nodes
for easy HTML rendering.
