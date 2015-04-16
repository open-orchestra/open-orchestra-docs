Server Configuration
====================

To know more about server configuration see `requirements`_.

Cron jobs
---------

Cron jobs are used for tasks (commands or shell scripts) to run periodically at fixed times, dates, or intervals.
Cron jobs typically automate system maintenance.

Cron jobs on Open Orchestra
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Open Orchestra has 2 cron jobs created with the provisioning:

* **Sitemap**: automatically generates sitemap files for every sites.
* **Robots**: automatically generates the robots.txt files for every sites.

Those tasks are launched every day at 2 am.
The schedule of the tasks is define in the ansible cron role.

For more information about the command which generates the sitemap.xml and the robots.txt see the documentation `sitemap and robots files`_

To modify the scheduling of the tasks, update variables in ``provisioning/roles/orchestraCron/vars/main.yml``.

Create a cron job
~~~~~~~~~~~~~~~~~

To add a cron job create a file named like your task in the ansible role ``provisioning/roles/orchestraCron/tasks``.

In your file use the ansible cron command:

.. code-block:: yaml

    cron: name="task description" min="minutes" hour="hour" day="day" month="month" job="job"

For more details about the cron command go see the documentation `ansible cron module`_.

Add your task in the file ``provisioning/roles/orchestraCron/tasks/main.yml``

.. code-block:: yaml

    - include: task.yml

The available variables are in ``provisioning/roles/orchestraCron/vars/main.yml``.

.. _requirements: /en/hosting_guide/requirements.rst
.. _sitemap and robots files:
.. _ansible cron module: http://docs.ansible.com/cron_module.html
