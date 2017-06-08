
Installation du CMS Open Orchestra
==================================

Par défaut, une application Open Orchestra est composée de deux applications Symfony:

- La Back office (`open-orchestra  <https://github.com/open-orchestra/open-orchestra>`_)
- Le Front office (`open-orchestra-front-demo  <https://github.com/open-orchestra/open-orchestra-front-demo>`_)

.. note::

     Open Orchestra permet aussi de regrouper le Back office et le
     Front office au sein d'une même application.


Pré-requis
----------

Pour simplifier l'installation et la mise en place d'un environnement compatible,
Open Orchestra fournit une configuration `Docker <https://www.docker.com/>`_.

 - `Installer Docker <https://docs.docker.com/engine/installation/>`_
 - `Installer Docker compose <https://docs.docker.com/compose/install/>`_

.. caution::

    Une version supérieur à 1.6.0 est requise pour Docker compose et
    supérieur à 1.10 pour Docker Engine.


Création des applications
-------------------------

.. caution::

    Cette section considère que vous maîtrisez `Composer <https://getcomposer.org/>`_
    et qu'il soit `installé <https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx>`_.

.. tip::

    Pour simplifier l'installation, il est conseillé de mettre les deux applications Symfony
    (Back office et Front office) et la configuration de l'environement Docker au sein du même dossier.


Création des applications Front et Back office :

.. code-block:: terminal

    $ cd my_project_name/

    # création des applications
    $ composer create-project open-orchestra/open-orchestra open-orchestra --ignore-platform-reqs --no-scripts
    $ composer create-project open-orchestra/open-orchestra-front-demo open-orchestra-front-demo --ignore-platform-reqs --no-scripts

    # Dossier qui contiendra les medias de la médiathèque
    $ mkdir uploaded-files


Création de l'environnement docker
----------------------------------

.. code-block:: terminal

    $ cd my_project_name/

    # clonage de la configuration pour l'environnement docker
    $ git clone git@github.com:open-orchestra/open-orchestra-provision-docker.git

    $ cd open-orchestra-provision-docker/
    # création des conteneurs
    $ docker-compose up -d


Installation des applications
-----------------------------

Installation des vendors, des dépendances Javascript et de la configuration.

Back office:

.. code-block:: terminal

    $ docker exec -it -u www-data oo_apache_php /bin/bash
    $ cd /var/www/openorchestra/ && composer install #install vendors
    $ ./bin/node ./node_modules/.bin/grunt # compilation des less et js
    $ exit

.. note::

    Lorsque Composer demandera de remplir les différents paramètres, utilisez les valeurs ci-dessous
    ou la valeur par défaut si le paramètre n'est pas spécifié

    .. code-block:: yaml

        open_orchestra_cms.mongodb.host: oo_mongo
        fos_http_cache.proxy_client.varnish.servers: [oo_varnish:6081]
        media_storage_directory: /var/www/uploaded-files
        host_elastica: oo_elasticsearch

Front office:

.. code-block:: terminal

    $ docker exec -it -u www-data oo_apache_php /bin/bash
    $ cd /var/www/front-openorchestra/ && composer install
    $ app/console assets:install
    $ exit

.. note::

    Lorsque Composer demandera de remplir les différents paramètres, utilisez les valeurs ci-dessous
    ou la valeur par défaut si le paramètre n'est pas spécifié

    .. code-block:: yaml

        open_orchestra_cms.mongodb.server: 'mongodb://oo_mongo:27017'
        fos_http_cache.proxy_client.varnish.servers: [oo_varnish:6081]
        host_elastica: oo_elasticsearch

Configuration des hosts
-----------------------

Dans le fichier de configuration des hosts de votre ordinateur (``/etc/hosts`` pour linux)
utilisez les dns suivants:

    .. code-block:: text

      [IP]   admin.openorchestra.2-0.dev
      [IP]   demo.openorchestra.2-0.dev
      [IP]   media.openorchestra.2-0.dev

.. note::

    | [IP] doit être remplacé par 127.0.0.1 pour Linux.
    | [IP] doit être remplacé par la valeur fournit par la commande ``docker-machine ip default``

