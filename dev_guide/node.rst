Pages, Templates
================

Les pages sont composées de zones et de blocs qui seront visibles par les utilisateurs en Front office.
Une page est versionable, tradusible et soumis au workflow définis dans le Back office.

Sur Open Orchestra, les templates disponibles utilisés par une page sont regroupés dans un conteneur,
 appelé *templateSet*.

.. note ::

    Un *template set* est sélectionné lors de la création d'un site. Ainsi toutes les pages de cd
    site peuvent utiliser les templates du *template set* sélectionné.

La création d'un nouveau *template set* se découpe en deux parties: Back office et Front office.

Configuration Back office
^^^^^^^^^^^^^^^^^^^^^^^^^

Configuration d'un template set
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

La configuration d'un *template set* ŝ'effectue simplement avec de la configuration YAML.

.. code-block:: yaml

    # app/config.yml

    # ...

    open_orchestra_backoffice:
       template_set:
            default_template_set: # identifiant du template set
                label: open_orchestra_backoffice.template_set.default.label # clé de traduction du label
                styles: [] # Liste des styles qui peuvent être utilisés dans les blocs
                templates: [] # Liste des templates appartenant au template set

Création d'un template
^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: yaml

    # app/config.yml

    # ...

    open_orchestra_backoffice:
       template_set:
            default_template_set: # Identifiant du template set
                label: app.template_set.default.label # clé de traduction du label
                styles: [] # Liste des styles qui peuvent être utilisés dans les blocs
                templates:
                    my_custom_template: # Identifiant du template
                        areas: # Liste des aires du template contribuable
                            - main
                        label: app.template_set.default.template_name.my_custom_template # clé de traduction du label
                        # Chemin du fichier qui représente le template utilisé lors de la contribution d'un node
                        path: /bundles/app/templateSet/default_template_set/my_custom_template.html


Le fichier fournis par le ``path`` est simplement un fichier HTML qui est utilisé afin d'avoir un rendu
visuelle du template lors de la contribution des pages utilisant ce template. Par exemple voici le fichier
utilisé pour **my_custom_template** qui est un template avec **trois zones** (header, main et footer) où
main est une zone contribuable.

.. code-block:: html

    <!-- src/AppBundle/Resources/public/templateSet/default_template_set/my_custom_template.html -->

    <div class="row">
        <div class="col-lg-12">
            <!-- Ajout de la classe disabled pour désactiver la contribution de l'aire -->
            <div class="area header disabled">
                <span>Header</span>
                <div class="block-container"></div>
            </div>
        </div>
    </div>
    <div class="row">
        <div class="col-lg-12">
            <!-- data-aire-id obligatoire pour les zones contribuables -->
            <div class="area " data-area-id="main">
                <span>Main</span>
                <div class="block-container"></div>
            </div>
        </div>
    </div>
    <div class="row">
        <div class="col-lg-12">
            <div class="area footer disabled">
                <span>Footer</span>
                <div class="block-container"></div>
            </div>
        </div>
    </div>

.. note ::

    Au sein de ce fichier, vous pouvez utiliser la représentation que vous désirez. Afin d'être reconnus
    les conteneurs des aires contribuables doivent posséder l'attribut ``data-area-id`` avec le nom de l'aire
    comme valeur.

Voici le rendu Back office lorsque le template ``my_custom_template`` est utilisé par une page :

.. image:: /images/page/template_bo_preview.png
    :align: center
    :alt: Rendu Back office du template my_custom_template


Configuration Front office
^^^^^^^^^^^^^^^^^^^^^^^^^^

Une fois la configuration Back office effectuée il faut réaliser le template qui sera utilisé
pour le rendu front de la page.

Dans un premier temps, il faut créer un template twig ou d'un autre type suivant le moteur de template utilisé
pour votre application Symfony.

.. code-block:: twig

    {# src/AppBundle/Resources/views/Template/Default/my_custom_template.html.twig #}

    {% extends 'OpenOrchestraFrontBundle:Node:base_node.html.twig' %}

    {% block body %}
        <div class="container">
            <header class="header">
                Mon header
            </header

            <main class="row">
                {{ render_area('main', node, {'parameters': parameters }) }}
            </main>

           <footer class="footer">
                Mon footer
           </footer>
        </div>
    {% endblock %}

.. note ::

    Il est recommandé d'étendre le template ``base_node.html.twig`` qui permet de définir les
    différentes balises contenues dans ``<head>`` (title, meta, etc) en fonction de la page affichée.


Le template possède une zone contribuable en Back office, la zone ``main``. Afin d'afficher cette zone
et ces différents blocs contribués en Back Office, il existe la fonction twig ``render_area``.

Pour finir, il faut indiquer dans la configuration que le template ``my_custom_template`` doit utiliser
le fichier ``my_custom_template.html.twig`` pour effectuer son rendu.


.. code-block:: yaml

    # app/config.yml

    # ...

    open_orchestra_front:
       template_set:
            default_template_set: # Identifiant du template set
                templates:
                    my_custom_template: 'AppBundle:Template/Default:my_custom_template.html.twig'

