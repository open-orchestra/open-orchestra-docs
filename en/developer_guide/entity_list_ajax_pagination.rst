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

The different variables used to filter (pagination, search, ordering) the data
are described in this `documentation`_.

In order to make the pagination operational, the api should return a facade filled with 4 parameters:
 * recordsTotal: Total number of entities
 * recordsFiltered: Number of entities matching the filters (search)
 * collectionName: The name of variable which contains the data
   (for instance if collectionName equals ``contents`` then the data will be in the variable ``$contents``)
 * data: The data to be displayed in the table. This is an array who contains your data (facade entity)
   after filtering (search, order, pagination)

For instance, here comes the json returned by the api for listing the workflow functions:

.. code-block:: JavaScript

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

.. _`DataTables`: https://www.datatables.net/
.. _`documentation`: https://www.datatables.net/manual/server-side#Sent-parameters