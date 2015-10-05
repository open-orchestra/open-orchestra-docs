deploy asset
============

Context
-------

As specified in Symfony Reference Documents :

The assets version "is used to bust the cache on assets by globally adding a query parameter to all rendered asset paths (e.g. /images/logo.png?v2).
This applies only to assets rendered via the Twig asset function (or PHP equivalent) as well as assets rendered with Assetic."

This assets version could be founded in app/config/config.yml.

.. code-block:: yaml

    framework:
        assets:
            version: 1.0.0

This assets version is used by Open Orchestra Back Office.
In order to minimize downloads, the different templates used in the rendering of Back Office are stocked in browser's local storage.
These templates have two indexes in local storage : assets version and Back Office language.
So, If a template is needed during navigation, the browser checks if it is present in local storage regarding to current asset version and language of the Back Office.
In such case, the browser loads the template from local storage instead of loading from server.

For this reason, in case of template updates, it is needed to change assets version in app/config/config.yml otherwise the changes will not appear.