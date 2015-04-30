API group context
=================

Context
-------

To increase readability and reduce the code duplication in the API, a transformer will only be
linked to one entity and one facade. This way, each time you will transform an entity into
a facade, it will be done using the same parameters. In some case, you do not want to display
all the data from a facade in a certain context.

For instance, when you list all the nodes, the area and blocks might not be usefull.

The ``JMSSerializerBundle`` allows you to hide some properties on the serialization by using
some serialization group. The main issue with this method is that you will still have to
complete all the data in the facade.

We are going to see how we can use the Open Orchestra project to limit the amount of data set
in the facade depending on the context

Usage
-----

In a controller action, you can directly add an annotation :

.. code-block:: php

    /**
     * @Api\Groups({"GROUP_FOO"})
     */
    public function fooAction()

With the requirements :

.. code-block:: php

    use OpenOrchestra\ApiBundle\Controller\Annotation as Api;

Then in the transformer, you can directly call the ``hasGroup`` method :

.. code-block:: php

    $this->hasGroup("GROUP_FOO");

This method will check if the group has been added in the action annotation.
Now you can either choose to set or not some properties in the facade.

Going further
-------------

All groups are stored in the ``open_orchestra_api.context.group`` service. As this service has a scope container
you can modify it in your code by adding a specific group.

.. code-block:: php

    $this->container->get('open_orchestra_api.context.group)->addGroup('GROUP_BAR');

In all the following transformer, you can now check if the ``GROUP_BAR`` is present :

.. code-block:: php

    $this->hasGroup('GROUP_BAR') // true
