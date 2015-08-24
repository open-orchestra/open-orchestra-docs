Using other database type
=========================

Context
-------

Open orchestra uses by default a MongoDb database. If you want to use another type of database like SQL,
you need to do some work for now.

Change object manager in configuration
--------------------------------------

By default, open orchestra uses Doctrine ODM to manage objects. Developers can define another document manager implementing
``Doctrine\Common\Persistence\ObjectManager`` with a change in configuration

.. code-block:: yaml

  open_orchestra_base_bundle:
      object_manager: namespace/of/objectManager

Override mongo documents and repositories
-----------------------------------------

Some bundles have dependencies to mongo. To replace them, there is several solutions depending of the type of dependencies.

Some packages need to be completely replaced
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The ``open-orchestra-model-bundle`` and ``open-orchestra-base-api-mongo-model-bundle`` have mongo
dependencies and need to be replaced by your packages.

Some bundles in the package need to be replaced
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Some bundles are called with a specific model bundle dependant to mongo in their dependencies. To use
another database, these bundles must not be activated in the ``appKernel`` and replaced by yours.

``open-orchestra-workflow-function-bundle`` :
- ``WorkflowFunctionAdminBundle``
- ``WorkflowFunctionModelBundle``

``open-orchestra-media-bundle``:
- ``MediaModelBundle``

``open-orchestra-cms-bundle``
- ``GroupBundle``
- ``ModelLogBundle``

``open-orchestra-user-bundle``
- ``UserModelBundle``