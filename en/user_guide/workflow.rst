Workflow
========

Open Orchestra allows to have a publication workflow.
It is a series of steps to achieve for the publication of a node or a content before it can be displayed on Front Office.

Status
------

Each version of a node or a content has a status, changing it allows to pass the publication workflow steps.
The users can define the status which will make up their workflow as long as there is one initial and one final status.

* An **initial** status is the first workflow status (assigned to a node or a content just after its creation).
* A **final** status is the last workflow status (which allows the display on the Front Office).

Status creation
~~~~~~~~~~~~~~~

* **Name** (required): status name
* **Published**: if this status is final
* **Initial**: if this status is initial
* **Label**: status label in all available languages
* **Color** (required): color used on the node (or content) status

.. image:: ../../images/status_form.png

Roles
-----

Open Orchestra allows to create roles.

* **Name**: role name
* **Description**: role description in all available languages.

.. image:: ../../images/role_form.png

See also `group management`_ to know how to give roles to the users.

Transitions
~~~~~~~~~~~

Transition allows users to update a node or a content from one status to another.

The roles also allow to create a transition between statuses. The selection of the two statuses in the role form will define the transition.

.. image:: ../../images/role_transition.png

The user with this role will be able to change the statuses of a node or content from the first one to the second one.

.. image:: ../../images/status_transition.png


.. _group management: /en/user_guide/user.rst
