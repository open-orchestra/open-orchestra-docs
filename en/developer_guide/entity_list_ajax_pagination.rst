Entity list with ajax pagination
================================
Context
-------

To list the entities in an ergonomic way, Open Orchestra uses the  `DataTables`_ plugin.
To improve performance, the pagination uses ajax calls.

For each display of the information on the page (i.e. paging, ordering, searching),
the plugin makes an ajax request to the api with a number of parameters.


Usage
-----

The different variables used to filter (pagination, search, ordering) send by the plugin are:

+-----------------------+--------------------------------------------------+
| **Parameter name**    | **Description**                                  |
+-----------------------+--------------------------------------------------+
| order[name]           | Column's name to which ordering                  |
|                       | should be applied                                |
+-----------------------+--------------------------------------------------+
| order[dir]            | Ordering direction (asc or desc)                 |
+-----------------------+--------------------------------------------------+
| search[columns][name] | Search value to apply to a specific column       |
|                       | Name is the ``name`` of column                   |
+-----------------------+--------------------------------------------------+
| search[global]        | Global search value                              |
+-----------------------+--------------------------------------------------+
| length                | Number of records that the table                 |
|                       | can display in the current draw                  |
+-----------------------+--------------------------------------------------+
| start                 | Paging first record indicator                    |
+-----------------------+--------------------------------------------------+

The ``search`` parameter is not present in the request if there is no value in all search input field.

Example of parameters sent:

.. code-block::

    order[name]:version
    order[dir]:asc
    start:0
    length:50
    search[columns][version]:2
    search[global]:car

In order to make the pagination operational, the api should return a facade filled with 4 parameters:
 * recordsTotal: Total number of entities
 * recordsFiltered: Number of entities matching the filters (search)
 * collectionName: The name of variable which contains the data
   (for instance if collectionName equals ``contents`` then the data will be in the variable ``$contents``)
 * data: The data to be displayed in the table. This is an array who contains your data (facade entity)
   after filtering (search, order, pagination)

For instance, here comes the json returned by the api for listing the workflow functions:

.. code-block:: json

    {
        "links":{},
        "collection_name":"workflow_functions",
        "workflow_functions": [
            {
            "id":"558162b902b0cfc4118b45a7",
            "links":{},
            "name":"Contributor"
            },
            {
            "id":"558162b902b0cfc4118b45a6",
            "links":{},
            "name":"Validator"
            }
        ],
        "recordsTotal":2,
        "recordsFiltered":2
    }

Server side search
------------------
Open Orchestra provides a set of tools to help you perform the server side search.

The ``OpenOrchestra\Pagination\MongoTrait\PaginationTrait`` trait should be used in
repositories supporting aggregation queries. It contains three methods:

* ``findForPaginate(PaginateFinderConfiguration $configuration)`` finds documents from
  various criteria defined in the configuration object
* ``count()`` counts all documents of the collection
* ``countWithFilter(PaginateFinderConfiguration $configuration)`` counts documents according
  to the configuration object

``PaginateFinderConfiguration`` is a configuration object with different properties
(``order``, ``limit``, ``skip``, ``search`` and ``descriptionEntity``), which,
except ``descriptionEnity``, can be automatically filled from the request sent by the dataTables
with the static method ``PaginateFinderConfiguration::generateFromRequest(Request $request)``.

The ``descriptionEntity`` property is an array describing the mapping between the columns
displayed in the dataTable and the entity properties.

For instance in the list of redirections there are five columns (``SiteName``, ``Routepattern``,
``Locale``, ``Redirection`` and ``Permanent``). In the ``Redirection`` entity the properties
matching these columns are:

.. code-block:: php

    class Redirection
    {
        // ...

        /**
         * @ODM\Field(type="string")
         */
        protected $locale;

        /*
         * @ODM\Field(type="string")
         */
        protected $siteName;

        /**
         * @ODM\Field(type="string")
         */
        protected $routePattern;

       /**
         * @ODM\Field(type="string")
         */
        protected $url;

        /**
         * @ODM\Field(type="boolean")
         */
        protected $permanent;

        // ...
    }

The ``descriptionEntity`` property linked to the ``Redirection`` will be:

.. code-block:: php

    $descriptionEntity = array(
        'site_name' => new Search('name' => 'siteName', 'type' => 'string', 'key' => 'site_name'),
        'route_pattern' => new Search('name' => 'routePattern', 'type' => 'string', 'key' => 'route_pattern'),
        'redirection' => new Search('name' => 'url', 'type' => 'string', 'key' => 'redirection'),
        'permanent' => new Search('name' => 'permanent', 'type' => 'boolean', 'key' => 'permanent'),
    )

The ``Search`` object describes an entity's property with three parameters:

* ``name`` : name of the entity's property
* ``type`` : type of the entity's property
* ``key`` : name of the property in your facade used by the dataTable

Open Orchestra provides the ``Search`` annotation to help you describe the mapping directly
in your entities.

For instance, the ``Redirection`` entity will look like:

.. code-block:: php

    use OpenOrchestra\Mapping\Annotations as ORCHESTRA;

    class Redirection
    {
        // ...

        /**
         * @ODM\Field(type="string")
         * @ORCHESTRA\Search(key="locale")
         */
        protected $locale;

        /*
         * @ODM\Field(type="string")
         * @ORCHESTRA\Search(key="site_name")
         */
        protected $siteName;

        /**
         * @ODM\Field(type="string")
         * @ORCHESTRA\Search(key="route_pattern")
         */
        protected $routePattern;

       /**
         * @ODM\Field(type="string")
         * @ORCHESTRA\Search(key="redirection")
         */
        protected $url;

        /**
         * @ODM\Field(type="boolean")
         * @ORCHESTRA\Search(key="permanent", type="boolean")
         */
        protected $permanent;

        // ...
    }

``type`` will take ``string`` as a default parameter.
``name`` will take the name of the property if not set.

The ``open_orchestra_api.annotation_search_reader`` will build the ``descriptionEntity``.

.. code-block:: php

    $mapping = $this->get('open_orchestra_api.annotation_search_reader')
        ->extractMapping('OpenOrchestra\ModelBundle\Document\Redirection');

.. _`DataTables`: https://www.datatables.net/
.. _`documentation`: https://www.datatables.net/manual/server-side#Sent-parameters
