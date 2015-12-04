Form Type Override
==================

Context
-------

Open orchestra is composed of a certain number of form types, it includes those needed system but also meets most
needs it user. Any time these needs are often unique, and see the need to expand to replace existing configuration
are required.

We provide you different ways to override part of the Open Orchestra form type which depends on
your use case :

- If you want to modify the logic of the form type, `override the service`_
- If you want to modify the whole service, `override the full form type`_

See again `symfony2 documentation`_ to modify the form display.

Override directly a form type
-----------------------------

Open Orchestra gives you two ways to override a form type.

.. _override the service:

Override the service
~~~~~~~~~~~~~~~~~~~~

You can directly replace a form type by overloading its service.
All open-orchestra form type have their referenced class in the parameters from config file.

.. code-block:: yaml

    # open-orchestra-cms-bundle/BackofficeBundle/Ressources/config/form.yml
    parameters:
        open_orchestra_backoffice.type.api_client.class: OpenOrchestra\BackofficeBundle\Form\Type\ApiClientType

It's thus possible for you to override these parameters and thus overload the class from service.

.. code-block:: yaml

    parameters:
        open_orchestra_backoffice.type.api_client.class: Foo\ExampleBundle\Form\Type\ApiClientType

This method won't give you the opportunity to change the class constructor and all the dependency
injected to the form type.

.. _override the full form type:

Override the full form type
~~~~~~~~~~~~~~~~~~~~~~~~~~~

To override an existing form type by its name, you have to add your block in the services form config file.
Don't forget the tag in your declaration.

.. code-block:: yaml

    services:
        fooexamplebundle.type.api_client:
            class: %fooexamplebundle.type.api_client.class%
            tags:
                - { name: form.type, alias: %FORM_TYPE_NAME% }

Finally, the getName method must return the same name as the overloaded form type.

.. code-block:: php

    public function getName()
    {
        return "form_type_name";
    }

This method will give you the opportunity to totally redefine the form type, from the dependency needed
to the working logic.

.. _`form type parameter`: /en/developer_guide/form_type.rst
.. _`symfony2 documentation`: http://symfony.com/doc/current/cookbook/form/form_customization.html
