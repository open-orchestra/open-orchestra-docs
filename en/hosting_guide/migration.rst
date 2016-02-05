Migration
=========

To know more about migration see `mongodb migration`_.

MongoDB Migration
-----------------

the MongoDBMigrationsBundle come with a set of command available under the name space mongodb:migrations.
These commands will respond according to the settings.

MongoDb Migration settings
~~~~~~~~~~~~~~~~~~~~~~~~~~

Here are the settings added to config.yml ;

.. code-block:: yaml

    mongo_db_migrations:
        collection_name: "migration_versions"
        database_name: "%open_orchestra_cms.mongodb.database%"
        dir_name: "%kernel.root_dir%/../vendor/open-orchestra/open-orchestra-model-bundle/OpenOrchestra/ModelBundle/Migrations/MongoDB"
        script_dir_name: "%kernel.root_dir%/../vendor/open-orchestra/open-orchestra-model-bundle/OpenOrchestra/ModelBundle/Migrations/MongoDB/scripts"
        name: "Open Orchestra MongoDB Migrations"
        namespace: "OpenOrchestra\\ModelBundle\\Migrations\\MongoDB"

- collection_name: this value indicates what will be the name of the collection used to store the migration information
- database_name: each time the name of the database is needed, this alias is used
- dir_name: as the use of this bundles will result in generation of files, the target is specified
- script_dir_name: same as dir_name, but this indicates where js script are located
- name: arbitrary value used in output
- namespace: this value should be consistent with dir_name

MongoDb Migration generate
~~~~~~~~~~~~~~~~~~~~~~~~~~

The command

.. code-block:: bash

    app/console mongodb:migrations:generate

generates a blank file in dir_name.
This file is characterized by a unique identifier, stored in database, which indicates the order of the file in the migration process.
Actually, OpenOrchestra contains one step : Version20150722104732.

It contains two functions, up to go to this migration step, and down to reverse this step.
The up function of this step will load the stored procedure create_duplicate_node_20150722104732.js in script_dir_name.
The down function will load the stored procedure delete_duplicate_node_20150722104732.js in script_dir_name which erases the stored procedure previously loaded by up function.

MongoDb Migration migrate
~~~~~~~~~~~~~~~~~~~~~~~~~

The command

.. code-block:: bash

    app/console mongodb:migrations:migrate

will execute the different steps of migration, in our case, the up function of Version20150722104732.

.. _mongodb migration: https://github.com/antimattr/mongodb-migrations-bundle
