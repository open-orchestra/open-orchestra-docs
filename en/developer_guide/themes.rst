Themes
======

The CSS and JS files of the themes are rendered with a call to the Twig functions ``openOrchestraCss()``
and ``openOrchestraJs()``, each one is taking as a parameter the theme name to render.

See the `Twig extensions page`_ for more details.

Configuration
-------------

In order for the Twig extension to correctly find the resource files needed for a theme,
the configuration must describe the path of these files individually for each theme available.

Here is a full example of a valid configuration for a theme:

.. code-block:: yaml

    open_orchestra_theme:
        themes: 
            foobar:
                name: "Theme example"
                stylesheets:
                    - AcmeBundle:foo:css/style.css
                    - AcmeBundle:bar:css/font.css
                javascripts:
                    - AcmeBundle:bar:js/main.js
                    
In this case ``foobar`` is the identifier of the theme as referred in the call to the Twig functions.
Three keys can be defined for a theme : 

* ``name`` is a required entry
* stylesheets is an array of CSS files to use
* javascripts is an array of JS files to use

The path of a resource is determined from the configuration. For instance, for the value
``AcmeBundle:foo:css/style.css``, the file will be located at
``[AcmeBundle folder]/Resources/public/themes/foo/css/style.css``.

.. _`Twig extensions page`: ../developer_guide/twig-extensions.html
