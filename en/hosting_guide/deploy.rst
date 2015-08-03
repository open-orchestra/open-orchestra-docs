Orchestra deployment on integration environment
===============================================

This tutorial is going to describe step by step how you can deploy the Open Orchestra
project on the integration environment:

Install Gem and Bundler
-----------------------

In order to separate all the project of your computer, we use `bundler`_ to execute only
the specified version of `capistrano`_.

.. code-block:: bash

    $ aptitude install ruby ruby-dev
    $ gem install bundler

Install capifony
----------------

In the root directory of your project, run the command

.. code-block:: bash

    $ bundle install

SSH configuration
-----------------

Make sure that your ssh configuration is ready and your personal public key is installed on
the integration server

.. code-block:: bash

    # ~/.ssh/config
    Host open_orchestra_front_inte
        Hostname 10.0.1.246
        User open_orchestra_front_inte
        ForwardAgent yes
    Host open_orchestra_media_inte
        Hostname 10.0.1.246
        User open_orchestra_media_inte
        ForwardAgent yes
    Host open_orchestra_backoffice_inte
        Hostname 10.0.1.246
        User open_orchestra_backoffice_inte
        ForwardAgent yes

Test the command
----------------

Run the following command to test the installation and connection to the server

.. code-block:: bash

    $ cap inte deploy:log_revision

Deploy
------

Before deploying the project, make sure that the composer.lock file is up-to-date on the master branch

.. code-block:: bash

    $ ./composer.phar update
    $ git add composer.lock
    $ git commit -m "update vendor"
    $ git pull --rebase origin master
    $ git push origin master:update_vendor

Once you are ready (passing tests for instance), you can merge in the branch you want to deploy

Then you can run the deploy command in the project directory

.. code-block:: bash

    $ cap inte deploy

Once this is done, your server has been updated.

.. _`bundler`: http://bundler.io/
.. _`capistrano`: http://capistranorb.com/
