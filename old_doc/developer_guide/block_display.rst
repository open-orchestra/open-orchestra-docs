Block display
=============

Display Independence
--------------------

In the Front Office, some blocks could require some specific CSS and JavaScript files.
To allow any block to add some specific files, the main node layout loads the
`requireJS`_ library which is a JavaScript file and module loader.
Each block is allowed to call the ``require()`` function of the ``requireJS`` library.
To allow CSS dynamic load, Open Orchestra offers an AMD module named ``openOrchestraCss``
which is meant to be used with ``requireJS``.
In a case in which the same block is displayed several times, corresponding CSS and JavaScript files
will only be loaded once.

Block loader file
-----------------

For each block there is a ``blockLoader.js`` file using the ``requireJS`` library.
In a ``blockLoader.js`` file are defined the module used to load CSS: ``openOrchestraCss``,
specific JavaScript files in block and JavaScript files in common libraries which are
needed to initialize a block.

After loading the elements, it does the initialization. During this step, CSS are loaded using
the ``openOrchestraCss`` module with the ``load()`` function and optional JavaScript is run.

A ``blockLoader.js`` file is structured as the following:

.. code-block:: javascript

    requirejs(
        ['jquery'],
        function() {
            require(
                [
                    //Define required elements
                    'openOrchestraCss', //Module used to load CSS
                    '/bundles/nameofbundle/block/NameOfMyBlock/js/foo.js', //Specific JavaScript in block
                    '/bundles/nameofbundle/libs/bar/bar.js'//JavaScript in common libraries
                ],
                function (openOrchestraCss) {
                    //Load block CSS
                    openOrchestraCss.load(['/bundles/nameofbundle/block/NameOfMyBlock/css/style.css']);

                    //You can add optional JavaScript code here
                    jQuery(document).ready(function ($) {


                    });
                }
            )
        }
    );


Example: Gallery block
----------------------

In the MediaBundle, the ``Resources/views/Block`` directory contains the Front Media blocks display
templates.
The file ``Gallery/show.html.twig`` ends with the ``blockLoader.js`` load which does CSS
and JavaScript dynamic load in relation with Gallery block.

.. code-block:: html

    <script>
        require(['{{ asset('/bundles/openorchestramedia/block/Gallery/blockLoader.js') }}']);
    </script>


Blocs maintainability
---------------------

To keep consistency between all blocks, you should use a file tree like the following:

.. code-block:: none

    |_ MyBundle
        |_ Resources
            |_ public
            |   |_ block
            |   |   |_ NameOfMyBlock
            |   |       |_ css
            |   |       |   |_ * Place here css files of your block *
            |   |       |
            |   |       |_ js
            |   |       |   |_ * Place here JavaScript files of your block *
            |   |       |
            |   |       |_ img
            |   |       |   |_ * Place here images files of your block *
            |   |       |
            |   |       |_ blockLoader.js * Block loading file which loads specific css and JavaScript *
            |   |
            |   |_ libs
            |   |   |_ * Place here commons libraries to many blocks *
            |   |
            |   |_ img
            |       |_ * Place here commons images to many blocks *
            |
            |_ views
                |_ Block
                    |_ NameOfMyBlock
                        |_ * Place here block display templates *

.. _`requireJS`: http://requirejs.org