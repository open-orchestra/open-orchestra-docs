Manage assets with Grunt
========================

Context
-------

To automate all the assets management process, the Open Orchestra Back Office uses the task manager
`Grunt`_.

*Grunt* is looking for its configuration inside the ``Gruntfile.js`` file in the root directory of
the project. This file mainly parses configuration files to recreate a Grunt configuration object.

In order to simplify the management of external bundles assets, each bundle describes its own
Grunt task and/or task options. As a result, adding a new bundle will simply require little change
in the ``Gruntfile.js`` of your project to load the new configuration parts.

In this documentation, you will see:

- how to `configure your project to use Grunt`_ 
- how to `add an external bundle using Grunt`_ tasks / options
- how to `add your specific tasks / options to your bundles`_ 

.. _configure your project to use Grunt:

Configuring your project to use Grunt
-------------------------------------

When you install your Open Orchestra Back Office, you have to create a ``Gruntfile.js`` to manage
the assets included in the bundles you choose. This file loads and parses configuration files to
produce the Grunt configuration.

You are totally free to code this the way you prefer, and here is a functionnal sample providing
standard functionnalities:

.. code-block:: javascript

    module.exports = function(grunt) {
        require('load-grunt-tasks')(grunt);
        grunt.loadTasks('./grunt_tasks');
        grunt.loadTasks('./vendor/open-orchestra/open-orchestra-cms-bundle/OpenOrchestra/GruntTasks');

        var merge = require('merge');
        var config = {
            pkg: grunt.file.readJSON('package.json'),
            env: process.env
        };
        config = merge.recursive(true, config, loadDirConfig('./grunt_tasks/options/'));
        config = merge.recursive(true, config, loadDirConfig('./vendor/open-orchestra/open-orchestra-cms-bundle/OpenOrchestra/GruntTasks/Options/'));

        grunt.initConfig(config);
    };

    function loadDirConfig(path) {
        var glob = require('glob');
        var merge = require('merge');
        var dirConfig = {};

        glob.sync('*', {cwd: path}).forEach(function(filename) {
            var fileConfig = loadFileConfig(path, filename);
            dirConfig = merge.recursive(true, dirConfig, fileConfig);
        });

        return dirConfig;
    }

    function loadFileConfig(path, filename) {
        var keys =  filename.replace(/\.js$/,'').split('.');

        var buildFileConfig = function(keys, filepath) {
            if (keys.length == 0) {
                return require(filepath);
            } else {
                var subArray = {};
                var index = keys[0];
                keys.shift();
                subArray[index] = buildFileConfig(keys, filepath);
                return subArray;
            }
        }

        return buildFileConfig(keys, path + filename);
    }

When launching Grunt (via the shell command ``./node_modules/.bin/grunt``), this script will be run. It
will search for Grunt tasks in directories ``./grunt_tasks`` and ``./vendor/open-orchestra/open-orchestra-cms-bundle/OpenOrchestra/GruntTasks``.
It will then search for tasks options in ``./grunt_tasks/options/`` and ``./vendor/open-orchestra/open-orchestra-cms-bundle/OpenOrchestra/GruntTasks/Options/``.
As you run Grunt without any parameter it will then launch the Default task.

.. _add an external bundle using Grunt:

Adding an external bundle using Grunt
-------------------------------------

If you take a closer look at the ``open-orchestra-cms-bundle``, you will see it does not contain
the media administration part. To manage the media, you have to add the ``open-orchestra-media-admin-bundle``.

This bundle comes with its own javascript and css files that need to be added to the website assets
files. Assuming you have installed the bundle using composer, you still have to configure Grunt to
use the bundle assets.

For that purpose, you need to update 3 parts of the Grunt configuration:

- load the new tasks
- load the new task options
- tell somewhere when these tasks must be run

To load the task, you have to use ``grunt.loadTasks`` on the correct directory. In our case you have
to update the ``Gruntfile.js`` file with this:

.. code-block:: javascript

    // line 5
    grunt.loadTasks('./vendor/open-orchestra/open-orchestra-media-admin-bundle/OpenOrchestra/GruntTasks');

To load task options, you have two possibilities, depending on what you want to do:

- to load a single file, use the ``loadFileConfig`` function
- to load all files in a directory, use the ``loadDirConfig`` function

In both cases, you have to merge the resulting object to the main configuration object.

For the ``open-orchestra-media-admin-bundle``, we want to load all files from a single directory,
so it looks like:

.. code-block:: javascript

    // line 13
    config = merge.recursive(true, config, loadDirConfig('./vendor/open-orchestra/open-orchestra-media-admin-bundle/OpenOrchestra/GruntTasks/Options/'));

``Grunt`` will now be aware of the different tasks present in the ``MediaAdminBundle``.

Some tasks, such as the symlinks generation, will be automatically launched. Other tasks will
require some configuration modifications. For instance it is the case of js and css concatenation.
All the Back Office javascript files are concatened in a single file, and the same applies to css
files. This operation is made in two parts (two similar passes for both js and css).

In the first part, files are grouped by functionnalities. For instance media related javascript
files are put in a file named ``media.js``.
The second part groups all generated files in a unique one. This final file is directly used by the
Back Office.

The ``open-orchestra-media-admin-bundle`` requires two concatenations: one for the javascript
described in the ``concat.mediajs.js`` file and one for the css described in the ``concat.mediacss.js``
file. Now you have to tell Grunt when to lauch these tasks and how to add the two 'functionnality'
files to the final files.

Add the media javascript task by modifying the main javascript task (``grunt_task/javascript_task.js``):

.. code-block:: javascript

    module.exports = function(grunt) {
        grunt.registerTask('javascript',
            [
                'coffee:discovering',
                'coffee',
                'concat:smartadminjs',
                'concat:libjs',
                'concat:orchestrajs',
                'concat:mediajs',
                'concat:js'
            ]
        );
    };

When the 'javascript' task will be run, the ``concat:mediajs`` task will now be called.

Do the same for the stylesheets by modifying the main css task (``grunt_task/css_task.js``):

.. code-block:: javascript

    module.exports = function(grunt) {
        grunt.registerTask('css',
            [
                'less:discovering',
                'less',
                'concat:smartadmincss',
                'concat:libcss',
                'concat:orchestracss',
                'concat:mediacss',
                'concat:css',
                'cssmin'
            ]
        );
    };

To include the result of the first concatenation part to the final javascript file, alter the
``grunt_tasks/options/concat.js.js`` file:

.. code-block:: javascript

    module.exports = {
        src: [
            'web/built/smartadmin.js',
            'web/built/lib.js',
            'web/built/orchestra.js',
            'web/built/media.js'
        ],
        dest: 'web/js/all.js'
    };

Finally the ``all.js`` file will include the smartadmin functionnality, followed by the lib
functionnality, and so on...

Do similar modification on the stylesheets by modifying the ``grunt_tasks/options/concat.css.js`` file:

.. code-block:: javascript

    module.exports = {
        src: [
            'web/built/smartadmin.css',
            'web/built/lib.css',
            'web/built/orchestra.css',
            'web/built/media.css'
        ],
        dest: 'web/css/all.css'
    };

Now run the Grunt command (``./node_modules/.bin/grunt``) to regenerate the ``all.js`` and ``all.css``
files. If you check these files, you should see the ``open-orchestra-media-admin-bundle`` assets.


.. _add your specific tasks / options to your bundles:

Adding your specific tasks / options to your bundles
----------------------------------------------------

At last, you may need to know how to create your specific tasks for your own bundle. As the process
is the same for the javascript and stylesheet files, we will only talk about javascript files. To
illustrate the explanation.

Let's assume you have created the ``FooBundle`` and want to manage its assets with Grunt.

As seen in the previous section, concatenation task is resolved in two passes. The first pass groups
files by functionnality and the second pass glues the functionnalities together. While the second
pass is described in the application (it depends on the used bundles), the first pass is described
by the bundle itself. This is done by adding an entry in the main concat task.

First create a directory to put all your tasks (``GruntTasks/Options`` for instance). Then you can
create a Grunt task file describing the files to append and naming the file to output the
concatenation. The Grunt task file name must follow a specific template: taskname.subtask1.subtask2.[...].subtaskn.js.
The task loader wil use that name to recreate the main configuration. In our case, we want to create
a sub-entry named foojs to the concat task, so name your file ``concat.foojs.js``. This file can be as
simple as:

.. code-block:: javascript

    module.exports = {
        src: [
            'web/bundles/FooBundle/js/*.js'
        ],
        dest: 'web/built/foo.js'
    };

Or if the concatenation order matters, you can be more exhaustive with something like:

.. code-block:: javascript

    module.exports = {
        src: [
            'web/bundles/FooBundle/js/js_1.js',
            'web/bundles/FooBundle/js/js_2.js',
            ...
            'web/bundles/FooBundle/js/js_n.js'
        ],
        dest: 'web/built/foo.js'
    };

When using your foo bundle in an Open Orchestra application, you can inject your task in the app as
described in the previous section.

.. _`Grunt`: http://gruntjs.com/
