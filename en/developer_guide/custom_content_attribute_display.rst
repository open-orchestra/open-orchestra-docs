Customize Content Attribute Display
===================================

Context
-------

In Open Orchestra the ``Content`` are composed of a set of base attributes and a collection of
``ContentAttribute`` (See `content`_ documentation for more information). The ``ContentAttribute``
are configured by the `content type`_.
In order to have minimum constraints on contents, Open Orchestra allows you to store any type
of ``value`` in the ``ContentAttribute``.

Sometimes, there is no easy way to render the value to the Back Office user.
A custom ``ContentAttribute`` could be stored as an array, which cannot be displayed directly in the dataTables plugin.
In that way the ``ContentAttribute`` class provides a specific attribute ``stringValue`` which is the
representation of the ``value`` in an HTML string.

Transformers
------------

Open Orchestra uses a ``ValueTransformer`` strategy manager to generate the HTML strings for
multiple ``value`` types. Open Orchestra already provides some strategies located in
``OpenOrchestra\Backoffice\ValueTransformer\Strategies``.

Strategy creation
~~~~~~~~~~~~~~~~~

Service used as ``ValueTransformer`` must be tagged as ``open_orchestra_backoffice.value_transformer.strategy``.

.. code-block:: yaml

    tags:
        - { name: open_orchestra_backoffice.value_transformer.strategy }

Such services also need to implement ``OpenOrchestra\Backoffice\ValueTransformer\ValueTransformerInterface``.

Strategy access
~~~~~~~~~~~~~~~

Open Orchestra uses the ``OpenOrchestra\Backoffice\ValueTransformer\ValueTransformerManager``
as an easy way to access every transformation strategies.
All ``ValueTransformer`` strategies are registered in the ``ValueTransformerManager``.
The ``transform`` method of the manager:

* searches the first transformation strategy supporting the current ``fieldType`` and ``value`` of the ``ContentAttribute``
* uses this strategy's ``transform`` method to return the ``stringValue``

Examples
--------

Transformation available
~~~~~~~~~~~~~~~~~~~~~~~~

+------------------------------+-------------------------------------------+--------------------------------+
| Value                        | StringValue                               | Strategy                       |
+==============================+===========================================+================================+
| "string"                     | "string"                                  | none                           |
+------------------------------+-------------------------------------------+--------------------------------+
| 1                            | "1"                                       | IntegerToHtmlStringTransformer |
+------------------------------+-------------------------------------------+--------------------------------+
| null                         | "none"                                    | NullToHtmlStringTransformer    |
+------------------------------+-------------------------------------------+--------------------------------+
| Object()                     | Object::__toString()                      | ObjectToHtmlStringTransformer  |
+------------------------------+-------------------------------------------+--------------------------------+
| array('foo' => array('bar')) | '<ul><li><ul><li>bar</li></ul></li></ul>' | ArrayToHtmlStringTransformer   |
+------------------------------+-------------------------------------------+--------------------------------+

New transformation
~~~~~~~~~~~~~~~~~~

Let's say that the field with the type ``foo`` will store relation to the ``FooDocument``. You will need to add
a transformer in order to create a ``stringValue`` that could be displayed on the Back office. In our example
the ``bar`` properties should be displayed.

You need to implement the three methods of the interface :

 * ``getName`` : give the name of the transformer
 * ``support`` : take the ``fieldType`` and the ``value`` to decide if the transformation should be applied
 * ``transform`` : will transform the value

In our case, the support method will check the field type and if the value is null or not.

.. code-block:: php

    public function support($fieldType, $value)
    {
        return $fieldType == 'foo' && $value != null;
    }

The transform method will need the ``fooDocument`` repository to find the document then will return the ``bar``
properties.

.. code-block:: php

    /**
     * $value = mongoId;
     */
    public function transform($value)
    {
        $fooDocument = $this->fooRepository->find($value);

        return $fooDocument->getBar();
    }

.. _`content type`: /en/latest/user_guide/content_type.rst
.. _`content`: /en/latest/user_guide/content.rst
