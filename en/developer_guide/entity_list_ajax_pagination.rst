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
+-----------------------+--------------------------------------------------+
| search[global]        | Global search value                              |
+-----------------------+--------------------------------------------------+
| length                | Number of records displayed in the current draw  |
+-----------------------+--------------------------------------------------+
| start                 | Paging first record indicator                    |
+-----------------------+--------------------------------------------------+

The ``search`` parameter is not present in the request if there is no value in all search input field.

Example of parameters sent:

.. code-block:: none

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
        'site_name' => array('field' => 'siteName', 'type' => 'string', 'key' => 'site_name'),
        'route_pattern' => array('field' => 'routePattern', 'type' => 'string', 'key' => 'route_pattern'),
        'redirection' => array('field' => 'url', 'type' => 'string', 'key' => 'redirection'),
        'url' => array('field' => 'url', 'type' => 'string', 'key' => 'url'),
        'permanent' => array('field' => 'permanent', 'type' => 'boolean', 'key' => 'permanent'),
    )

* ``field`` : name of the entity's property
* ``type`` : type of the entity's property
* ``key`` : name of the property in your facade used by the dataTable

This mapping can be specified in a number of different formats including YAML, XML or
directly inside your entities class via annotations

For instance, the ``Redirection`` entity will look like:

Annotation:

.. code-block:: php

    // src/AppBundle/Document/Redirection.php
    namespace AppBundle\Document;

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
         * @ORCHESTRA\Search(key={"redirection", "url"})
         */
        protected $url;

        /**
         * @ODM\Field(type="boolean")
         * @ORCHESTRA\Search(key="permanent", type="boolean")
         */
        protected $permanent;

        // ...
    }

Yaml:

.. code-block:: yaml

    # src/AppBundle/Resources/config/search/Document.Redirection.yml

    AppBundle\Document\Redirection:
        properties:
            locale:
                key: locale
            siteName:
                key: site_name
            routePattern:
                key: route_pattern
            url:
                key: [redirection, url]
            permanent:
                key: permanent
                type: boolean

Xml:

.. code-block:: xml

    <!-- src/AppBundle/Resources/config/search/Redirection.xml -->

    <search-mapping>
        <class name="AppBundle\Document\Redirection">
            <field field="locale" key="locale" />
            <field field="siteName" key="site_name" />
            <field field="routePattern" key="route_pattern" />
            <field field="url" key="redirection, url" />
            <field field="locale" key="locale" />
            <field field="permanent" key="permanent" type="boolean"/>
        </class>
    </search-mapping>

The ``open_orchestra_api.annotation_search_reader`` will extract the ``descriptionEntity``.

.. code-block:: php

    $mapping = $this->get('open_orchestra_api.annotation_search_reader')
        ->extractMapping('OpenOrchestra\ModelBundle\Document\Redirection');

Notes
-----

In the mapping :

* ``type`` will take ``string`` as a default parameter if it is not specified.
* With the mapping in annotation ``field`` will take the name of the property if it is not set.

By default the xml and yaml mapping files should be located in the folder ``Ressources/config/search`` of your bundle.
To specify another folder, you must change the configuration :

.. code-block:: yaml

    open_orchestra_mongo:
        search_metadata:
            directories:
                AppBundle:
                    namespace_prefix: "My\\AppBundle"
                    path: \@AppBundle/Ressources/config/mymapping

Custom search field of columns
------------------------------

By default, Open Orchestra provides differents search fields for columns (text, date, number and boolean).
You can specify the fields types in the data attribute ``input-header`` of the navigation panel link
(futher information in document of `navigation panel`_).

To create a custom search field, you should create a backbone view and add it in the ``OpenOrchestra.DataTable.ViewFieldConfigurator``.

For instance with the text field:

.. code-block:: coffeescript

  (($, OpenOrchestra) ->

    ###*
     * @class TextFieldSearchView
    ###
    class TextFieldSearchView extends AbstractSearchFieldView

      events:
        'keyup input.search-column': 'searchColumn'

      ###*
       * required options
       * {
       *   column: {integer} column index
       *   api: {object} DataTable api
       *   domContainer: {object} jquery element
       * }
       * @param {Object} options
      ###
      initialize: (options) ->
        @options = @reduceOption(options, [
          'columnIndex'
          'domContainer'
          'api'
        ])
        @loadTemplates [
          'OpenOrchestraBackofficeBundle:BackOffice:Underscore/datatable/header/textField'
        ]

      ###*
       * @return {this}
      ###
      render: ->
        @setElement @renderTemplate('OpenOrchestraBackofficeBundle:BackOffice:Underscore/datatable/header/textField',
            column: @options.columnIndex
            value: @options.api.column(@options.columnIndex).search()
        )
        @insertFieldInHeader()

        return @

    OpenOrchestra.DataTable = {} if not OpenOrchestra.DataTable?
    OpenOrchestra.DataTable.ViewFieldConfigurator = {} if not OpenOrchestra.DataTable.ViewFieldConfigurator?
    OpenOrchestra.DataTable.ViewFieldConfigurator.text = TextFieldSearchView

  ) jQuery,
    window.OpenOrchestra = window.OpenOrchestra or {}

You can extend ``AbstractSearchFieldView`` to facilitate research and insertion of the field in the header.

The key in ``OpenOrchestra.DataTable.ViewFieldConfigurator`` defines the name used in data-attribute (``input-header``).

With this custom view, it is possible to create a completly dynamic field, not only static ones.
By sending an ajax request in the view, 
the server can interact with the rendering of the search field for instance.

.. _`DataTables`: https://www.datatables.net/
.. _`documentation`: https://www.datatables.net/manual/server-side#Sent-parameters
.. _`navigation panel`: /en/latest/developer_guide/ǹavigation_panel.html
