Backbone specific view
======================

Context
-------

In the Open Orchestra Back Office, to display an edition form, there are two parts :

* The Twig template given by the server
* The Backbone view which handle all the javascript events

In some cases, during the integration of the Open Orchestra Back Office, the generic view used for the
edition page will not suit your needs. There are some new behaviour to add to the form, such as a
specific event when you edit a field.

There are two simple solutions to avoid :

* Add some javascript in the form template
* Add a global listener to the javascript project

Both of these solutions are to avoid because :

* They couple the template and the javascript
* They may be checked each time the DOM is modified

To prevent these usage, Open Orchestra provide a way to modify the view used in Backbone.

Usage
-----

As all the CRUD are based on an ``entityType``, you will have the possibility to add a view for the
``edit`` and ``add`` action on this ``entityType``.

.. code-block:: js

    appConfigurationView.setConfiguration(entityType, action, view)

The ``view`` parameter should be the reference to your specific view. For instance :

.. code-block:: js

    appConfiguration.setConfiguration('group', 'edit', SpecificFullPageFormView)

For the content, the ``entityType`` parameter will have a different value for each content type :

.. code-block:: js

    entityType = 'contents_news'; //will be the value for the news content type

For the content, the ``entityType`` will be composed of the content type news and the ``contents`` string.
``contents_news`` will be the one for the news content.
