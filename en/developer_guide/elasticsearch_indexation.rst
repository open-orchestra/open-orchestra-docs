Elasticsearch indexation
========================

General note
------------

This documentation describes the provisionning modification for the ``vagrant`` environment. All the modifications
could be done on all the different environments.

Elasticsearch
-------------

`Elasticsearch`_ is a common indexor based on the `lucene`_ engine written in Java. To install it on the
computer running the application, you should add the ``indexation`` group to the file
``provisioning/hosts/vagrant`` :

.. code-block:: none

    [indexation]
    admin.openorchestra.1-1.dev

You should also add some configuration to the ``provisioning/hosts/group_vars/vagrant`` file:

.. code-block:: yaml

    elasticsearch_version: 1.4
    elasticsearch_config:
      network.bind_host: 192.168.33.10
      network.host: 192.168.33.10
      network.publish_host: 192.168.33.10
      http.bind_host: 192.168.33.10
      http.host: 192.168.33.10
      http.publish_host: 192.168.33.10
    elasticsearch_plugins:
      - name: mobz/elasticsearch-head
        check_file: /usr/share/elasticsearch/plugins/head/index.html

This way, `Elasticsearch`_ will be binded to the public ip of the vagrant box.

We also recommand you to install the `plugin head`_ which could give you usefull information about the cluster.

Run the provisionning (``vagrant provision``) to install `Elasticsearch`_.

Go on http://192.168.33.10:9200/ to check if it is running properly. You should see ``status: 200`` in
the json response.

Go on http://192.168.33.10:9200/_plugin/head/ to see the `plugin head`_ working.

Elasticsearch and Open Orchestra
--------------------------------

To perform all the indexation in `Elasticsearch`_ an Open Orchestra bundle has been created. It is the
`open-orchestra-elastica-bundle`_.

Add in your ``composer.json`` file :

.. code-block:: javascript

    "open-orchestra/open-orchestra-elastica-bundle": "*"

In the ``app/AppKernel.php`` file :

.. code-block:: php

    new OpenOrchestra\ElasticaBundle\OpenOrchestraElasticaBundle(),

Add the `Elasticsearch`_ listening address in the ``app/config/config.yml`` file :

.. code-block:: yaml

    open_orchestra_elastica:
        host: 192.168.33.10

``192.168.33.10`` is our local configuration, this can vary on your installation.

After running the ``composer update`` command, you should see some new command appear when running
``php app/console`` :

.. code-block:: bash

    $ php app/console | grep orchestra

Those commands are :

.. code-block:: bash

    orchestra:elastica:index:create         Create an index in elastic search
    orchestra:elastica:index:drop           Drop the index in elasticsearch
    orchestra:elastica:populate             Populate the content index with the contents
    orchestra:elastica:schema:create        Load the schema from the content types

Creating the index
~~~~~~~~~~~~~~~~~~

The first time you install `Elasticsearch`_ you can use the command ``orchestra:elastica:index:create``
to create the index.

.. code-block:: bash

    $ php app/console orchestra:elastica:index:create

For more advanced users, you can directly go on `Elasticsearch`_ and create your index with the name ``content``.

There is only an output if there is an error during the process.

Creating the schema
~~~~~~~~~~~~~~~~~~~

Once your index is created, you should create the schema to help `Elasticsearch`_ store and retrieve your datas.

The first time you are using `Elasticsearch`_ on an existing installation, you should use the command :

.. code-block:: bash

    $ php app/console orchestra:elastica:schema:create

During the project lifetime, the schema will be automatically updated each time the ``ContentType`` are updated.

There is only an output if there is an error during the process.

Populating the index
~~~~~~~~~~~~~~~~~~~~

The first time you are using `Elasticsearch`_, you could populate the index with the existing datas, using
the command :

.. code-block:: bash

    $ php app/console orchestra:elastica:populate

During the project lifetime, the indexed data will be automatically updated each time you publish a ``Content``.

There is only an output if there is an error during the process.

.. _`Elasticsearch`: https://www.elastic.co/
.. _`lucene`: https://lucene.apache.org/core/
.. _`plugin head`: https://mobz.github.io/elasticsearch-head/
.. _`open-orchestra-elastica-bundle`: https://packagist.org/packages/open-orchestra/open-orchestra-elastica-bundle
