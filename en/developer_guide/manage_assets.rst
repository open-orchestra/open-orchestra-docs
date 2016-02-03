Manage assets with Grunt
========================

Context
-------

To automate all the assets management process, the Open Orchestra Back Office uses the task manager `Grunt`_.
This tool allows the creation and execution of assets related tasks written in javascript. For instance Open
Orchestra uses it to compile *CoffeeScript* files or to create some symlinks.

When running grunt via the command

.. code-block:: javascript

   ./node_modules/.bin/grunt

*Grunt* build its configuration via the ``Gruntfile.js`` file located in the root directory of the application.

In order to be as extensible as possible, Open Orchestra offers to each bundle the possibility to extend this
*Grunt* configuration by describing its own task and/or task targets. As a result, managing the assets of a
newly added bundle simply requires a little change in the *Grunt* configuration.

In this documentation, you will see:

- how to `configure your application to use Grunt`_ 
- how to `add an external bundle using Grunt`_ tasks / targets
- how to `add your specific tasks / targets to your bundles`_ 

.. _configure your application to use Grunt:

Configuring your application to use *Grunt*
-------------------------------------------

When you install the Open Orchestra Back Office, you have to create a ``Gruntfile.js`` to manage the assets
included in the bundles you are using. This file loads and parses configuration files to produce the Grunt
configuration.

The ``Grunfile.js`` file belongs to your application, so it's up to you to write it. But to avoid you a waste
of time, you can use the GruntConfigBuilder AMD module developped for Open Orchestra to load *Grunt* splitted
configuration. The file is packaged with the [open-orchestra-cms-bundle](https://github.com/open-orchestra/open-orchestra-cms-bundle)
and located in the GruntTasks folder. The [Open Orchestra Back Office demo project](https://github.com/open-orchestra/open-orchestra)
show how to use it.
The gruntfile.js of this demo is as simple as:

.. code-block:: javascript

   module.exports = function(grunt) {
      var appConfig = require('./grunt/app_config.js');
      var GruntConfigBuilder = require(appConfig.GruntConfigBuilder);

      GruntConfigBuilder.init(grunt, appConfig);
   };

Attached to this minimalist file is a configuration file located at ``application_root_folder/grunt/app_config.js``.
This AMD module describes three things:

.. code-block:: javascript

   module.exports = {
      GruntConfigBuilder:
         /* Path to the GruntConfigBuilder AMD module */
      tasksDir:
         /* Array of paths where to search for Grunt task definitions */
      targetsDir:
         /* Array of paths where to search for Grunt task targets */
   };

The GruntConfigBuilder attribute refers to the AMD module described earlier and located in the
``open-orchestra-cms-bundle``.

The tasksDir attribute is an array listing all folders including *Grunt* task definitions. This is typically
here where you register your bundles providing new *Grunt* tasks.

The targetsDir attribute is an array listing all folders including *Grunt* task targets. This is typically
here where you register your bundles providing new *Grunt* tasks.

For this mechanism to work properly, tasks and target have to be normalized with a few rules:

* First of all, they must be written as AMD modules that the GruntConfigBuilder will load
* Secondly, tasks and targets have to be separated: one folder for tasks, another one for targets
* The name of a file describing a target must be formatted as following: TASK_NAME.TARGET_NAME.js
  For instance ``clean.symlinks.js`` is reffering to the target symlink of the clean task.

If each bundle respects theses rules, everything will load right.

When running *Grunt* (via the shell command ``./node_modules/.bin/grunt task_name``), the Gruntfile.js script
is launched. The ``app_config.js`` is loaded and passed to the GruntConfigBuilder which search all configured
folders to find tasks and target. It then build a *Grunt* config object, and the task_name provided in the
command line is run (or the default task if none is provided).

.. _add an external bundle using Grunt:

Adding an external bundle using Grunt
-------------------------------------

This section explains how to exploit in your application a bundle providing its own *Grunt* tasks and/or task
tagets.

If you take a closer look at the (open-orchestra-cms-bundle)(https://github.com/open-orchestra/open-orchestra-cms-bundle),
you will see it does not contain the media administration part. To manage the media, you have to add the
(open-orchestra-media-admin-bundle)[https://github.com/open-orchestra/open-orchestra-media-admin-bundle].
So this bundle can be taken as an example to illustrate this section. 

The ``open-orchestra-media-admin-bundle`` comes with its own javascript and css files needing to be added
to the application assets files. Assuming you have installed the bundle using composer, you still have to
configure *Grunt* to use the bundle targets.

For that purpose, you only need to update the ``app_config.js``. As the bundle only contains task targets
located in the ``GruntTasks/Targets`` folder, you only have to add this path in the targetsDir attribute of
the ``app_config.js``. Something like:

.. code-block:: javascript

    targetsDir: [
       './grunt/targets',
       './vendor/open-orchestra/open-orchestra-cms-bundle/GruntTasks/Targets',
       './vendor/open-orchestra/open-orchestra-media-admin-bundle/GruntTasks/Targets'
    ]

If the bundle was introducing new *Grunt* tasks, the tasksDir attribute should have been updated the same way.

*Grunt* is now aware of the different targets present in the ``open-orchestra-media-admin-bundle``, but you
still have to associate them to a main task for them to be played.

The ``open-orchestra-media-admin-bundle`` introduces, three targets: one to create new symlinks, one to
concatenate some media related js and the last to concatenate media related css files.

You should add the ``concat:media_js`` target to the main javascript task by modifying the main javascript
task (``application_root_folder/grunt/tasks/javascript_task.js``):

.. code-block:: javascript

   module.exports = function(grunt) {
      grunt.registerTask(
         'javascript',
         'Main project task to generate javascripts',
         [
            'coffee:discovering',
            'coffee:compile',
            'concat:smartadmin_js',
            'concat:lib_js',
            'concat:orchestra_js',
            'concat:media_js',
            'concat:all_js'
         ]
      );
   };

When the ``javascript`` task will be run, the ``concat:media_js`` task will now be called, and a ``media.js``
file will be produced.

You can do the same for the stylesheets by modifying the main css task
(``application_root_folder/grunt/tasks/css_task.js``):

.. code-block:: javascript

   module.exports = function(grunt) {
      grunt.registerTask(
         'css',
         'Main project task to generate stylesheets',
         [
            'less:discovering',
            'less',
            'concat:lib_css',
            'concat:smartadmin_patches_css',
            'concat:orchestra_css',
            'concat:media_css',
            'concat:pre_smartadmin_css',
            'concat:post_smartadmin_css',
            'cssmin'
         ]
      );
   };

When the ``css`` task will be run, the ``concat:media_css`` task will now be called, and a ``media.css`` file
will be produced.

To include the ``media.js`` file to the final and unique javascript file used by the Open Orchestra Back Office,
alter the ``application_root_folder/grunt/targets/concat.all_js.js`` file:

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

That way, when the ``concat:all_js`` target will be called, the ``all.js`` file will include the
``open-orchestra-media-admin-bundle`` javascripts.

A similar modification on the stylesheets is to be done by modifying the
``application_root_folder/grunt/targets/concat.post_smartadmin_css.js`` file:

.. code-block:: javascript

    module.exports = {
       src: [
          'web/built/smartadminpatches.css',
          'web/built/orchestra.css',
          'web/built/media.css'
       ],
       dest: 'web/css/postsmartadmin.css'
    };

As for the javascript, the ``postsmartadmin.css`` file will now include the media stylesheets.

Now you can run the Grunt command (``./node_modules/.bin/grunt``) to regenerate the ``all.js`` and
``postsmartadmin.css`` files. If you check these files, you should see the ``open-orchestra-media-admin-bundle``
assets.


.. _add your specific tasks / targets to your bundles:

Adding your specific tasks/targets to your bundles
--------------------------------------------------

At last, you may need to know how to create your specific tasks for your own bundle. As the process is the
same for the javascript and stylesheet files, we will only talk about javascript files.

Let's assume you have created the ``FooBundle`` and want to manage its assets with Grunt.

As seen in the previous section, concatenation task is resolved in two passes. The first pass groups
files by functionnality and the second pass glues the functionnalities together. While the second
pass is described in the application (it depends on the used bundles), the first pass is described
by the bundle itself. This is done by adding an entry in the main concat task.

First create a directory to put all your tasks targets (``GruntTasks/Targets`` for instance). Then you can
create a *Grunt* task targets file describing the files to append and naming the file to output the
concatenation. The *Grunt* task target file name must follow a specific pattern: TASK_NAME.TARGET_NAME.js.
The task loader wil use that name to recreate the main configuration. In our case, we want to create
a target named foojs to the concat task, so name your file ``concat.foojs.js``. This file can be as
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
