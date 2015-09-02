Using other database type
=========================

Context
-------

Open orchestra uses by default a MongoDB database. If you want to use another type of database like
SQL, you will need to tune some settings and to replace some files.

Configuration: object manager
-----------------------------

By default, Open Orchestra uses Doctrine ODM to map database documents to objects. Developers can
define another document manager, the only condition is to implement
``Doctrine\Common\Persistence\ObjectManager``. If the new object manager fits the condition, change
the configuration:

.. code-block:: yaml

  open_orchestra_base_bundle:
      object_manager: namespace/of/objectManager

Override mongo documents and repositories
-----------------------------------------

Some bundles have dependencies to mongoDB. The way to replace them depends on the type of
dependencies.

Complete replacement of the package
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The ``open-orchestra-model-bundle`` and ``open-orchestra-base-api-mongo-model-bundle`` have mongo
dependencies and need to be replaced by your packages.

Bundle replacement
~~~~~~~~~~~~~~~~~~

Some bundles included in Open Orchestra packages are model bundle developped for mongoDB. To use
another database, these bundles must not be activated in the ``appKernel`` and must be replaced by
yours. These are:

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
