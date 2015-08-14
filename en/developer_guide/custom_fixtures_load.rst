Custom fixtures load
====================

Context
-------

Open Orchestra comes with a set of fixtures that will allow you to have a full overview of the project.
Those fixtures contains some pages, content, media, and much more.

If you want to have just the base data which would allow you to login on the Back Office and start
creating your first pages, a simple solution would be to load only the fixtures you need.

You could do it by adding some paths as command arguments :

.. code-block:: shell

    $ php app/console doctrine:mongo:fixture:load --fixtures="src" --fixtures="vendor/open-orchestra/"

This solution should be avoided because it wouldn't be functional if the fixtures folder is moving.

Open Orchestra Solution
-----------------------

Common usage
~~~~~~~~~~~~

Open Orchestra provides a console command which allows you to load only the fixtures you need.

.. code-block:: shell

    $ php app/console orchestra:mongo:fixtures:load

This command will look through all the project fixtures and load only those implementing
a specific interface :

.. code-block:: php

    use OpenOrchestra\ModelInterface\DataFixtures\OrchestraProductionFixturesInterface;

    /**
     * Class LoadStatusData
     */
    class LoadStatusData extends AbstractFixture implements OrderedFixtureInterface, OrchestraProductionFixturesInterface {}

Specific usage
~~~~~~~~~~~~~~

The previous solution allows you to load only the fixtures needed to get logged on the Back Office.

If you want to load only some fixtures specific to your project, the ``orchestra:mongo:fixtures:load``
can also be used.

First your fixtures file should implement a specific interface (defined in your project):

.. code-block:: php

    use FooBundle\Loader\BarFixtureInterface;

    class LoadFooData implements BarFixtureInterface {}

Then you should configure the ``ModelBundle`` to load only the fixtures implementing the ``BarFixtureInterface``.

.. code-block:: yaml

    open_orchestra_model:
        production_fixtures_interface:
            - FooBundle\Loader\BarFixtureInterface

If you want to load the base production fixtures and your personal fixtures, you can add both interfaces in
the configuration:

.. code-block:: yaml

    open_orchestra_model:
        production_fixtures_interface:
            - OpenOrchestra\ModelInterface\DataFixtures\OrchestraProductionFixturesInterface
            - FooBundle\Loader\BarFixtureInterface
