Install OpenOrchestra with Docker for contributors
==================================================

Open Orchestra is composed of three projects:

- *open-orchestra* which is the CMS Back Office;
- *open-orchestra-front-demo* which is the Front Office part that will display the sites and pages
  created in the CMS Back Office;
- *open-orchestra-media-demo* which will display the images loaded in the CMS Back Office.

For contributors, we provide a Docker environment so you get minimal
setup actions to do.


Install Docker
--------------

Install of Open Orchestra with docker require `Compose 1.6.0+` and `Docker Engine 1.10.+`.

 - Install Docker for `Linux  <https://docs.docker.com/engine/installation/linux/>`_
 - Install Docker for `Mac  <https://docs.docker.com/docker-for-mac/>`_
 - Install Docker for `Windows  <https://docs.docker.com/docker-for-windows/>`_


Install OpenOrchestra
---------------------

Clone the Open Orchestra applications repository and Docker repositories in the same folder:

  .. code-block:: bash

    $ cd <your_project_folder>/
    $ git clone git@github.com:open-orchestra/open-orchestra-provision-docker.git --branch 1.2
    $ git clone git@github.com:open-orchestra/open-orchestra.git --branch 1.2
    $ git clone git@github.com:open-orchestra/open-orchestra-front-demo.git --branch 1.2
    $ git clone git@github.com:open-orchestra/open-orchestra-media-demo.git --branch 1.2
    $ mkdir uploaded-files

Build Docker containers:

  .. code-block:: bash

    $ cd <your_project_folder>/open-orchestra-provision-docker/
    $ docker-compose up -d


Install applications:

Back Office:

  .. code-block:: bash

    $ cd <your_project_folder>/open-orchestra-provision-docker/
    $ docker exec -it -u www-data oo_apache_php /bin/bash
    $ cd /var/www/openorchestra/ && composer install #install vendors

  When to complete the application settings, use these parameters (use default value for other)

  .. code-block:: yaml

    open_orchestra_cms.mongodb.host: oo_mongo
    fos_http_cache.proxy_client.varnish.servers: [oo_varnish:6081]
    host_elastica: oo_elasticsearch
    media.directory: /var/www/uploaded-files

  .. code-block:: bash

    $ ./bin/grunt  #install assets
    $ app/console orchestra:mongo:fixtures:load --env=prod --type=all #load fixtures
    $ exit

Front Office:

  .. code-block:: bash

    $ cd <your_project_folder>/open-orchestra-provision-docker/
    $ docker exec -it -u www-data oo_apache_php /bin/bash
    $ cd /var/www/front-openorchestra/ && composer install
    $ app/console assets:install
    $ exit

  When to complete the application settings, use these parameters (use default value for other)

  .. code-block:: yaml

    open_orchestra_cms.mongodb.server: 'mongodb://oo_mongo:27017'
    fos_http_cache.proxy_client.varnish.servers: [oo_varnish:6081]
    host_elastica: oo_elasticsearch

Media:

  .. code-block:: bash

    $ cd <your_project_folder>/open-orchestra-provision-docker/
    $ docker exec -it -u www-data oo_apache_php /bin/bash
    $ cd /var/www/media-openorchestra/ && composer install
    $ exit

  When to complete the application settings, use these parameters (use default value for other)

  .. code-block:: yaml

    media.directory: /var/www/uploaded-files


Override the DNS redirections
-----------------------------

In the ``/etc/hosts`` file of your computer add the following lines:

    [IP] must be replaced by 127.0.0.1 for Linux
    [IP] must be replaced by the value gived by the command ``docker-machine ip default``

    .. code-block:: text

      [IP]   admin.openorchestra.1-2.dev
      [IP]   demo.openorchestra.1-2.dev
      [IP]   media.openorchestra.1-2.dev