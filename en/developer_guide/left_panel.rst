Left panel
==========

Context
-------

The left panel containing the navigation menu is fully configurable by adding specific services to the application.
Open Orchestra natively provides different kind of strategies for this panel that are reusable for you own entries.

Usage
-----

Create the strategy
~~~~~~~~~~~~~~~~~~~

Each panel entry is a service implementing the interface ``OpenOrchestra\Backoffice\LeftPanel\LeftPanelInterface``.
Different strategies are already available in the folder ``OpenOrchestra\Backoffice\LeftPanel\Strategies`` and can be reused for most common needs in panel services.

For the service to be recognised as a menu entry, it should be tagged with ``open_orchestra_backoffice.left_panel.strategy``:

.. code-block:: yaml

    tags:
        - { name: open_orchestra_backoffice.left_panel.strategy }

Display of the menu
~~~~~~~~~~~~~~~~~~~

The display of the menu item is managed by the method ``LeftpanelInterface::show()`` which should return an HTML string.

The menu link should have the following attributes :

* href : an anchor defining the route for Backbone.js, it will be displayed in the browser's address bar
* id : merge of the "nav-" string and the name of the strategy as returned by ``LeftpanelInterface::getName()``, for instance "nav-user"
* data-url : API url to be called to retrieve the data to be displayed when clicking the menu

Specifics
---------

It is possible to modifiy the order of the items in the panel by changing the return value of the ``LeftpanelInterface::getWeight()`` method.
The heaviest elements are displayed below the other ones.

The ``LeftpanelInterface::getParent()`` method allows an item to have a parent item in order to define a hierarchy of elements.
The root of the panel is an ``administration`` node so all top level items should have it as a parent.

Restricting access to a menu element is done by defining a specific role the user should possess inside ``LeftpanelInterface::getRole()``.
