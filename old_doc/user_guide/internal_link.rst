Internal Link
=============

Open Orchestra use TinyMce to edit rich text.
A custom button is used to add an internal link, ie a link to a page managed by the Back Office.
.. image:: ../../images/tiny_internal_link.png

This button opens a modal with a form to construct the internal link:
.. image:: ../../images/form_internal_link.png

The form contains :

* Label: the label for the link displayed in Front Office
* Pages: the target of the link
* Content: as specified in the `contents display documentation`_, content blocks need content id in the url. If the target of the link contains such a block, you can choose the id with this sub form. To simplify the choice of the id, the content form contains search filters as content type and keywords (see `boolean expression`_). A refresh button shows the filtered contents.
* Site: The site target of the link as Open Orchestra is multi-site. The site aliases of the choosen site could be seen by clicking the refresh button and one could be specified.
* Query string: optional parameters definition (param0=value0&param1=value1&param2=value2)

.. _contents display documentation: ./content_display.html
.. _boolean expression: ./boolean_expression.html