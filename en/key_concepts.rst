Concepts-clés
=============

Cette documentation vous expliquera les concepts les plus importants de Open Orchestra.

Les noeuds
----------

Les noeuds sont les conteneurs des zones et des blocs. Dans Open Orchestra il y a deux types de noeuds :
* Les noeuds transverses, ils contiennent les blocs transverses (bloc commun sur un site par exemple le bloc menu).
* Les noeuds sont les pages d'un site.

Les noeuds sont multilangues, multi-version et ont un workflow de validation.

Voir aussi la documentation `Les paramètres d'un noeud`_.

Les contenus
------------

Dans Open Orchestra tout ce que nous affichons est un contenu (article, news, etc...).
Les contenus ont un type de contenu qui définit les champs de celui-ci.
Comme pour les noeuds les contenus sont multilangues, multi-version et ont un workflow de validation.

Voir aussi `Présentation des types de contenus et des contenus`_.

Les templates
-------------

Les templates sont les gabarits des pages du site. Open Orchestra permet de créer des gabarits et de les réutiliser lors de la création des noeuds.

Voir aussi `configuration d'un template`_.

Les zones
---------

Les zones sont dans des noeuds et contiennent d'autres zones ou des blocs. Les zones permettent d'organiser l'architecture de la page.

Voir aussi `configuration d'une zone`_.

Les blocs
---------

Le bloc est la brique de base représentant tout élément visible sur une page.
L'agrégation des blocs dans un noeud permet de construire des pages variés.

Voir aussi la `liste des blocs`_ disponibles.

Les blocs transverses
---------------------

Les blocs transverses sont définis dans le noeud transverse, ils sont communs à touts les noeuds d'un site.
Tous les blocs peuvent être transverses, il faut les ajouter dans le noeud transverse, puis on les retrouve ensuite dans la liste des blocs.
Les blocs transverse ne sont configurable que dans le noeud transverse.

Les thèmes
----------

Les thèmes regroupent les fichiers css et javascript qui ont une cohérence entre eux afin de pouvoir habiller des sites d'une certaine manière.

Voir aussi comment ajouter un `thème`_.

Les sites
---------

Open Orchestra est multisite et permet de créer des sites dans le Backoffice.

Voir aussi conguration d'un `site`_.

Les appareils
-------------

Open Orchestra est multi-device et permet d'afficher, sur le FrontOffice, un template différent en fonction du device utilisé.

Voir aussi `multi-devices`_.

Les mots-clés
-------------

Dans Open Orchestra vous pouvez créer des mots-clés dans la partie administration du Backoffice, que vous pourrez utiliser ensuite pour tagguer des contenus ou des médias.

Les utilisateurs
----------------

Les utilisateurs sont ceux pouvant se connecter au Backoffice de Open Orchestra et y faire des contributions.
Open Orchestra permet de donner des groupes aux utilisateurs.

Voir aussi configuration d'un `utilisateur`_.

Les rôles
---------

Les rôles permettent de définir des droits sur le Backoffice.

Voir aussi création d'un `rôle`_.

Les groupes
-----------

Les groupes permettent de définir les rôles pour un site.
Les groupes ont plusieurs rôles.

Voir aussi configuration d'un `groupe`_.

Les bundles
-----------

Open Orchestra suit la modularité de Symfony et nous avons donc organisé le code en bundles séparés.

Les bundles d'Open Orchestra :

 * open-orchestra-base-bundle
 * open-orchestra-cms-bundle
 * open-orchestra-front-bundle
 * open-orchestra-display-bundle
 * open-orchestra-model-interface
 * open-orchestra-model-bundle
 * open-orchestra-media-bundle
 * open-orchestra-user-bundle
