Install OpenOrchestra on your computer
======================================

Open Orchestra is composed of three projects : *open-orchestra* which is the CMS Back Office
and *open-orchestra-front-demo* which is the Front Office part that will display the sites
and pages created in the CMS Back Office and *open-orchestra-media-demo* which will display
the images loaded in the CMS Back Office.

This tutorial has been tested on a debian 8.2.

Install the environment
-----------------------

Install the php server
~~~~~~~~~~~~~~~~~~~~~~

Install php5 and the mongo extension :

.. code-block:: bash

    $ sudo aptitude install php5-cli php5-dev php-pear php5-curl php5-imagick libav-tools
    $ sudo pecl install mongo

Activate the mongo extension in php :

.. code-block:: bash

    $ sudo echo "extension=mongo.so" > /etc/php5/mods-available/mongo.ini
    $ sudo ln -s /etc/php5/mods-available/mongo.ini /etc/php5/cli/conf.d/30-mongo.ini

Install the database
~~~~~~~~~~~~~~~~~~~~

Install mongo in the 2.6 version at least :

.. code-block:: bash

    $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
    $ echo 'deb http://downloads-distro.mongodb.org/repo/debian-sysvinit dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list
    $ sudo aptitude update
    $ sudo aptitude install mongodb-org

Check the mongo version :

.. code-block:: bash

    $ mongo --version #MongoDB shell version: 2.6.*

Install NPM
~~~~~~~~~~~

As a prerequisite, install those packages :

.. code-block:: bash

    $ sudo aptitude install wget curl make g++ gcc libcurl4-openssl-dev libsasl2-2 libsasl2-dev libcurl3

Download and install npm :

.. code-block:: bash

    $ wget http://nodejs.org/dist/v0.10.24/node-v0.10.24.tar.gz ./node-v0.10.24.tar.gz
    $ tar -xvzf node-v0.10.24.tar.gz
    $ cd node-v0.10.24
    $ sudo ./configure --prefix=/usr/local/ && sudo make && sudo make install

Install the project
-------------------

Download Composer
~~~~~~~~~~~~~~~~~

Composer is the package manager used by modern PHP applications.

To install composer with curl:

.. code-block:: bash

    $ sudo aptitude install git
    $ curl -sS https://getcomposer.org/installer | php

If you don't have curl installed, you can also download it with php:

.. code-block:: bash

    $ php -r "readfile('https://getcomposer.org/installer');" | php

see [Download Composer](https://getcomposer.org/download/)

Install OpenOrchestra
~~~~~~~~~~~~~~~~~~~~~

Install open-orchestra with composer:

.. code-block:: bash

    $ ./composer.phar create-project open-orchestra/open-orchestra path/to/your/folder -s stable 1.1.x
    $ ./composer.phar create-project open-orchestra/open-orchestra-front-demo path/to/your/folder -s stable 1.1.x
    $ ./composer.phar create-project open-orchestra/open-orchestra-media-demo path/to/your/folder -s stable 1.1.x

Install the assets
------------------

Launch the grunt command to generate all assets

.. code-block:: bash

    $ ./bin/grunt

Load the fixtures
-----------------

Open Orchestra needs some fixtures to work (an admin user, a website, ...).

.. code-block:: bash

    $ php app/console orchestra:mongodb:fixtures:load --type=production --env=prod


Launch the server
~~~~~~~~~~~~~~~~~

You can use the built in webserver to launch the backoffice of Open Orchestra :

.. code-block:: bash

    $ php app/console server:run

Go on the homepage : ``http://127.0.0.1:8000``

For the front office, you need to install apache and configure the server
