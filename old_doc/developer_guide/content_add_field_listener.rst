Add a special listener to a Content Attribute
=============================================

Context
-------

When working with the Content and ContentType, you might have the need to add a specific listener.

In some case, the field can store a collection which needs to be initialized by a listener to set all the data.

The main issues is that all the contentAttribute are stored as a raw field in mongoDB. By doing this, the data you will
save will be typed but the data you get back will only be an array.

Here is an example of how you can take profit of the Content architecture to store some TranslatedValue field
inside.

Usage
-----

Prerequisites
~~~~~~~~~~~~~

In the Open Orchestra model abstraction, the Translated Value are stored as a collection of ``TranslatedValueInterface``
implementation. Each object will store the language code and the translated value.

When you use it in a simple form, you will need to add a listener on the form :

.. code-block:: php

    $builder->addEventListener(FormEvents::PRE_SET_DATA, array($this->translateValueInitializerListener, 'preSetData'));

Then you can simply add the form type :

.. code-block:: php

    $builder->add('descriptions', 'translated_value_collection');

The entity should also implement the ``TranslatedValueContainerInterface``.

Issue description
~~~~~~~~~~~~~~~~~

As you use a dynamic Field Type to describe your content, the ``Content`` document cannot implement the
``TranslatedValueContainerInterface`` to give the name of the translated fields.

Moreover, the listener has to be configured in the root form. As the configuration is fully dynamic, you
cannot add it.

Solution
~~~~~~~~

A simple solution is to create a specific form type, add an initializer, and take care of the data transformation.

First create the specific form type :

.. code-block:: php

    class TranslatedValueContainerAttributeType extends AbstractType
    {
        public function getName()
        {
            return 'translated_value_container_attribute';
        }
    }


Then inject the default value initializer :

.. code-block:: php

    protected $translatedValueDefaultValueInitializer;

    /**
     * @param TranslatedValueDefaultValueInitializer $translatedValueDefaultValueInitializer
     */
    public function __construct(TranslatedValueDefaultValueInitializer $translatedValueDefaultValueInitializer)
    {
        $this->translatedValueDefaultValueInitializer = $translatedValueDefaultValueInitializer;
    }

Finally, create the listener to initialize the data :

.. code-block:: php

    public function buildForm(FormBuilderInterface $builder, array $options)
    {
        $translatedValueDefaultValueInitializer = $this->translatedValueDefaultValueInitializer;
        $builder->addEventListener(FormEvents::PRE_SET_DATA, function(FormEvent $event) use ($translatedValueDefaultValueInitializer) {
            $data = $event->getData();
            if (is_null($data)) {
                $values = new ArrayCollection();
                $translatedValueDefaultValueInitializer->generate($values);
                $data['value'] = $values;
            } elseif (is_array($data) && array_key_exists('value', $data)) {
                foreach ($data['value'] as $key => $element) {
                    $newElement = new TranslatedValue();
                    $newElement->setLanguage($element['language']);
                    $newElement->setValue($element['value']);
                    $data['value'][$key] = $newElement;
                }
            }
            $event->setData($data);
        });

        $builder->add('value', 'translated_value_collection');
    }

When you create the contentAttribute, there are no data stored, so the ``$data`` is null. You need to create an
``ArrayCollection`` which will be later saved and use the initializer to generate all the data you need.

This is the same workflow as the other translated values.

As you can see, there is no event listener bound on Submit events. The raw field type automatically
accepts ``array`` and ``ArrayCollection``.

When you want to display the data stored, you need to transform it from an ``array`` to a
``TranslatedValue`` document.

*Note :* This should be done in a `DataTransformer`_.

Configuration
~~~~~~~~~~~~~

In order to make this form type available in the field type, you need to declare it :

.. code-block:: yaml

    translated:
        label: translated
        type: translated_value_container_attribute
        options:
            required:
                default_value: false

.. _`DataTransformer`: http://symfony.com/doc/current/cookbook/form/data_transformers.html
