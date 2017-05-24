Elasticsearch add new indexed document
======================================

General note
------------

To use this documentation, you should already have installed `Elasticsearch`_ on your
environment.

This documentation describes how to create the schema, and how to populate the index of
the new document.

Schema creation
---------------

To generate the schema of your document, you need to create an initializer that implements
``ElasticaSchemaInitializer``.

This initializer should be tagged with :

.. code-block:: yaml

    tags:
        - { name: open_orchestra_elastica.schema_initializer.strategy }

All initializers are called by the console command ``orchestra:elastica:schema:create``.

This initializer can call a schema generator class that should implement
``DocumentToElasticaSchemaGeneratorInterface``.

Index population
----------------

To populate the index with your document data, there are two possible actions :

* Populate the index from the data of you database
* Modify the index each time one of your document is modified

Populate from the database
``````````````````````````

To populate the index from the database, you need to create a populator that implements
``ElasticaPopulatorInterface``.

This populator should be tagged with :

.. code-block:: yaml

    tags:
        - { name: open_orchestra_elastica.populator.strategy}

This populator queries all the documents that you want to index from the database. This
service should call a indexor which implement ``MultipleDocumentIndexorInterface``.

All populators are called when you run the ``orchestra:elastica:populate`` command.

The indexor gets an array of documents, transforms them into elastica document
and send the indexed document to the database.
The indexor should call a transformer which implement ``ModelToElasticaTransformerInterface``.

The transformer gets a document and output an elastica document.

Modify the index
````````````````

Create or update a document
'''''''''''''''''''''''''''

When a document is created or modified, you should listen to the ``DocumentEvents::CREATE``
or ``DocumentEvents::UPDATE`` events.

The listener should call an indexor that implements ``DocumentIndexorInterface``

The indexor gets the document and index an elastica document. The indexor calls
the transformer that you created in the previous section to perform the transformation.

Delete a document
'''''''''''''''''

When a document is deleted, you should listen to the ``DocumentEvents::DELETE`` event.

The listener should call an indexor that implements ``DocumentDeletorInterface``.

The deletor gets a document and send a delete query to Elasticsearch with the elastica
document. The indexor calls the transformer that you created in the previous section.

.. _`Elasticsearch`: https://www.elastic.co/
