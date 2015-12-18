Media display
=============

Context
-------

To improve your website performances, a common way is to download the page data from
multiple servers. In fact, in the HTTP protocol, a browser can make only two parallel
requests to the same domain. Recent browsers (such as ``Chrome`` or ``Firefox`` can perform
up to 10 simultaneous requests). In the following documentation, we will just assume that
browsers can make only two simultaneous requests to the same domain.

An easy way to load and display the medias would be to add a new virtual host to your existing Open Orchestra
installation. This will allow your browser to increase the number of parallel requests that can be done as
several domain are available. It will then reduce the global latency of each page's download

Request scheme:

.. image:: ../../images/two_parallel.gif
.. image:: ../../images/four_parallel.gif

This solution is not ideal because you will need to boot the whole Open Orchestra
kernel each time you will request an image.

Open Orchestra Solution
-----------------------

A simple solution would be to install only the ``open-orchestra-media-file-bundle`` as a single
``Symfony`` application.

Basic installation
~~~~~~~~~~~~~~~~~~

The ``open-orchestra-media-file-bundle`` can run on it's own if you require it in the ``composer.json`` file :

.. code-block:: json

    "require": {
        "incenteev/composer-parameter-handler": "~2.0",
        "open-orchestra/open-orchestra-media-file-bundle": "*"
    },

Then enable all the required bundles in your ``AppKernel.php`` file:

.. code-block:: php

    new Symfony\Bundle\FrameworkBundle\FrameworkBundle(),
    new Symfony\Bundle\SecurityBundle\SecurityBundle(),
    new Symfony\Bundle\TwigBundle\TwigBundle(),
    new Sensio\Bundle\FrameworkExtraBundle\SensioFrameworkExtraBundle(),

    new Knp\Bundle\GaufretteBundle\KnpGaufretteBundle(),

    new OpenOrchestra\BaseBundle\OpenOrchestraBaseBundle(),
    new OpenOrchestra\MediaBundle\OpenOrchestraMediaFileBundle(),

Ease your installation
~~~~~~~~~~~~~~~~~~~~~~

To facilitate this installation, we provide you with the ``open-orchestra-media-demo``
repository which implements all those modifications.

To install it :

.. code-block:: bash

    composer create-project open-orchestra/open-orchestra-media-demo ./
