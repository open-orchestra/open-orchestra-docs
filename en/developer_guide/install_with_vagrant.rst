Install OpenOrchestra with vagrant
==================================

Open Orchestra is composed of two projects : *open-orchestra* which is the CMS Backoffice and *open-orchestra-front-demo* which
is the Frontoffice part that will display the sites and pages created in the CMS.

Requirements
------------

To install Open Orchestra you need to have installed the following software on your server:

* Apache2 ``sudo aptitude install apache2``
* PHP ``sudo aptitude install php5-dev php5-cli php-pear``
* php-mongo  ``sudo pecl install mongo``
* Activate php mongo extension copy ``extension=mongo.so`` on your php.ini

For developers, we provide a Vagrant-powered environment with provisioning so you get minimal setup actions to do.

Install Vagrant
---------------
The project is running on a Vagrant virtual environment built on VirtualBox to be production ready.

.. code-block:: bash

    $ aptitude install virtualbox
    $ wget https://dl.bintray.com/mitchellh/vagrant/vagrant_1.6.3_x86_64.deb
    $ dpkg -i vagrant_1.6.3_x86_64.deb

Install ansible
---------------

All the project server configuration is going to be handled by ansible.
To avoid version troubles, switch to release 1.8.2

.. code-block:: bash

    $ git clone git://github.com/ansible/ansible.git --recursive
    $ cd ./ansible
    $ git checkout -b release1.8.2 origin/release1.8.2
    $ git submodule init
    $ git submodule update --recursive
    $ source ./hacking/env-setup

Go on the project page for more information : http://www.ansible.com

Download Composer
-----------------

Composer is the package manager used by modern PHP applications.

To install composer with curl:

.. code-block:: bash

    $ curl -sS https://getcomposer.org/installer | php

If you don't have curl installed, you can also download it with php:

.. code-block:: bash

    $ php -r "readfile('https://getcomposer.org/installer');" | php

see `Download Composer`_

Install OpenOrchestra
---------------------

Install open-orchestra with composer:

.. code-block:: bash

    $ ./composer.phar create-project open-orchestra/open-orchestra path/to/your/back/folder -s dev
    $ ./composer.phar create-project open-orchestra/open-orchestra-front-demo path/to/your/front/folder -s dev
    $ ./composer.phar create-project open-orchestra/open-orchestra-media-demo path/to/your/media/folder -s dev

Clone the provisioning repository in another folder :

.. code-block:: bash

    $ git clone git@github.com:open-orchestra/open-orchestra-provision.git

Install roles from ansible-galaxy
---------------------------------

Install roles needed to launch the box
as a prerequisite, update your python modules if required with those two

.. code-block:: bash

    $ aptitude install python-yaml
    $ aptitude install python-jinja2

If running under Mac OS X, you would install them through ``pip``

    easy_install pip
    pip install pyyaml jinja2

Then go into openorchestra-provisioning directory

.. code-block:: bash

    $ ansible-galaxy install --role-file=galaxy.yml

Override the dns redirection
----------------------------

In the ``/etc/hosts`` file of your computer add the following lines :

.. code-block:: text

    192.168.33.10   admin.openorchestra.dev
    192.168.33.10   demo.openorchestra.dev
    192.168.33.10   media.openorchestra.dev

Launch the box
--------------

In the ``open-orchestra`` directory, when you launch the box, it will take some time to :

* Import the base box
* Launch it
* Run all the provisioning scripts

.. code-block:: bash

    $ vagrant up

Install the assets
------------------

We are using npm to manage some server side javascript libraries and bower to manage the client side libraries

Connect to the vagrant box using ``vagrant ssh``, then go in the project directory inside the box

.. code-block:: bash

    $ cd /var/www/openorchestra

Install the npm dependencies

.. code-block:: bash

    $ npm install

The npm should have also installed the bower component.

Launch the grunt command to generate all assets

.. code-block:: bash

    $ ./node_modules/.bin/grunt

Load the fixtures
-----------------

In the symfony project directory ``/var/www/openorchestra`` you can load the fixtures provided :

.. code-block:: bash

    $ php app/console doctrine:mongo:fixture:load --env=prod

Now you can log on http://admin.openorchestra.dev/login with username=admin and password=admin for the CMS
and see the result on http://demo.openorchestra.dev.

All the images will be visible on the http://media.openorchestra.dev url.

.. _`Download Composer`: https://getcomposer.org/download/
