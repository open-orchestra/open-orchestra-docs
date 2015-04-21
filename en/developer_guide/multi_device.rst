Multi-device
============

Prerequisite
------------

To enable the multi-device rendering, we assume that the server entry point (webserver or reverse-proxy)
 implements the Wurfl librairy and is able to add a request header with the device type.
You will also have to set up the `device detection`_.

The device name will be used in the configuration and in the template name. For instance, if you have defined two specific
devices, phone and tablet, you will have to create the following templates :

* default template : template.html.twig
* tablet template : template.tablet.html.twig
* phone template : template.phone.html.twig

Configuration
-------------

To activate the adaptive response, you have to define all the devices name in the configuration :

.. code-block:: yaml

    #app\config\config.yml
    open_orchestra_front:
        devices:
            web: ~
            tablet:
                parent: web
            phone:
                parent: web
            android:
                parent: phone

If we take a closer look at this configuration :

* The web device is the root one
* If there is no android template, it will look for the phone one
* If there is no phone template, it will look for the main one
* If there is no tablet template, it will look for the main one

Template engine
---------------

In order to switch automatically between all the templates, we had to add some functionality to the template engine.

If you want to use another template engine, you need to implement this logic. We provide you with all the modifications
we made in twig as an exemple.

Twig exemple
------------

First we have extended both TwigEngine and TimedTwigEngine in the FrontBundle :

.. code-block:: php

    FrontBundle\Twig\OrchestraTimedTwigEngine
    FrontBundle\Twig\OrchestraTwigEngine

Use the ``FrontBundle\Twig\Renderable`` trait which overrides the ``render()`` method by adding the device name
in the template name

.. code-block:: php

    if (strstr($name, 'twig')) {
        return str_replace('html.twig', $device . '.html.twig', $name);
    }

Then, you declare the engine service based on the new class and set the ``templating`` value as the service alias  :

.. code-block:: yaml

    #FrontBundle\Resources\config\twig.yml

    parameters:
     open_orchestra_front.twig.orchestra_twig_engine.class: OpenOrchestra\FrontBundle\Twig\OrchestraTwigEngine

    services:
        open_orchestra_front.twig.orchestra_twig_engine:
            class: %open_orchestra_front.twig.orchestra_twig_engine.class%
            arguments:
                - @twig
                - @templating.name_parser
                - @templating.locator
                - @request_stack
                - %open_orchestra_front.devices%
            alias: templating

.. _device detection:
