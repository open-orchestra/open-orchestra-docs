Block creation
==============

The block system
----------------

In Open Orchestra, pages are made of blocks representing data to display.

In order for them to be easily manageable, each block comes with a set of strategies defined as services:

- A display strategy for the frontoffice
- A display strategy for the backoffice
- An icon and title display strategy, visible in the backoffice
- A strategy for displaying the form fields when editing the block in the backoffice

These strategies are identified by the usage of specific tags when declaring the service.

The different strategies
------------------------

Display strategies
~~~~~~~~~~~~~~~~~~

For the display of a block (whether on the frontoffice or backoffice), the tag to use is ``open_orchestra_display.display_block.strategy``:

.. code-block:: yaml

    tags:
        - { name: open_orchestra_display.display_block.strategy }

It also needs to implement ``OpenOrchestra\DisplayBundle\DisplayBlock\DisplayBlockInterface``

Strategies for the icon
~~~~~~~~~~~~~~~~~~~~~~~

For the display of the block icon, the tag to use is ``open_orchestra_backoffice.display_icon.strategy``:

.. code-block:: yaml

    tags:
        - { name: open_orchestra_backoffice.display_icon.strategy }

It also needs to implement ``OpenOrchestra\BackofficeBundle\DisplayIcon\DisplayInterface``

Strategies for the form
~~~~~~~~~~~~~~~~~~~~~~~

For the display of the block form, the tag to use is ``open_orchestra_backoffice.generate_form.strategy``:

.. code-block:: yaml

    tags:
        - { name: open_orchestra_backoffice.generate_form.strategy }

It also needs to implement ``OpenOrchestra\Backoffice\GenerateForm\GenerateFormInterface``

Generating blocks in command line
---------------------------------

In order to easily create blocks, Open Orchestra has a Symfony command available named ``orchestra:generate:block``.

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
In the FrontOffice application, each block is rendered in an ESI block using the render_esi() twig function.

See also `ESI blocks`_.

.. _ESI blocks: /en/developer_guide/esi.rst
