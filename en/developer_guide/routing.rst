Routing
=======

Base URL
--------

In Open Orchestra, the base url of a website is composed by the domain and possibly a language prefix.
To manage all the possibilities, Open Orchestra associates each website in the database with website aliases which contain:

* **domain**: domain name
* **language prefix**: used by Open Orchestra to define the language
* **scheme** : to choose with which protocol page can be accessed

Here is an example of some base URL generated for a website associate to two domains: ``dev.example.com`` and ``test.example.com``,
each of them, with english as default language and french as secondary one.

+----------+--------+------------------+----------+-----------------+-----------------------------+
| Alias Id | Scheme | Domain           | Language | Language prefix | Base URL                    |
+==========+========+==================+==========+=================+=============================+
| 0        | http   | dev.example.com  | fr       | fr              | http://dev.example.com/fr   |
+----------+--------+------------------+----------+-----------------+-----------------------------+
| 1        | http   | dev.example.com  | en       | none            | http://dev.example.com      |
+----------+--------+------------------+----------+-----------------+-----------------------------+
| 2        | http   | test.example.com | fr       | fr              | http://test.example.com/fr  |
+----------+--------+------------------+----------+-----------------+-----------------------------+
| 3        | https  | test.example.com | en       | none            | https://test.example.com    |
+----------+--------+------------------+----------+-----------------+-----------------------------+


URL Pattern
-----------

The url pattern is added to the ``base URL`` to generate the url.
For a node, the url pattern can be chosen by the contributor or is generated automatically from the page title.

It uses Symfony rules :

* Variables to extract between {}, ex : ``/example/{param}/test``
* Pattern have to be unique

See the ``Url pattern`` chapter from `Node Configuration`_ for more details.

Redirection
-----------

Open Orchestra allows users to determine redirection in the back office.
The redirection form contains some arguments:

* **site name**: contextual site which triggers the redirection
* **site language**: contextual language which triggers the redirection
* **pattern to redirect**: pattern that will be the URL of the redirection
* **node where the redirection is headed**: redirect to a node
* **Url to redirect to**: redirect to url if node is not specify
* **permanent redirection**: Use to adapt response code

Example:

+-------------------+----------+---------------------+------+-------------------------------+
| Base Site         | Language | Pattern to redirect | Node | URL to redirect               |
+===================+==========+=====================+======+===============================+
| http://example.fr | english  | oo                  | none | http://www.open-orchestra.com |
+-------------------+----------+---------------------+------+-------------------------------+
| http://example.fr | french   | open-orchestra      | HOME | none                          |
+-------------------+----------+---------------------+------+-------------------------------+

If an user comes on ``http://example.fr/oo`` so the english site with the good pattern,
it will be redirect to the ``http://www.open-orchestra.com`` website.

If an user comes on ``http://example.fr/fr/open-orchestra`` so the french site with the good pattern,
it will be redirect to the ``HOME`` node of the french page.

But if an user comes on ``http://example.fr/fr/oo``, it will have a ``404 not found`` error page because redirections
are attached to languages.

Implementations
---------------

Open Orchestra provides two alternatives mechanisms for the routing :

* Get the url directly from the database (default configuration)
* Dump the route in a cache file

We are going to see how to configure one or the other, then which solution you could choose for your project.

Routing from the database
~~~~~~~~~~~~~~~~~~~~~~~~~

In the database, Open Orchestra saves all the routes (for the nodes, and redirections) with document implementing
the ``RouteDocumentInterface``.

When you perform a request, the router called is the ``OpenOrchestraDatabaseRouter``. It will check in the database
for a matching route.

As this configuration is the default one, you have no modification to make to the project configuration.

Routing in the file
~~~~~~~~~~~~~~~~~~~

Open Orchestra is also able to dump all the routes (nodes and redirection) inside a cache file.

When you perform a request, the router called is the ``OpenOrchestraRouter``. It will check in the cache file for
a matching route.

To configure this router, you  have to specify the different loader you are using (nodes and redirection) in
the ``routing.yml`` file :

.. code-block:: yaml

    open_orchestra_database:
        resource: '.'
        type: database

    open_orchestra_redirection:
        resource: '.'
        type: orchestra_redirection

You also have to modify the project configuration, in the ``config.yml`` file :

.. code-block:: yaml

    open_orchestra_front:
        routing_type: file

How to choose between both of the solutions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This part will not tell you which routing type you should use, but only list some condition to use
one or the other.

You have a lot of pages, and they are updated by a big number of people all the time :

* Use the database routing, no cache file will be updated each time a route is created

There is only a few update of the pages :

* If you want to lower the number of query to the database, use the file routing
* Use the database routing if there is no restriction

You are not using the Open Orchestra Back Office :

* Use the file routing, you will only have to configure the application
* Use the database routing, but note that you need to update the ``route_document`` collection each time
  a node is updated

.. _`Node Configuration`: ../user_guide/node_configuration.html
