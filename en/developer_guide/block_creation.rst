Block creation
==============

The block system
----------------

In Open Orchestra, pages are made of blocks representing data to display.

In order for them to be easily manageable, each block comes with a set of display strategies defined
as services:

- A display strategy for the Back Office. This strategy is used to render the block when editing a
  node
  including that type of block
- An icon and title display strategy, visible in the Back Office, in the blocks panel of node pages
- A strategy for displaying the form to edit the block in the Back Office
- A display strategy for the Front Office

These strategies are identified by the usage of specific tags when declaring the service.

The different strategies
------------------------

Back Office display strategies
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Services used as Back Office block display strategies, must be taggued as ``open_orchestra_backoffice.display_block.strategy``:

.. code-block:: yaml

    tags:
        - { name: open_orchestra_backoffice.display_block.strategy }

Those services also need to implement ``OpenOrchestra\DisplayBundle\DisplayBlock\DisplayBlockInterface``

Strategies for the icon
~~~~~~~~~~~~~~~~~~~~~~~

Services used as block icon display strategies must be taggued as ``open_orchestra_backoffice.display_icon.strategy``:

.. code-block:: yaml

    tags:
        - { name: open_orchestra_backoffice.display_icon.strategy }

Such services also need to implement ``OpenOrchestra\BackofficeBundle\DisplayIcon\DisplayInterface``

Strategies for the form
~~~~~~~~~~~~~~~~~~~~~~~

Services used as block form display strategies must be tagged as ``open_orchestra_backoffice.generate_form.strategy``:

.. code-block:: yaml

    tags:
        - { name: open_orchestra_backoffice.generate_form.strategy }

They also need to implement ``OpenOrchestra\Backoffice\GenerateForm\GenerateFormInterface``

Front Office display strategies
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Services used as Front Office block display strategies, must be taggued as ``open_orchestra_display.display_block.strategy``:

.. code-block:: yaml

    tags:
        - { name: open_orchestra_display.display_block.strategy }

Those services also need to implement ``OpenOrchestra\DisplayBundle\DisplayBlock\DisplayBlockInterface``

Generating blocks in command line
---------------------------------

In order to easily create blocks, Open Orchestra offers a Symfony console command named ``orchestra:generate:block``.

The usage is pretty straightforward :

.. code-block:: bash

    $ php app/console orchestra:generate:block
        --block-name="TestBlock"
        --form-generator-dir="src/YourVendor/AcmeBundle/Path/To/Form/Strategies"
        --front-display-dir="src/YourVendor/AcmeBundle/Path/To/Front/Display/Strategies"
        --backoffice-icon-dir="src/YourVendor/AcmeBundle/Path/To/Icon/Strategies"
        --backoffice-display-dir="src/YourVendor/AcmeBundle/Path/To/Back/Display/Strategies"
        --no-interaction

Cache control
-------------

Open Orchestra leverages the power of ESI blocks to optimize page rendering and increase performance.
In the Front Office application, each block is rendered in an ESI block using the render_esi() twig function.

See also `ESI blocks`_.

.. _ESI blocks: /en/developer_guide/esi.rst
