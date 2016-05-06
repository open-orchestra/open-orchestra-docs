API transformer
===============

Context
-------

To decouple the data exposed through the API and the data stored in the model,
Open Orchestra uses the `Facade design pattern`_.

If you want to add a new entity to your project and need to expose it through the API,
an easy way would be to directly serialize the object to render it.

This solution is not ideal for a main reason: the response is going to move each
time you will modify your model.

Open Orchestra solution
-----------------------

Open Orchestra gives you the opportunity to decouple the data exposition from the
data storage.

To simplify this documentation, let's say that we want to expose a ``Foo`` document.

.. code-block:: php

    class Foo
    {
        /**
         * @var string
         */
        public $bar;
    }

Facade
~~~~~~

The facade is the object that will be exposed through the API, let's also say you
need to put the value of ``Foo::bar`` inside a ``baz`` property.

Create the ``FooFacade`` with the ``baz`` property:

.. code-block:: php

    namespace FooBundle\Facade;

    use JMS\Serializer\Annotation as Serializer;
    use OpenOrchestra\BaseApi\Facade\FacadeInterface;

    class FooFacade implements FacadeInterface
    {
        /**
         * @Serializer\Type("string")
         */
        public $baz;
    }

The ``FooFacade`` class should implement the ``FacadeInterface`` to be recognized as
a facade in the rest of the application.

Transformer
~~~~~~~~~~~

As the transformation for the ``bar`` to ``baz`` property is not intuitive, you will
need to create a Transformer to perform the modification.

Create the ``FooTransformer``:

 * It must implement the ``OpenOrchestra\BaseApi\Transformer\TransformerInterface``
 * Be registered as a service with the tag ``open_orchestra_api.transformer.strategy``

.. code-block:: php

    namespace FooBundle\Transformer;

    use OpenOrchestra\BaseApi\Facade\FacadeInterface;
    use OpenOrchestra\BaseApi\Transformer\AbstractTransformer;
    use FooBundle\Facade\FooFacade;

    class FooTransformer extends AbstractTransformer
    {
        public function getName()
        {
            return 'foo';
        }

        public function transform($foo)
        {
            $facade = new FooFacade();
            $facade->baz = $foo->bar;

            return $facade;
        }
    }

And the declaration :

.. code-block:: yaml

    foo.transformer.foo:
        class: FooBundle\Transformer\FooTransformer
        tags:
            - { name: open_orchestra_api.transformer.strategy }

To limit the dependency, Open Orchestra provides a ``TransformerManager`` knowing
all the transformers. This way, you are able to directly call an other
transformer with the method ``$this->getTransformer('foo')``.

You also have access to the ``Router`` and to the ``GroupContext``
(see `group context page`_)

Usage
~~~~~

In the controller, you should access your transformer via
``TransformerManager``.

.. code-block:: php

    class FooController extends Controller
    {
        public function listAction()
        {
            $foo = new Foo(); //Create foo object

            return $this
                ->get('open_orchestra_api.transformer_manager')
                ->get('foo')
                ->transformer($foo);
        }
    }

Entity modification
~~~~~~~~~~~~~~~~~~~

Once your entity has been serialized as a Facade to expose the data,
you might need to modify it.

To help you do it, the ``TransformerInterface`` provides you a ``reverseTransform``
method. This method take as argument the facade send in the request and
the entity to modify.

First, add a method to the ``FooController``:

.. code-block:: php

    // Set a route on the 'POST' method and a paramConverter
    public function editAction(Request $request, Foo $foo)
    {
        // Deserialize the content of the request in the FooFacade
        $facade = $this
            ->get('jms_serializer')
            ->deserialize(
                $request->getContent(),
                'FooBundle\Facade\FooFacade',
                $request->get('_format', 'json')
            );

        // Perform the reverse transform operation
        $this
            ->get('open_orchestra_api.transformer_manager')
            ->get('foo')
            ->reverseTransform($facade, $foo);

        // Check if the entity is valid
        if ($this->isValid($foo)) {
            //Save the entity

            return new Response('', 200);
        }

        // If the entity is not valid, return the violations
        return new Response(
            $this
                ->get('jms_serializer')
                ->serialize(
                    $this->getViolations(),
                    $request->get('_format', 'json')
                ),
            400
        );
    }

Then complete the ``reverseTransform`` method from the ``FooTransformer``, I will
keep the same parameter.

.. code-block:: php

    public function reverseTansform(FacadeInterface $fooFacade, $fooEntity = null)
    {
        if (isset($fooFacade->baz)) {
            $fooEntity->bar = $facade->baz;
        }

        return $fooEntity;
    }

.. _`group context page`: /en/latest/developer_guide/api_group_context.html
.. _`Facade design pattern`: https://en.wikipedia.org/wiki/Facade_pattern
