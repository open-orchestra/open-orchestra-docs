Concepts-clés
=============

Cette documentation vous expliquera les concepts les plus importants de OpenOrchestra.

Les noeuds
----------

Les noeuds correspondent aux pages que les utilisateurs voient sur le site, ce sont des conteneurs pour les zones et les blocs.
Dans Open Orchestra il y a deux types de noeuds :
* Les noeuds qui sont les pages du site.
* Le noeud transverse qui contient les blocs transverses (bloc commun à plusieurs pages d'un site par exemple le bloc menu).

Les noeuds sont multilangues, multi-version et ont un workflow de validation.

Voir aussi la documentation `Les paramètres d'un noeud`_.

Les types de contenus
---------------------

Les types de contenus permettent de créer de nouvelle sorte de contenu que vous pourrez contribuer plus tard. La création d'un type de contenu permet de définir les champs de ces futures contenus.

Par exemple pour un type de contenus news avec les champs suivants :

* Un champ titre de type text
* Un champ date de type date
* Un champ information de type textarea

Lorsque vous créerez un contenu de type news vous devrez contribuer ces champs.

Voir aussi `Présentation des types de contenus`_.

Les contenus
------------

Dans Open orchestra les contenus permettent d'afficher des informations (articles, news, etc...).
Les contenus sont définis par un type de contenu.
Comme pour les noeuds les contenus sont multilangues, multi-version et ont un workflow de validation.

Voir aussi `Présentation des contenus`_.

Les templates
-------------

Les templates permettent de préconfigurés des pages en y plaçant des zones. Open Orchestra permet d'utiliser un des templates déjà créé comme modèle pour la création des noeuds.

Voir aussi `configuration d'un template`_.

Les zones
---------

Les zones permettent d'organiser l'architecture de la page. Les zones sont dans des noeuds et contiennent d'autres zones ou des blocs.

Voir aussi `configuration d'une zone`_.

Les blocs
---------

Le bloc est la brique de base représentant tout élément visible sur une page.
L'agrégation des blocs dans un noeuds permet de construire des pages variées.

Voir aussi la `liste des blocs`_ disponibles.

Les blocs transverses
---------------------

Les blocs transverses sont définis dans le noeud transverse, ils peuvent être utilisés par plusieurs noeuds d'un site.
Tous les blocs peuvent être transverses, il suffit de les ajouter dans le noeud transverse.
Les blocs transverses sont configurables que dans le noeud transverse.

Les thèmes
----------

Un thème représente l'identité visuelle d'un site, notamment les thèmes regroupent les fichiers css et javascript qui ont une cohérence entre eux afin de pouvoir habiller des sites d'une certaine manière.

Voir aussi comment ajouter un `thème`_.

Les sites
---------

Open Orchestra est multisite et permet de créer plusieurs sites depuis le même Back Office.

Voir aussi conguration d'un `site`_.

Les appareils
-------------

Open Orchestra est multi-device et permet d'afficher, sur le Front Office, un template différent en fonction du device utilisé.

Voir aussi `multi-devices`_.

Les mots-clés
-------------

Dans Open Orchestra vous pouvez créer des mots-clés dans la partie administration du Back Office, que vous pourrez utiliser ensuite pour tagguer des contenus ou des médias.

Les utilisateurs
----------------

Les utilisateurs sont ceux pouvant se connecter au Back Office de Open Orchestra et y faire des contributions. Il y a aussi les utilisateurs Front Office qui peuvent se connecter sur les parties privées d'un site.
Open Orchestra permet de donner des groupes aux utilisateurs.

Voir aussi configuration d'un `utilisateur`_.

Les rôles
---------

Les rôles permettent de définir des droits sur le Back Office.

Voir aussi création d'un `rôle`_.

Les groupes
-----------

Les groupes agrègent des rôles et sont ensuite attribués aux utilisateurs.
Les groupes ont plusieurs rôles.

Voir aussi configuration d'un `groupe`_.

Les bundles
-----------

Open Orchestra suis la modularité de Symfony et le code est donc organisé en bundles séparés.

Les bundles d'Open Orchestra :

 * open-orchestra-base-bundle contient les méthodes commune au Back Office et Front Office.
 * open-orchestra-cms-bundle contient les méthodes d'affichage du Back Office.
 * open-orchestra-front-bundle contient les méthodes d'affichage du Front Office.
 * open-orchestra-display-bundle contient toutes les strategies d'affichage Front Office des blocs.
 * open-orchestra-model-interface est une description exhaustive des méthodes utilisées par les autres bundles.
 * open-orchestra-model-bundle contient tous ce qui rattaché à la base de donnée (doctrinemongodb).
 * open-orchestra-media-bundle contient tous ce qui est rattaché aux médias.
 * open-orchestra-user-bundle contient tous ce qui est rattaché aux utilisateurs.

 Pour utiliser une autre base de donnée ajoutez votre propre bundle implementant toutes les interfaces de open-orchestra-model-interface.

.. _rôle:
.. _site:
.. _thème:
.. _groupe:
.. _utilisateur:
.. _multi-devices:
.. _liste des blocs:
.. _configuration d'une zone:
.. _Présentation des contenus:
.. _Les paramètres d'un noeud:
.. _configuration d'un template:
.. _Présentation des types de contenus:
