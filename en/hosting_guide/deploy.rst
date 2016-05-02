Orchestra deployment on integration environment
===============================================

This tutorial is going to describe step by step how you can deploy the Open Orchestra
project on the integration environment.

To be able to deploy with `capistrano`_, your target environment should have the
requirements :

- `git`_ installed
- `composer`_ installed and executable as the ``composer`` command
- The user used to deploy and the one used to execute the php should be able to write
  in the cache and log directory at all time.

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
    Host open_orchestra_bo_inte_1-1
        Hostname 10.0.1.228
        User open_orchestra_bo_inte_1-1
        ForwardAgent yes
    Host open_orchestra_front_inte_1-1
        Hostname 10.0.1.228
        User open_orchestra_front_inte_1-1
        ForwardAgent yes
    Host open_orchestra_front2_inte_1-1
        Hostname 10.0.1.228
        User open_orchestra_front2_inte_1-1
        ForwardAgent yes
    Host open_orchestra_media_inte_1-1
        Hostname 10.0.1.228
        User open_orchestra_media_inte_1-1
        ForwardAgent yes

Test the command
----------------

Run the following command to test the installation and connection to the server

.. code-block:: bash

    $ cap 1.1 deploy:log_revision

Deploy
------

Before deploying the project, make sure that the ``composer.lock`` file is up-to-date on the master branch.

.. code-block:: bash

    $ cap inte composer:update_vendor

This task run ``composer update vendor`` on the server to update ``composer.lock`` and create a branch on GitHub.

Once you are ready (passing tests for instance), you can merge in the branch you want to deploy

Then you can run the deploy command in the project directory

.. code-block:: bash

    $ cap 1.1 deploy

Once this is done, your server has been updated.

.. _`git`: https://git-scm.com/
.. _`bundler`: http://bundler.io/
.. _`composer`: https://getcomposer.org/
.. _`capistrano`: http://capistranorb.com/
