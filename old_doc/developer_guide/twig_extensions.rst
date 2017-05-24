Twig extensions
===============

Some twig extensions have been developed specifically for Open Orchestra and are available for use.

Media functions
---------------

If you are using the media bundles, you will probably have to manipulate media within your twig templates. You
can use these twig extensions to help you:

* ``display_media(mediaId, format)``: render a media (or an alternative) using the DisplayMediaManager
* ``get_media_url(mediaId, format)``: get the url of a media (or an alternative)
* ``get_media_title(mediaId)``: get the title of a media, in the current language
* ``get_media_alt(mediaId)``: get the alt of a media, in the current language

Theme functions
---------------

In Open Orchestra, themes are easily configurable by defining the list of
JavaScript and CSS files used in the configuration of the application for each theme.

In order to render the HTML tags for these files, two functions are available in Twig :

* ``openOrchestraCss(themeId)``: render a html stylesheet tag linking the css of the theme
* ``openOrchestraJs(themeId)``: render a html javascript tag linking the javascript of the theme

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
