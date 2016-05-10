Install OpenOrchestra with vagrant for contributors
===================================================

Open Orchestra is composed of three projects: 

- *open-orchestra* which is the CMS Back Office;
- *open-orchestra-front-demo* which is the Front Office part that will display the sites and pages
  created in the CMS Back Office;
- *open-orchestra-media-demo* which will display the images loaded in the CMS Back Office.

For contributors, we provide a Vagrant-powered environment with provisioning so you get minimal
setup actions to do.

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

To contribute on the project you have to install tree versions: the 1.2 version, 1.1 version and 1.0 version.
The 1.2 version is the branch which should be used to add new features to the project.
Here is the directory tree with your tree projects that we recommand:

.. code-block:: none

    |_ install-directory
          |_ open-orchestra-1.0
                |_ open-orchestra
                |_ open-orchestra-front-demo
                |_ open-orchestra-media-demo
                |_ open-orchestra-provision
          |_ open-orchestra-1.1
                |_ open-orchestra
                |_ open-orchestra-front-demo
                |_ open-orchestra-media-demo
                |_ open-orchestra-provision
          |_ open-orchestra-1.2
                |_ open-orchestra
                |_ open-orchestra-front-demo
                |_ open-orchestra-media-demo
                |_ open-orchestra-provision

- To install the 1.2 open-orchestra parts using ``composer``:

  In your ``open-orchestra-1.2`` directory:
  
  .. code-block:: bash

    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra ./open-orchestra -s dev --ignore-platform-reqs --no-scripts --keep-vcs dev-master
    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra-front-demo ./open-orchestra-front-demo -s dev --ignore-platform-reqs --no-scripts --keep-vcs dev-master
    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra-media-demo ./open-orchestra-media-demo -s dev --ignore-platform-reqs --no-scripts --keep-vcs dev-master

  Clone the provisioning repository:

  .. code-block:: bash

    $ git clone git@github.com:open-orchestra/open-orchestra-provision.git

- To install the 1.1 version open-orchestra parts using ``composer``:

  In your ``open-orchestra-1.1`` directory:
  
  .. code-block:: bash

    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra ./open-orchestra -s dev --ignore-platform-reqs --no-scripts --keep-vcs 1.1.x
    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra-front-demo ./open-orchestra-front-demo -s dev --ignore-platform-reqs --no-scripts --keep-vcs 1.1.x
    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra-media-demo ./open-orchestra-media-demo -s dev --ignore-platform-reqs --no-scripts --keep-vcs 1.1.x

  Clone the 1.1 provisioning repository. Don’t forget to specify the last 1.1 version branch
  with the ``--branch`` option.

  .. code-block:: bash

    $ git clone git@github.com:open-orchestra/open-orchestra-provision.git --branch=1.1

- To install the 1.0 version open-orchestra parts using ``composer``:

  In your ``open-orchestra-1.0`` directory:

  .. code-block:: bash

    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra ./open-orchestra -s dev --ignore-platform-reqs --no-scripts --keep-vcs 1.0.x
    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra-front-demo ./open-orchestra-front-demo -s dev --ignore-platform-reqs --no-scripts --keep-vcs 1.0.x
    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra-media-demo ./open-orchestra-media-demo -s dev --ignore-platform-reqs --no-scripts --keep-vcs 1.0.x

  Clone the 1.0 provisioning repository. Don’t forget to specify the last 1.0 version branch
  with the ``--branch`` option.

  .. code-block:: bash

    $ git clone git@github.com:open-orchestra/open-orchestra-provision.git --branch=1.0

Override the dns redirection
----------------------------

In the ``/etc/hosts`` file of your computer add the following lines:

.. code-block:: text

    192.168.33.10   admin.openorchestra.1-1.dev
    192.168.33.10   demo.openorchestra.1-1.dev
    192.168.33.10   media.openorchestra.1-1.dev

    192.168.33.11   admin.openorchestra.1-0.dev
    192.168.33.11   demo.openorchestra.1-0.dev
    192.168.33.11   media.openorchestra.1-0.dev

    192.168.33.12   admin.openorchestra.1-2.dev
    192.168.33.12   demo.openorchestra.1-2.dev
    192.168.33.12   media.openorchestra.1-2.dev

You should follow the same steps to install each versions :

* Install roles from ansible-galaxy
* Launch the box
* Install the assets
* Load the fixtures

Install roles from ansible-galaxy
---------------------------------

Go into ``open-orchestra-provisioning`` directory and install roles needed to launch the box:

.. code-block:: bash

    $ ansible-galaxy install --role-file=galaxy.yml

Launch the box
--------------

In the ``open-orchestra`` directory, when you launch the box, it will take some time to:

* Import the base box
* Launch it
* Run all the provisioning scripts

.. code-block:: bash

    $ vagrant up

Install the assets
------------------

We are using npm to manage some server side javascript libraries and bower to manage the client side libraries.

Connect to the vagrant box using ``vagrant ssh``

Finalise the ``composer`` installation in each project:

.. code-block:: bash

    $ cd /var/www/openorchestra && composer run-script post-install-cmd
    $ cd /var/www/front-openorchestra && composer run-script post-install-cmd
    $ cd /var/www/media-openorchestra && composer run-script post-install-cmd

Then go in the Back Office project directory inside the box:

.. code-block:: bash

    $ cd /var/www/openorchestra

If you are dealing with version 1.1 or superior, launch the grunt command to generate all assets:

.. code-block:: bash

    $ ./bin/grunt

If you are dealing with the 1.0 version, the process differs, you have to install manually the dependencies
then when it's ok, run grunt from the node_modules folder:

.. code-block:: bash

    $ npm install
    $ ./node_modules/.bin/grunt


Load the fixtures
-----------------

In the symfony project directory ``/var/www/openorchestra`` you can load the fixtures provided:

.. code-block:: bash

    $ php app/console doctrine:mongo:fixture:load --env=dev

Result
------

1.2 version
~~~~~~~~~~~

You can log on http://admin.openorchestra.1-2.dev/app_dev.php/login with username=admin and
password=admin for the CMS and see the result on http://demo.openorchestra.1-2.dev/app_dev.php.

All the images will be visible on the http://media.openorchestra.1-2.dev/app_dev.php url.

1.1 version
~~~~~~~~~~~

You can log on http://admin.openorchestra.1-1.dev/app_dev.php/login with username=admin and
password=admin for the CMS and see the result on http://demo.openorchestra.1-1.dev/app_dev.php.

All the images will be visible on the http://media.openorchestra.1-1.dev/app_dev.php url.

1.0 version
~~~~~~~~~~~

You can log on http://admin.openorchestra.1-0.dev/app_dev.php/login with username=admin and
password=admin for the CMS and see the result on http://demo.openorchestra.1-0.dev/app_dev.php.

All the images will be visible on the http://media.openorchestra.1-0.dev/app_dev.php url.

.. _`Download Composer`: https://getcomposer.org/download/
.. _`Ansible installation documentation`: http://docs.ansible.com/ansible/intro_installation.html
