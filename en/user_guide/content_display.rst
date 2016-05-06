Contents display
================

Once contributed, there is only one way to display a content: using content blocks in nodes. Open
Orchestra comes with 3 block types able to render a content, but a developer can create his own block
to match his needs. The three standard Open Orchestra content blocks are:

* Content list block
* Content block
* Configurable content block


Content list block
------------------
This block renders in Front Office a list of contents matching criteria given by the setting of the
block. A typical use case may be the display of short previews for an article list, or a listing of
customers.

Contribution
````````````
Besides the common settings for all blocks, the content list block requires two specific types of
settings:

* Criteria: These are a combination of two basic criteria. The contributor must choose a content
  type and/or keyword(s) to trigger the contents.

* Rendering: The contributor has two ways to render this block. He can use the standard template of
  the content list block or create one in the Back Office to be used in that specific context, i.e.
  only for that block instance in that node.

Using the standard template
'''''''''''''''''''''''''''
To use the standard template, put the template usage on Off.

Using a "one shot" template
'''''''''''''''''''''''''''
To use a new specific and unique template, put the template usage on On, then use the rich text area
below to create the template. You can use the twig syntax. This template will be used only for that
block in that node. Other content list blocks in that node or in others are not been concerned by that
template.


Content block
-------------
The content block renders the content whose id is given in the page address. A typical use is to
create a generic node rendering specific content detailed information. By varying the content id
in the url, the same node can be used to display various articles or customer details.

For instance a node with the pattern /customer/{contentId} would be accessed in Front Office via
url /customer/paul-smith and then the content block would display some information about Paul Smith.
It could also be accessed via url /customer/john-anderson, and then displaying information about John
Anderson.

Contribution
````````````
On this block, like on the content list block, the contributor can use the standard template of the
block or create a specific one for that block/node using the rich text.

**To get this block working, the node url pattern has to be set in a specific way. As the content
id comes from the url, the node pattern must include the string {contentId} or the content id will
not be available**. For more information about this, see `node configuration`_.


Configurable content block
--------------------------
The configurable content block renders a single content, chosen by the contributor.

This block type could be used to create a focus on a specific content somewhere in the page, that
could not be the principal information of the page, such has a mini-block on the last product
developped by the company, or the employee of the month.

Contribution
````````````
To get the block working, the contributor must first choose a content type then choose the content to
display.

.. _node configuration: /en/latest/user_guide/node_configuration.html
