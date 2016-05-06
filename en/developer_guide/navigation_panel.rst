Navigation panel
================

Context
-------

The navigation panel containing the navigation menu is fully configurable by adding specific services
to the application. Open Orchestra natively provides different kind of strategies for this panel that
are reusable for you own entries.

.. image:: ../../images/navigation_panel.png

Usage
-----

Create the strategy
~~~~~~~~~~~~~~~~~~~

Each panel entry is a service implementing the interface
``OpenOrchestra\Backoffice\NavigationPanel\NavigationPanelInterface``. Different strategies are already
available in the folder ``OpenOrchestra\Backoffice\NavigationPanel\Strategies`` and can be reused for
most common needs in panel services.

For the service to be recognised as a menu entry, it should be tagged with
``open_orchestra_backoffice.navigation_panel.strategy``:

.. code-block:: yaml

    tags:
        - { name: open_orchestra_backoffice.navigation_panel.strategy }

Display of the menu
~~~~~~~~~~~~~~~~~~~

The display of the menu item is managed by the method ``NavigationPanelInterface::show()`` which should
return an HTML string.

The menu link must have the following attributes :

* href : an anchor defining the route for Backbone.js, it will be displayed in the browser's address bar
* id : merge of the "nav-" string and the name of the strategy as returned by
  ``NavigationPanelInterface::getName()``, for instance "nav-user"

Menu and data table
~~~~~~~~~~~~~~~~~~~

Many panel entries allow to consult records formated in a data table view based on `DataTables library`_..
This library allows multiple configurations to custom these tables: name of the column, visible or not by default, search fields...
OpenOrchestra uses its own process to manage these configurations.

First of all, a yaml file describes the settings of each column for a given data table.

Settings available:

* **name**: *(string)* field name
* **title**: *(string)* key of title translation
* **visible**: *(boolean)* Enable or disable the display of column
* **activateColvis**: *(boolean)* Enable or disable the toggle of column in colvis button
* **searchable**: *(boolean)* Enable or disable the search of column
* **searchField**: *(string)* type of search field, further information in `Entity list`_ documentation
* **orderable**: *(boolean)* Enable or disable the order of column
* **orderDirection**: *(string)* asc|desc Indicate the order direction if orderable option is enable

Here is an example of yml data table configuration (datatable_parameter.yml):

.. code-block:: yaml

    open_orchestra_backoffice.navigation_panel.trashcan.parameters :
        -
          name : name
          title : open_orchestra_backoffice.table.trashcan.name
          visible : true
          activateColvis : true
          searchField : text
        -
          name : deleted_at
          updated_by : name
          title : open_orchestra_backoffice.table.trashcan.deleted_at
          visible : true
          activateColvis : true
          searchField : date

Then, this configuration parameter, ``open_orchestra_backoffice.navigation_panel.trashcan.parameters``, is injected to the panel strategy.
Here is the service configuration:

.. code-block:: yaml

    open_orchestra_backoffice.navigation_panel.trashcan:
        class: "%open_orchestra_backoffice.navigation_panel.administration.class%"
        arguments:
            - trashcan
            - ROLE_ACCESS_DELETED
            - 250
            - "%open_orchestra_backoffice.navigation_panel.menu.editorial%"
            - "%open_orchestra_backoffice.navigation_panel.trashcan.parameters%"
            - "@translator"
        calls:
            - [ setTemplate, [OpenOrchestraBackofficeBundle:BackOffice:Include/NavigationPanel/Menu/Editorial/trashcan.html.twig] ]
        tags:
            - { name: open_orchestra_backoffice.navigation_panel.strategy }

As a remark, the Symfony translator is also injected. It will try to translate  each value from the column settings. 
In this case ``open_orchestra_backoffice.table.trashcan.name`` will be translated.

Finally a client side call to the method ``datatableParameterAction``
of the controller ``OpenOrchestra\ApiBundle\Controller\DataTableController`` allows to retrieve all these settings.
which are stored in a global js object ``dataTableConfigurator``.

Each panel strategy called by the controller returns its settings in an associative array.
The keys of each panel strategy array have two purposes :

* allow merging in controller without conflict,
* serve as a search key on client side.

Indeed, by setting ``data-datatable-parameter-name``, each entry in panel indicates where to find its configuration in ``dataTableConfigurator``. 
In the common case, the name of the strategy is used.

In the previous example, the ``open_orchestra_backoffice.navigation_panel.trashcan`` panel strategy serves the controller the settings
by associating them to the name of the strategy: ``trashcan``.
On client side, settings are founded in ``dataTableConfigurator`` at the key ``trashcan`` specified by ``data-datatable-parameter-name``.    

Define Backbone route
~~~~~~~~~~~~~~~~~~~~~

When clicking on the menu element, the Backbone route matching with href attribute value will be executed.
To learn more about the way to define a new Backbone route, see `Backbone routing in Open Orchestra`_.

Specifics
---------

Order the menus
~~~~~~~~~~~~~~~

It is possible to modify the order of the items in the panel by changing the return value of the
``NavigationPanelInterface::getWeight()`` method. The heaviest elements are displayed below the other ones.

The ``NavigationPanelInterface::getParent()`` method allows an item to have a parent item in order to define
a hierarchy of elements. The root of the panel is an ``administration`` node so all top level items should
have it as a parent.

Access restriction
~~~~~~~~~~~~~~~~~~

Restricting access to a menu element is done by defining a specific role the user should possess inside
``NavigationPanelInterface::getRole()``.

To be allowed to configure the role in the Back Office ( by adding it to a `group`_ ), you will need to add the
role to the ``RoleCollector`` class.

You will need to create a `compiler pass`_ to add the role to the ``RoleCollector`` definition in the ``kernel``.
The ``BackofficeBundle`` already provides the ``AbstractRoleCompilerPass`` which will simplify the process.

Let's say that in the ``FooBundle`` you would like to add the ``ROLE_BAR``.

First create the ``RoleCompilerPass`` in the ``DependencyInjection\Compiler`` folder of your bundle :

.. code-block:: php

    <?php

    namespace OpenOrchestra\FooBundle\DependencyInjection\Compiler;

    use OpenOrchestra\BackofficeBundle\DependencyInjection\Compiler\AbstractRoleCompilerPass;
    use Symfony\Component\DependencyInjection\ContainerBuilder;

    /**
     * Class RoleCompilerPass
     */
    class RoleCompilerPass extends AbstractRoleCompilerPass
    {
        /**
         * You can modify the container here before it is dumped to PHP code.
         *
         * @param ContainerBuilder $container
         *
         * @api
         */
        public function process(ContainerBuilder $container)
        {
            $this->addRoles($container, array(
                'ROLE_BAR',
            ));
        }
    }

Then declare the compiler pass in the bundle creation file ``OpenOrchestraFooBundle`` :

.. code-block:: php

    <?php

    namespace OpenOrchestra\FooBundle;

    use OpenOrchestra\FooBundle\DependencyInjection\Compiler\RoleCompilerPass;
    use Symfony\Component\DependencyInjection\ContainerBuilder;
    use Symfony\Component\HttpKernel\Bundle\Bundle;

    /**
     * Class OpenOrchestraFooBundle
     */
    class OpenOrchestraFooBundle extends Bundle
    {
        /**
         * @param ContainerBuilder $container
         */
        public function build(ContainerBuilder $container)
        {
            parent::build($container);
            $container->addCompilerPass(new RoleCompilerPass());
        }
    }

After clearing the cache, you will see the role ``ROLE_BAR`` displayed in the role list in the ``Group``
modification form.

Finally, you can add some translation on the role. To separate the role translations from the rest of the
application, we use the ``role`` domain. This way, you will have to add the translation in the
``role.en.yml`` file (for the ``en`` locale).

.. _`group`: /en/latest/user_guide/user.html
.. _`compiler pass`: http://symfony.com/doc/current/cookbook/service_container/compiler_passes.html
.. _`Backbone routing in Open Orchestra`: /en/latest/developer_guide/backbone_routing.html
.. _`Entity list`: /en/latest/developer_guide/entity_list_ajax_pagination.html
.. _`DataTables library`: https://www.datatables.net/
