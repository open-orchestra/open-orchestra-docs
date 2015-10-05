Block parameter
===============

Context
-------

For their display to be customizable, some blocks need to receive parameters when being rendered.
Those parameters could be of multiple types, for instance :

- url parameters
- server parameters
- header parameters
- ...

A simple solution to give those parameters to the block would have been to give all the request
parameters when the block is called.

This solution is not optimal for a main reason: when loading blocks via `ESI`_, each
block will be cached for each url variant.

In this example, the block 1, which does not require any parameters, will be cached for each url variant :

- ``/block/1`` will be in one cache entry.
- ``/block/1?foo=bar`` will be in another cache entry.

To improve your cache hit ratio, you should have the least entries for a given page.

Open Orchestra solution
-----------------------

Open Orchestra lets you specify the parameters to give to a block in order to limit the cache
entries for a single block.

This solution requires to work in two specifics areas :
- in the Back Office, where you add the block
- in the Front Office, where you will require some parameters linked to the block.

Back Office work
~~~~~~~~~~~~~~~~

When a block is added in an area of a node, a block reference is created to link the block and the area.
That block reference contains the parameter types required to display the block in Front Office.

You need to create a service implementing the interface
``OpenOrchestra\Backoffice\BlockParameter\BlockParameterInterface``.

In this interface, the method ``getBlockParameter`` returns an array of all the parameters needed by the block
to work properly.

This service should be declared with the tag ``open_orchestra_backoffice.block_parameter.strategy``

.. code-block:: yaml

    tags:
        - { name: open_orchestra_backoffice.block_parameter.strategy }

Front Office work
~~~~~~~~~~~~~~~~

In the Front Office, the sub-request to display a block (in the main request) is created while you don't
have any idea of the block type. The ``blockParameter`` will help you to complete the sub-request parameters.

To analyze the parameters and complete the request, you need to create a service implementing the
interface ``OpenOrchestra\FrontBundle\SubQuery\SubQueryGeneratorInterface``

This service should be declared with the tag ``open_orchestra_front.sub_query.strategy``

.. code-block:: yaml

    tags:
        - { name: open_orchestra_front.sub_query.strategy }

Example
-------

Subquery strategies available
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Open Orchestra comes with a few strategies already defined. *All those strategies
can be cumulated for a single block.*

+----------------------------------+------------------------------------------------------------+
| Name                             | Action                                                     |
+==================================+============================================================+
| ``DeviceSubQueryStrategy``       | Pass the header parameter ``x-ua-device``                  |
+----------------------------------+------------------------------------------------------------+
| ``PostDataSubQueryStrategy``     | Pass all data from the ``POST`` part                       |
+----------------------------------+------------------------------------------------------------+
| ``RequestSubQueryStrategy``      | Pass the specified request parameter (aliasId for instance |
+----------------------------------+------------------------------------------------------------+
| ``CurrentRouteSubQueryStrategy`` | Pass the current route to the block                        |
+----------------------------------+------------------------------------------------------------+

New Subquery Strategy
~~~~~~~~~~~~~~~~~~~~~

Let's say that you want to translate the foo parameter from the request and give it to the block.

You need to implement the three methods of the interface :

- ``getName`` : give the name of the strategy
- ``support`` : take the block parameter to decide if the strategy should be used
- ``generate`` : will generate the value

In our case, we will check if the block requires a parameter named ``foo``.

.. code-block:: php

    public function support($blockParameter)
    {
        return strpos($blockParameter, 'foo') === 0;
    }

The generate method will need the ``translator`` service in order to find the translation for the parameter.

.. code-block:: php

    public function generate($blockParameter)
    {
        $fooParameter = $this->request->get('foo');

        return array('foo' => $this->translator->trans($fooParameter);
    }

In the sub-request, the ``foo`` parameter will be added to the request parameters.

.. _`ESI`: /en/developer_guide/esi.rst
