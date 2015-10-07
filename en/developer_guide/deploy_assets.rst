Deploy asset
============

Context
-------

As specified in Symfony Reference Documents :

The assets version

    "is used to bust the cache on assets by globally adding a query parameter to all rendered asset paths (e.g. /images/logo.png?v2).
	This applies only to assets rendered via the Twig asset function (or PHP equivalent) as well as assets rendered with Assetic."

This assets version could be founded in app/config/config.yml.

.. code-block:: yaml

    framework:
        assets:
            version: 1.0.0

This assets version is used by Open Orchestra Back Office.
In order to minimize downloads, the different templates used in the rendering of Back Office are stocked in browser's local storage.
These templates have two indexes in local storage : assets version and Back Office language.
While rendering, the Back Office requires some underscore template.
When asked, the browser will first check in the local storage, with the current asset version and current Back Office language as key.
If the the template is found, there will be no request to the server to load it.

For this reason, in case of template updates, This process will require a modification of the asset version parameter in the app/config/config.yml file to allow the changes to appear.