Dashboard widgets
=================

The Back Office dashboard is the place to show to the user information concerning him. It's like a
blackoard on which are pinned post-it. Each post-it is a widget. Open Orchestra comes with four
widgets:

* My 10 latest published nodes
* My 10 latest nodes
* My 10 latest published contents
* My 10 latest contents

As a developer, you can customize your application dashboard by choosing widgets and/or create new
ones. Here is how to do.

Configuring the dashboard
-------------------------
To choose the widgets to display in the dashboard, add a key ``open_orchestra_backoffice.dashboard_widgets``
to your app configuration. Then set the list of widgets you want to use. Here is an exemple in yaml
format showing the 4 standard widgets:

.. code-block:: yaml

    open_orchestra_backoffice:
        dashboard_widgets:
            - last_nodes
            - draft_nodes
            - last_contents
            - draft_contents

Creating a widget
-----------------
To build a new widget, you only have to create its Backbone view and register it in Open Orchestra.

Creating a backbone view
~~~~~~~~~~~~~~~~~~~~~~~~
As the Back Office is build with ``BackboneJs``, all widgets are Backbone views added to the main
view from scratch or extend one of the pseudo-abstract layers used by the standard Open Orchestra
widgets. To get some examples, you can take a look at the files located in
``BackOfficeBundle/Ressources/public/coffee/dashboard/widget``

Your widget html can be anything, but we suggest you to use the jarvis widget template to have a
visual uniformity in the dashboard. This template can be found in
``BackOfficeBundle/Ressources/views/BackOffice/Underscore/dashboard/widget/abstract/abstractWidgetListView._tpl.twig``

Declaring the view
~~~~~~~~~~~~~~~~~~
To make your newly created widget available in Open Orchestra, you need to add it to the
``appConfigurationView``. This object is used in the Back Office to list all backbone views and
access them when required. To add your view to the configurator, use something like this:

.. code-block:: javascript

    jQuery(function() {
      return appConfigurationView.setConfiguration(
        'dashboard_widgets',
        'my_widget_name',
        'my_widget_backbone_view'
      );
    });

where ``my_widget_name`` is the widget key to use in the configuration and ``my_widget_backbone_view``
is the Backbone view you have just created. That done, your widget is ready to be added to your app
configuration.
