Contents
========

In Open Orchestra, Contents are grouped by families, a family being described by a Content Type. If "Car"
was a Content Type, "Ford mustang" or "Dodge Viper" could be contents of that type. See `Content Types`_
documentation for more information.


Listing
-------
Contents listing is accessed in the Editorial section, by clicking on the "Contents" link. A submenu
lists all Content Types available.

.. image:: ../../images/content_list_submenu.png

By clicking a Content Type, the list of related contents appears.

.. image:: ../../images/content_list.png

This list has a pagination and filters, and shows the name, the status, the version and the language
of existing contents. From this list, new content can be created, and existing ones can be edited or
deleted.


Creation
--------
From the content list, creation form can be accessed by clicking on the "Add" button. The form will be
related on the Content Type concerned. By saving the content is created, with the version number 1 and
the initial status of the workflow.


Edition
-------
From the content list, clicking on an "Edit" button makes an edit form appear. The edit form is mainly
the same as the creation form, completed with current values, but has three more functionalities.

.. image:: ../../images/content_edit.png

* **Status**: The status button allows you to change the workflow status of the content (See the `workflow`_
documentation for more information)

* **Translations**: the language tabs allow you to create/edit the content in alternative languages

* **Versioning**: The version selector allows you to edit a previous version of the content in the
selected language. The "New version" button will duplicate the last version of the content in the
selected language to create a new version.

**Saving the modifications does not create a new version or change the status. Those operations have
to be done individually.**


Front display
-------------

The contents are not directly accessible in Front Office. Like everything visible in Front Office, the contents
are displayed through blocks. See the documentation on the `Contents display`_ for more information about it.


.. _Content Types: ./content_types.rst
.. _workflow:
.. _Contents display: ./content_display.rst
