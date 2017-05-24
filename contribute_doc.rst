Contribution à la documentation
===============================

note::
------

.. note::

    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    Cras ac arcu ligula. Nulla molestie neque eget justo blandit,
    ac laoreet tellus tristique. Sed libero nunc, tincidunt id accumsan sed, porttitor eu mauris.
    In blandit leo id mauris egestas laoreet. Aenean nisi ex, viverra at tempor quis, placerat at nisi.
    Suspendisse potenti.Mauris urna eros, pretium id sodales non, lobortis a est.

    .. code-block:: terminal

        # for example, if WAMP is used ...
        c:\> move symfony c:\wamp\bin\php
        # ... then, execute the command as:
        c:\> symfony

tip::
-----

.. tip::

    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    Cras ac arcu ligula. Nulla molestie neque eget justo blandit,
    ac laoreet tellus tristique. Sed libero nunc, tincidunt id accumsan sed, porttitor eu mauris.
    In blandit leo id mauris egestas laoreet. Aenean nisi ex, viverra at tempor quis, placerat at nisi.
    Suspendisse potenti.Mauris urna eros, pretium id sodales non, lobortis a est.


caution::
---------

.. caution::

    then *three* services have been created (the automatic service + your two services)
    and the automatically loaded service will be passed - by defaut - when you type-hint
    ``SiteUpdateManager``. That's why creating the alias is a good idea.

code-block:: ini
----------------

.. code-block:: ini

   ; Linux and macOS systems
   curl.cainfo = "/path/to/cacert.pem"

   ; Windows systems
   curl.cainfo = "C:\path\to\cacert.pem"


code-block:: text
-----------------

.. code-block:: text

    http://localhost:8000/config.php

code-block:: terminal
---------------------

.. code-block:: terminal

    # Linux and macOS systems
    $ sudo mkdir -p /usr/local/bin
    $ sudo curl -LsS https://symfony.com/installer -o /usr/local/bin/symfony
    $ sudo chmod a+x /usr/local/bin/symfony

code-block:: yaml
-----------------

.. code-block:: yaml

    # config.yml

    # FOSUserBundle
    fos_user:
        db_driver: mongodb
        firewall_name: main
        user_class: OpenOrchestra\UserBundle\Document\User
        group:
            group_class: OpenOrchestra\GroupBundle\Document\Group


code-block:: javascript
-----------------------

.. code-block:: javascript

    module.exports = function(grunt) {
      var appConfig = require('./grunt/app_config.js');
      var GruntConfigBuilder = require(appConfig.GruntConfigBuilder);

      GruntConfigBuilder.init(grunt, appConfig);
    };


code-block:: bash
-----------------

.. code-block:: bash

    ./bin/grunt



code-block:: php
----------------

.. code-block:: php

    class AppKernel extends Kernel
    {
        // ...

        public function registerBundles()
        {
            $bundles = array(
                // others bundles
                new Doctrine\Bundle\MongoDBBundle\DoctrineMongoDBBundle(),
                new FOS\HttpCacheBundle\FOSHttpCacheBundle(),
            );

            // ...
        }
    }
