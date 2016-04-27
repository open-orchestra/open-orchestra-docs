Server provisioning
===================

Context
-------

At some point in your project, you will have to deploy your Open Orchestra application
across multiple servers and environments.

Whenever you do it, by following this documentation you will be able to use the same
provisioning for all your environments (staging, production, ...).

Host configuration
------------------

In your project, we recommend you to create a ``provisioning/hosts`` folder.
Inside, you will put a host file for each environment to provision, for instance ``prod``
for the production environment.

The ``prod`` file will contain the group server with the ssh hosts :

.. code-block:: none

    [prod]
    open_orchestra_prod

In this case, the prod group will only contain one server, but you can add more if needed

Environment configuration
-------------------------

In the ``provisioning/hosts`` folder, you need to create a ``group_vars`` folder which
will contain all the specific information for each environment. (The files should be
named as in the hosts folder)

Server configuration
~~~~~~~~~~~~~~~~~~~~

* ``user_root`` : The user with the root privileges
* ``hosts_localhost`` : The ``/etc/hosts`` configuration
* ``hosts_site`` : Additional ``hosts`` configuration linked to the deployed sites
* ``sudoers`` : Users used to deploy, they should be able to restart ``Apache2`` and ``Varnish``
* ``selenium_current_directory`` : The folder where the provisioning will download ``selenium``

Apache configuration
~~~~~~~~~~~~~~~~~~~~

* ``apache_main_ports`` : All the ports ``Apache2`` is listening to
* ``apache_conf`` : One entry for each website managed

The ``Apache2`` vhost configuration will require some parameters :

* ``key`` : the key will be used as the vhost filename
* ``port`` : On which port the vhost will be listening
* ``serverName`` : The vhost server name
* ``docRoot`` : The web folder of your Open Orchestra installation
* ``errorLog`` : The filename with the error logs of your vhost
* ``accessLog`` : The filename with the access logs of your vhost
* ``siteId`` : The site id of the front website you are deploying (only needed on front installation)
  The value can be found in the edit form in the Back Office

Example :

.. code-block:: yaml

    apache_conf:
        demo-orchestra.conf:
            port: 8000
            serverName: demo.openorchestra.1-0.dev
            docRoot: /var/www/front-open-orchestra/web
            errorLog: demo-openorchestraError.log
            accessLog: demo-openorchestraAccess.log
            siteId: 2


Varnish configuration
~~~~~~~~~~~~~~~~~~~~~

* ``varnish_listen_port`` : The port ``varnish`` is listening to
* ``backend_conf`` : All the vhost redirected by ``varnish``

The ``backend_conf`` will require some parameters :

* ``name`` : The redirection name
* ``port`` : The redirection port
* ``host`` : The redirection host
* ``admin`` : Set to true if the backend is an Back Office installation

Crontab configuration
~~~~~~~~~~~~~~~~~~~~~

* ``path_front`` : The folder of the front installation
* ``mail_to`` : The webmail where the cron error are send
