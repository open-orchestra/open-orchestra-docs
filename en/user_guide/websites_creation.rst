Website creation
================

Open Orchestra is multisite and allows to create several websites from the same Back Office application.

Name (required)
---------------

The name field is used for the website name and it allows to generate the identifier of the website.

Website id (required)
---------------------

The site id can be generated from the site name or directly by the user at the creation.
In the remaining process, this field is not anymore editable.
Open Orchestra verifies during the form validation that the site id does not already exist.

.. image:: ../../images/website_id.png

Aliases
-------

Open Orchestra allows to create  several aliases for a site.

For example :

* Scheme by default (required): http
* Domain (required): demo.openorchestra.dev
* Language (required): English
* Language prefix : en
* main aliases : on

The website home page will be ``http://demo.openorchestra.dev/en``.

See the `routing documentation`_ for further information.

Open Orchestra uses only the main alias for the sitemap generation.

.. image:: ../../images/aliases.png

Blocks available
----------------

This attribute lists all the blocks available for the nodes of this website.
Only the selected blocks will be available during the node contribution.

.. image:: ../../images/blocks_available.png

Default Theme (required)
------------------------

The attribute theme is the default theme used by the website.
Each node can also have its own theme.

Sitemap generation (required)
-----------------------------

The two folling attributes are used for the sitemap generation :

* Indicative periodicity of change
* Relative importance compared to the other pages of the website, this attribute is used by default for the node creation.

Meta
----

The meta attributes provide information about the nature and content of a web page, they are added in the page HTML header with the use of meta tags.
These attributes are also provided in the website configuration, which value is used if they are not overriden by the page configuration.

.. image:: ../../images/meta.png

Meta keyword
~~~~~~~~~~~~

This is a list of keywords asociated to the page and can be used by search engines for ranking.

Meta description
~~~~~~~~~~~~~~~~

This is used by search engines to display a description of the page in the results list.

Meta index
~~~~~~~~~~

This attribute defines whether or not the page should be referenced in search engines.

Meta follow
~~~~~~~~~~~

This attribute indicates to search engines if they should follow the hypertext links on the page in order to index other documents.

Informations contained in the robots.txt file (required)
--------------------------------------------------------

This attribute contains the data of the robots.txt file.

robots.txt file example
~~~~~~~~~~~~~~~~~~~~~~~

    User-agent: *
    Allow: /

User-agent: * means that one or several instruction (s) which follow applies for all the agents.
Allow: / means that the search engine can browse all the directories and the pages of the site.

.. _routing documentation: /en/developer_guide/routing.rst
