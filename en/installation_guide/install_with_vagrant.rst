Install OpenOrchestra with vagrant
==================================

Open Orchestra is composed of three projects : *open-orchestra* which is the CMS Back Office
and *open-orchestra-front-demo* which is the Front Office part that will display the sites
and pages created in the CMS Back Office and *open-orchestra-media-demo* which will display
the images loaded in the CMS Back Office.

For developers, we provide a Vagrant-powered environment with provisioning so you get minimal setup actions to do.

Install Vagrant
---------------
The project is running on a Vagrant virtual environment built on VirtualBox to be production ready.
For more information about Vagrant installation, you can see ` Vagrant installation documentation <https://www.vagrantup.com/docs/>`


Install ansible
---------------

All the project server configuration is going to be handled by ansible.

Our configuration was made for the 1.9.4 version of ansible. **It doesn't work with the version 2 of ansible**.

For more information about ansible installation, you can see `Ansible installation documentation`_.

If you need *tar.gz* archives, you can see this link : https://releases.ansible.com/ansible/

Install nfs server
------------------

To improve the vagrant box performance, we share the folders with the ``nfs`` protocol. You need to
install a nfs server instance on your computer.

.. code-block:: bash

    $ aptitude install nfs-kernel-server

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

Install the different open-orchestra part using ``composer``:

.. code-block:: bash

    $ ./composer.phar create-project open-orchestra/open-orchestra path/to/your/folder -s stable 1.1.x
    $ ./composer.phar create-project open-orchestra/open-orchestra-front-demo path/to/your/folder -s stable 1.1.x
    $ ./composer.phar create-project open-orchestra/open-orchestra-media-demo path/to/your/folder -s stable 1.1.x

Clone the provisioning repository in another folder :

.. code-block:: bash

    $ git clone https://github.com/open-orchestra/open-orchestra-provision.git --branch=1.1

Install roles from ansible-galaxy
---------------------------------

Go into ``open-orchestra-provisioning`` directory and install roles needed to launch the box:

.. code-block:: bash

    $ ansible-galaxy install --role-file=galaxy.yml

Override the dns redirection
----------------------------

In the ``/etc/hosts`` file of your computer add the following lines :

.. code-block:: text

    192.168.33.10   admin.openorchestra.1-1.dev
    192.168.33.10   demo.openorchestra.1-1.dev
    192.168.33.10   media.openorchestra.1-1.dev

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

Connect to the vagrant box using ``vagrant ssh``

Finalise the ``composer`` installation in each project

.. code-block:: bash

    $ cd /var/www/openorchestra && composer run-script post-install-cmd
    $ cd /var/www/front-openorchestra && composer run-script post-install-cmd
    $ cd /var/www/media-openorchestra && composer run-script post-install-cmd

Then go in the Back Office project directory inside the box

.. code-block:: bash

    $ cd /var/www/openorchestra

Launch the grunt command to generate all assets

.. code-block:: bash

    $ ./bin/grunt

Load the fixtures
-----------------

In the symfony project directory ``/var/www/openorchestra`` you can load the fixtures provided :

.. code-block:: bash

    $ php app/console orchestra:mongodb:fixtures:load --type=production --env=prod

Now you can log on http://admin.openorchestra.1-1.dev/login with username=admin and password=admin for the CMS
and see the result on http://demo.openorchestra.1-1.dev.

All the images will be visible on the http://media.openorchestra.1-1.dev url.

.. _`Download Composer`: https://getcomposer.org/download/
.. _`Ansible installation documentation`: http://docs.ansible.com/ansible/intro_installation.html
