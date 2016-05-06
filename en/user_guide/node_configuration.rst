Node configuration
==================

Here are the available options in the `node`_ configuration. Some of them are required
in order to build a node and must therefore be provided.

Page (required)
---------------

The page attribute is the name of the node, it is also used to build the url pattern.

Url pattern (required)
----------------------

The url pattern attribute is generated automatically with the name of the page.
It represents the pattern that will be the URL of the page on the website.

If the pattern starts with a slash, it will be appended to the  website's base url
(domain + language prefix) to make the full page url. Otherwise, if the page has a parent,
the pattern will be appended to the parent's URL to generate the final URL.

Here is a as example of some URL generated from the page patterns if the website's
domain is "example.com" and the language is "en".

+---------+---------------------+------------------------+
| pattern | parent page pattern | final URL              |
+=========+=====================+========================+
| /foo    | /bar                | example.com/en/foo     |
+---------+---------------------+------------------------+
| foo     | /bar                | example.com/en/bar/foo |
+---------+---------------------+------------------------+
| foo     | no parent page      | example.com/en/foo     |
+---------+---------------------+------------------------+

Some node url might contains variable to works. To add them, you should put the
variable name between braces.

For instance, a page with content id required:

+----------------+---------------------+-------------------------------+
| pattern        | parent page pattern | final URL                     |
+================+=====================+===============================+
| {contentId}    | no parent page      | example.com/en/any-content-id |
+----------------+---------------------+-------------------------------+

Scheme (required)
-----------------

The scheme defines which protocol the page can be accessed by (http, https, etc...).
By default Open Orchestra uses the value set in the site configuration.

Indicative periodicity of change
--------------------------------

This attribute is used to optimize the sitemap data.

Relative importance compared to the other pages of the site
-----------------------------------------------------------

This attribute manages the importance of the page regarding the other pages.
It is used in the sitemap generation.

The theme (required)
--------------------

The theme to use on the page is chosen here.

Show in menus
-------------

This attribute indicates if the page should appear in the menus.
It is used when rendering a menu block.

Show in footer
--------------

This attribute indicates if the page should appear in a footer.
It is used when rendering a footer block.

Meta
----
The meta attributes provide information about the nature and content of a web page,
they are added in the page HTML header with the use of meta tags.
These attributes are also provided in the website configuration, which value is used
if they are not overridden by the page configuration.

Meta keywords
~~~~~~~~~~~~~

This is a list of keywords associated to the page and can be used by search engines for ranking.

Meta description
~~~~~~~~~~~~~~~~

This is used by search engines to display a description of the page in the results list.

Meta index
~~~~~~~~~~

This attribute defines whether or not the page should be referenced in search engines.

Meta follow
~~~~~~~~~~~

This attribute indicates to search engines if they should follow the hypertext links
on the page in order to index other documents.

Role needed to display the page
-------------------------------

The role attribute defines which role is allowed to access the page.
Pages are public by default, if a role is selected then only a user with the
mandatory roles will be able to access the page.

Max age of the response for the node
------------------------------------

This attribute is used to set up the lifetime of this page inside the cache.


Attributes specific to page creation
------------------------------------
When creating a new page, one of the two following attributes must be used.

Source page
~~~~~~~~~~~

The source page attribute allows to create a new page by copying the content of an existing page.

Template id
~~~~~~~~~~~

The template id allows to define a template that should be use as a basis for the page.

.. _`node`: ../user_guide/node.html
