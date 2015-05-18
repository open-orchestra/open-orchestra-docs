Multi-device
============

Open Orchestra is compatible with the adaptive way of rendering web pages. The idea is to serve
different html versions of the same document according to the device displaying it. For instance
an iphone version could show less blocks than a comptuter version.

The main steps of the process are the following:

- Request tagguing: The server catch the request and tag it with the device type
- Request processing: Open Orchestra processes the request
- Template selection: When requested to render the page, the template engine select automatically
  the correct template version
- Response generation: The page is rendered and served to the client


Prerequisite
------------

To enable the multi-device rendering, the server entry point (webserver or reverse-proxy) must be able
to detect the client device type and to add a request header corresponding to that device type. A good
way to do that is to use a tool implementing the Wurfl library. Varnish for instance can do that task.
The `device detection`_ must also be set up.


Configuration
-------------

To activate the adaptive response, all the devices name requiring a specific template have to be defined
in the configuration:

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

If we take a closer look at this configuration, we can see that four device types are declared : web,
tablet, phone and androïd. We can also see that a fallback tree is generated:

* The web device is the default one
* Tablet and Phone device have the same parent: web. This generates a fallback from tablet templates
  to web templates and from phone templates to web templates. If a tablet template is required but
  can't be found, the parent template version, ie web one on this example, will be used.
* On an androïd device, the parent is phone, introducing a new fallback.

Fallback mechanism is recursive, so if the parent alternative is not found, the grand-parent will be
required, and so on until the default one. So default templates always have to be implemented.


Device detection
----------------

As seen on he prerequisite, the server entry point (webserver or reverse-proxy) must implement the
`Wurfl library`_. This libray tests the User-Agent and normalizes device names. With that information,
the server can patch the request headers by adding a parameter ``x-ua-device``.

With the previous configuration sample, the generated header ``x-ua-device`` needs to be equal to
'tablet', 'phone' or 'android'.

**Open Orchestra does not provides configuration allowing that detection and headers modification,
it's up to you to configure the tool you're using.**


Template engine
---------------

When a template must be rendered, the method ``render`` of the template engine is called. So to
exploit the multi-devices features, the template engine must be updated with some functionalities.

Out of the box, Open Orchestra enhances the twig engine. If you need to use another template engine,
you have to implement this logic on this engine.


Twig exemple
------------

Here is how Open Orchestra enhances TwigEngine.


First both TwigEngine and TimedTwigEngine classes are extended in the FrontBundle:

.. code-block:: php

    FrontBundle\Twig\OrchestraTimedTwigEngine
    FrontBundle\Twig\OrchestraTwigEngine


The ``FrontBundle\Twig\Renderable`` trait overrides the ``render()`` method by adding the device
name in the template name, exploring the previously set request header ``x-ua-device``.

.. code-block:: php

    if (strstr($name, 'twig')) {
        return str_replace('html.twig', $device . '.html.twig', $name);
    }


The newly extended template engine can now be declared in the conf:

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


Required templates
------------------
Once the template engine is able to get the correct template alternative according to the request
header, the matching templates have to be created. In our exemple, each template have to be declined 
as follow :

* default template version : myTemplate.html.twig
* tablet template version : myTemplate.tablet.html.twig
* phone template version : template.phone.html.twig

Note that if an alternative version is not created, the fallback mechanism will check for the parent
alternative. So again, each alternative are optionals, but the default template is required to prevent
the fallback mechanism to crash.

.. _device detection: /en/developer_guide/multi_device.rst#device-detection
.. _Wurfl library: http://wurfl.sourceforge.net
