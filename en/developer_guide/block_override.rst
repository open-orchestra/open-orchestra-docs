Block Override
==============

Context
-------

From time to time, the block provided by Open Orchestra will fulfill some of your requirements
but you would want to modify a little part of their behaviour.

As the block is partially functional, you do not want to create an other block with the functionality.

We provide you different ways to override part of the Open Orchestra block which depends on
your use case :

- If you want to modify only the block display, `override the template of a block`_
- If you want to modify the logic of the block, `override the service`_
- If you want to modify the whole service, `override the full block`_

.. _override the template of a block:

Override the template of a block
--------------------------------

Overloading the template of a block is achieved by creating a template in the following folder structure :

.. code-block::

    |_ app
        |_ Resources
            |_ {BUNDLE_NAME}
                |_ views
                    |_ {PATH_TEMPLATE}
                        |_ {FILENAME}


Example :
~~~~~~~~~

You need to override the template of the Content List Block block from the Back Office to display
additional datas.

.. code-block::

    |_ Open-orchestra
        |_ open-orchestra-cms-bundle
            |_ BackofficeBundle
                |_ Ressources
                    |_ views
                        |_ Block
                            |_ ContentList
                                |_ show.html.twig

``Open-orchestra/open-orchestra-cms-bundle/BackofficeBundle/Ressources/views/Block/
ContentList/show.html.twig``

You simply create your template in next folder:

.. code-block::

    |_ app
        |_ Resources
            |_ OpenOrchestraBackofficeBundle
                |_ views
                    |_ Block
                        |_ ContentList
                            |_ show.html.twig

``app/Ressources/OpenOrchestraBackofficeBundle/views/Block/ContentList/show.html.twig``

See again `symfony2 documentation`_

Override directly a block
-------------------------

As an introduction to this part, being familiar with the `block parameter`_ documentation page is
a requirement.

Open Orchestra gives you two ways to override a block.

.. _override the service:

Override the service
~~~~~~~~~~~~~~~~~~~~

You can directly replace a block by overloading its service.
All open-orchestra blocks have their referenced class in the parameters from config file.

.. code-block:: yaml

    # open-orchestra-cms-bundle/BackofficeBundle/Ressources/config/display.yml
    parameters:
        open_orchestra_backoffice.display.content_list.class: OpenOrchestra\BackofficeBundle\DisplayBlock\Strategies\ContentListStrategy
        open_orchestra_backoffice.display.content.class: OpenOrchestra\BackofficeBundle\DisplayBlock\Strategies\ContentStrategy

It's thus possible for you to override these parameters and thus overload the class from service.

.. code-block:: yaml

    parameters:
        open_orchestra_backoffice.display.content_list.class: Foo\ExampleBundle\Blocks\Strategies\ContentListStrategy

This method won't give you the opportunity to change the class constructor and all the dependancy
injected to the block.

.. _override the full block:

Override the full block
~~~~~~~~~~~~~~~~~~~~~~~

To override an existing block by its name, you have to add your block in the services form config file.
Don't forget the tag in your declaration.

.. code-block:: yaml

    services:
        itkg.display.content_list:
            class: %itkg.display.content_list.class%
            tags:
                - { name: open_orchestra_backoffice.display_block.strategy }

Finally, the getName method must return the same name as the overloaded block.

.. code-block:: php

    public function getName()
    {
        return "block_name";
    }

This method will give you the opportunity to totaly redifine the block, from the dependency needed
to the working logic and the template used.

.. _`block parameter`: /en/developer_guide/block_parameter.rst
.. _`symfony2 documentation`: http://symfony.com/doc/current/cookbook/controller/error_pages.html
