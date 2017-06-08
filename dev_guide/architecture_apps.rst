
Architecture des applications
=============================

Back office
-----------

.. image:: /images/architecture/archi_back.png
    :align: center
    :alt:   Architecture Back office


Base de données
^^^^^^^^^^^^^^^

Open Orchestra n'est pas lié à un type de base de données spécifique. Par défaut,
il y a une implémentation avec `MongoDB <https://www.mongodb.com/fr>`_ qui est fourni. Toutefois elle
peut être remplacée afin d'utiliser une autre base de données (Mysql, ...).

Api
^^^

Open Orchestra fournit une `Api REST <https://fr.wikipedia.org/wiki/Representational_state_transfer>`_ réalisée avec
Symfony afin d'accéder aux différentes entités du CMS (pages, contenus, sites, etc)

Form
^^^^

Sur Open Orchestra les formulaires ne sont pas créés par l'application Javascript mais par Symfony,
cela afin de bénéficier des différents avantages du `composant form <http://symfony.com/doc/current/forms.html>`_ de Symfony.
L'application Javascript récupère les formulaires générés par Symfony en Ajax.

Application Javascript
^^^^^^^^^^^^^^^^^^^^^^

Le Back office d'Open Orchestra est réalisé intégralement en JavaScript avec le framework `Backbone.js <http://backbonejs.org/>`_
L'application Javascript récupère les différentes données en Ajax fournies par l'application Symfony.

Front office
------------


.. image:: /images/architecture/archi_front.png
    :align: center
    :alt:   Architecture Front office

L'application Front office d'un site réalisée avec Open Orchestra se rapproche plus de l'architecture standard
 d'une application Symfony.

La seule particularité est la présence d'un reverse proxy qui permet d'améliorer les performances
avec notamment l'utilisation du cache `esi <https://symfony.com/doc/current/http_cache/esi.html>`_ .

.. note::

    La :doc:`configuration docker </dev_guide/install>` proposée par Open Orchestra utilise `Varnish <https://www.varnish-cache.org/>`_ comme reverse proxy.
    Il est accessible depuis le port ``6081``


.. note::

    Sur Open Orchestra la présence d'un reverse proxy n'est pas obligatoire. Si aucun reverse proxy n'est
    configuré sur l'application Front office, cette dernière continuera de fonctionner.
