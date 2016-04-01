Migration
=========
Open Orchestra offers migration tasks to facilitate the update version.
To know more about migration see `mongodb migration`_.

MongoDB Migration
-----------------

The MongoDBMigrationsBundle come with a set of command available under the name space mongodb:migrations.
These commands will respond according to the settings.

MongoDb Migration settings
~~~~~~~~~~~~~~~~~~~~~~~~~~

To use migration tasks of Open Orchestra, you must configure the bundle with this settings:

.. code-block:: yaml

    mongo_db_migrations:
        collection_name: 'migration_versions'
        database_name: '%open_orchestra_cms.mongodb.database%'
        dir_name: '%kernel.root_dir%/../vendor/open-orchestra/open-orchestra-model-bundle/OpenOrchestra/ModelBundle/Migrations/MongoDB'
        script_dir_name: '%kernel.root_dir%/../vendor/open-orchestra/open-orchestra-model-bundle/OpenOrchestra/ModelBundle/Migrations/MongoDB/scripts'
        name: 'Open Orchestra MongoDB Migrations'
        namespace: 'OpenOrchestra\ModelBundle\Migrations\MongoDB'

MongoDb Migration migrate
~~~~~~~~~~~~~~~~~~~~~~~~~

The command

.. code-block:: bash

    app/console mongodb:migrations:migrate

will execute the different steps of migration.

.. _mongodb migration: https://github.com/antimattr/mongodb-migrations-bundle
