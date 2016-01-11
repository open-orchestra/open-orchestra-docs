Manage Bower and Npm Dependencies
=================================

Open Orchestra uses npm to manage some server side javascript libraries and
bower to manage the client side libraries.

To facilitate the addition of bower and npm dependencies, Open Orchestra uses the composer plugin
`composer-extra-assets`_ which allows to declare such dependencies in the composer.json

Adding Bower and Npm Dependencies
---------------------------------

To add your own Bower and Npm dependencies you have to specify them in the ``composer.json`` of your
application or your bundle.

.. code-block:: javascript

    "require": {
        "koala-framework/composer-extra-assets": "~2.0"
    },
    "extra": {
        "require-npm": {
            "grunt": "0.4.*"
        },
        "require-bower": {
            "jquery": "*"
        },
    }

If you add Npm dependencies in your bundle, you can add the ``expose-npm-packages``
attribute to the composer, with this option , the Npm package are available in the node_modules 
directory of Composer's root and not in the directory of your bundle.

.. code-block:: javascript

    "require": {
        "koala-framework/composer-extra-assets": "~2.0"
    },
    "extra": {
        "require-npm": {
             "gulp": "*"
        },
        "expose-npm-packages": true
    }

Bower.json and Package.json files
---------------------------------

``composer-extra-assets`` generates ``bower.json`` and ``package.json`` files.
it's not recommended to add your Bower and Npm dependencies in these files because she will be overwritten
when the next ``composer update|install``.

.. _`composer-extra-assets`: https://github.com/koala-framework/composer-extra-assets
