Prevent document suppression when they are embedded
===================================================

Context
-------

In a document oriented database (like Mongo), to improve performances, a standard practice is to avoid relations
between documents using embed documents. However, when you want to suppress a document that is used by other
documents a little issue can appear.

In our case, the Open Orchestra Backoffice presents some status that can be used in multiple
documents like the ``Node``, ``Content``, ``Role``, ... . Deleting a ``Status`` document could lead
to a loss of consistence from the database.

Open Orchestra implementation example
-------------------------------------

In Open Orchestra, if you look to the ``DeleteStatusVoter`` you will see it using the
``StatusUsageFinder`` to check if the ``Status`` can be deleted.

If you add a document implementing ``StatusableInterface`` :

- Your document repository should implement ``StatusableElementRepositoryInterface``
- You should add your repository to the ``StatusUsageFinder`` service

Implement the interface
~~~~~~~~~~~~~~~~~~~~~~~

In the ``NodeRepository`` class, the interface implements the ``StatusableElementRepositoryInterface`` :

.. code-block:: php

    interface NodeRepositoryInterface extends StatusableElementRepositoryInterface

And the repository implement the method :

.. code-block:: php

    public function hasStatusedElement(StatusInterface $status)
    {
        $node = $this->findOneBy(array('status' => $status));
        return $node instanceof NodeInterface;
    }

Modify the configuration
~~~~~~~~~~~~~~~~~~~~~~~~

To add your repository, ``foo.repository.bar`` in our example, you should modify the usage finder
definition in your bundle :

.. code-block:: php

    class FooBarExtension extends Extension
    {
        public function load(array $configs, ContainerBuilder $container)
        {
            $definition = $container->getDefinition('open_orchestra_backoffice.usage_finder.status')
            $definition->addMethodCall('addRepository', array(new Reference('foo.repository.bar')));
        }
    }

With this modification, each time the ``StatusUsageFinder`` is called, it will also check
in your own repository if the given status is used.