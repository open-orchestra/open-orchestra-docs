Install OpenOrchestra with Docker for contributors
===================================================

Open Orchestra is composed of three projects: 

- *open-orchestra* which is the CMS Back Office;
- *open-orchestra-front-demo* which is the Front Office part that will display the sites and pages
  created in the CMS Back Office;
- *open-orchestra-media-demo* which will display the images loaded in the CMS Back Office.

For contributors, we provide a Docker environment so you get minimal
setup actions to do.

Install Virtualbox (for MacOS and Windows)
------------------------------------------

Mac OS

- download http://download.virtualbox.org/virtualbox/4.3.20/VirtualBox-4.3.20-96996-OSX.dmg

Windows

- download http://download.virtualbox.org/virtualbox/4.3.20/VirtualBox-4.3.20-96997-Win.exe

Install Docker
---------------
The project is running in a virtual environment to be production ready.

### Linux ###

.. code-block:: bash

    $ sudo apt-get update
    $ sudo apt-get install wget
    $ sudo apt-get install curl
    $ wget -qO- https://get.docker.com/ | sh
    
Note: If your company is behind a filtering proxy, you may find that the apt-key command fails for the Docker repository during installation. To work around this, add the key directly using the following:

.. code-block:: bash

    $ wget -qO- https://get.docker.com/gpg | sudo apt-key add -
    
Create docker group

.. code-block:: bash

    $ sudo usermod -aG docker ubuntu
	
Install docker compose

.. code-block:: bash

    $ curl -L https://github.com/docker/compose/releases/download/1.5.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
    $ chmod +x /usr/local/bin/docker-compose
    
### Mac OS ###

.. code-block:: text

    download https://www.docker.com/docker-toolbox (mac version)
    install the package
    open a terminal (e.g. http://cmder.net/)
    
type the commands
    
.. code-block:: bash

    $ docker-machine create default --driver=virtualbox
    $ eval $(docker-machine env default)

### Windows ###

.. code-block:: text

    download https://www.docker.com/docker-toolbox (mac version)
    install the package
    open a terminal (e.g. http://cmder.net/)
    
type the commands
    
.. code-block:: bash

    $ docker-machine create default --driver=virtualbox
    $ eval $(docker-machine env default)

Download Composer
-----------------

Composer is the package manager used by modern PHP applications.

To install composer with curl:

.. code-block:: bash

    $ curl -sS https://getcomposer.org/installer | php

If you don't have curl installed, you can also download it with PHP:

.. code-block:: bash

    $ php -r "readfile('https://getcomposer.org/installer');" | php

see `Download Composer`_

Install OpenOrchestra
---------------------

First of all, you have to clone the Open Orchestra Docker repository:

  .. code-block:: bash

    $ git clone git@github.com:open-orchestra/open-orchestra-provision-docker.git

To contribute to the project a script can install two versions: the master version and the last stable one. The master branch is the branch which should be used to add new features to the project.
Here is the directory tree with your two projects:

.. code-block:: none

    |_ open-orchestra-provision-docker
          |_ open-orchestra-master
                |_ open-orchestra
                |_ open-orchestra-front-demo
                |_ open-orchestra-media-demo
                |_ open-orchestra-provision
          |_ open-orchestra-stable
                |_ open-orchestra
                |_ open-orchestra-front-demo
                |_ open-orchestra-media-demo
                |_ open-orchestra-provision

1. Easy way

You can run all the commands below with one script :

  .. code-block:: bash

    $ ./install.sh master
    or
    $ ./install.sh stable
    
2. Manual way

To install the master open-orchestra parts using ``composer``:

  In your ``open-orchestra-master`` directory:
  
  .. code-block:: bash

    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra ./open-orchestra -s dev --ignore-platform-reqs --no-scripts --keep-vcs dev-master
    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra-front-demo ./open-orchestra-front-demo -s dev --ignore-platform-reqs --no-scripts --keep-vcs dev-master
    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra-media-demo ./open-orchestra-media-demo -s dev --ignore-platform-reqs --no-scripts --keep-vcs dev-master

  Build Docker containers :

  .. code-block:: bash

    $ docker-compose -f docker-compose.yml -f docker-compose-master.yml up -d

- To install the stable open-orchestra parts using ``composer``:

  In your ``open-orchestra-stable`` directory:
  
  .. code-block:: bash

    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra ./open-orchestra -s stable --ignore-platform-reqs --no-scripts --keep-vcs
    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra-front-demo ./open-orchestra-front-demo -s stable --ignore-platform-reqs --no-scripts --keep-vcs
    $ [path-to-composer]/composer.phar create-project open-orchestra/open-orchestra-media-demo ./open-orchestra-media-demo -s stable --ignore-platform-reqs --no-scripts --keep-vcs

  Build Docker containers :

  .. code-block:: bash

    $ docker-compose -f docker-compose.yml -f docker-compose-stable.yml up -d

Parameters to define at the end of composer install
---------------------------------------------------

.. code-block:: yaml

    open_orchestra_cms.mongodb.host : mongo
    fos_http_cache.proxy_client.varnish.servers : [varnish:6081]
    host_elastica : elastica
    
Override the DNS redirections
-----------------------------

In the ``/etc/hosts`` file of your computer add the following lines:

    [IP] must be replaced by 127.0.0.1 for Linux
    [IP] must be replaced by the value gived by the command ``docker-machine ip default``

.. code-block:: text

    [IP]   admin.openorchestra.dev
    [IP]   demo.openorchestra.dev
    [IP]   media.openorchestra.dev
    [IP]   admin.openorchestra.stable
    [IP]   demo.openorchestra.stable
    [IP]   media.openorchestra.stable

You should follow the same steps to install each versions :

* Run the containers
* Install the assets
* Load the fixtures

Run the init script
-------------------

To finish the insytallation, you must launch an init script inside the main container by using this command:

  .. code-block:: bash

    $ docker exec -it app_open_orchestra_master /load.sh
    or
    $ docker exec -it app_open_orchestra_stable /load.sh

It will take some time to:

* prepare the cache and logs directories inside the App container
* NPM Install (it's the longer process of the procedure)
* Composer install
* Load fixtures
* Create ElasticSearch Indexes and populate data
* Launch Grunt to install the assets


Result
------

Master version
~~~~~~~~~~~~~~

You can log on http://admin.openorchestra.dev/app_dev.php/login with username=admin and
password=admin for the CMS and see the result on http://demo.openorchestra.dev/app_dev.php.

All the images will be visible on the http://media.openorchestra.dev/app_dev.php url.

Stable version
~~~~~~~~~~~~~~

You can log on http://admin.openorchestra.stable/app_dev.php/login with username=admin and
password=admin for the CMS and see the result on http://demo.openorchestra.stable/app_dev.php.

All the images will be visible on the http://media.openorchestra.stable/app_dev.php url.

.. _`Download Composer`: https://getcomposer.org/download/

