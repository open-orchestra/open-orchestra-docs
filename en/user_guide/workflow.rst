Workflow
========

In Open Orchestra, key contributions such as nodes and contents are subject to a publication workflow.
It allows several levels of validation by different people from creation to publication. Workflows
are fully customizable.

A workflow is composed of steps, each corresponding to a status. Each status is linked to one (or
several) other status by a transition. To change a content status or a node status, a contributor
must have a right mapping the corresponding transition.

For instance, the article content type could have a workflow represented by the following status:

    Draft => Pending => Published

In that configuration, three diffent types of contributors could be involved in the validation of an
article. A contributor create the content and make it in the Draft status. A second one is responsible
for a first step of validation and, if ok, put it in the Pending status. A last contributor is required
to publish the content on the Front Office.

So to create a workflow, an administrator needs to create the different status, then the transitions
linking those status, and finally assign rights to the contributors.

Status
------

Each version of a node or a content has a status representing its state (for instance draft or
published).
There are 3 types of status : 

* An **initial** status is the begining state of a workflow (automatically assigned to a node or a
  content just after its creation).
* A **final** status makes a content visible on the Front Office.
* All status that are not initial or final are **standard**

An administrator can define as many status as required to create his workflows.

Status creation
~~~~~~~~~~~~~~~

The status form asks for the following information:

* **Name** (required): status name
* **Published**: if this status is final
* **Initial**: if this status is initial
* **Label**: status label in all available languages
* **Color** (required): color representing the status (used on the node or content edit page)

.. image:: ../../images/status_form.png

Transitions
-----------

A transitions links two status together, for instance in the previous example, there is a transition
to change an article from Draft to Pending and another one to change it from Pending to Published.

As not all contributors may be allowed to change the status of an article, there is a right notion
related to the transitions. In fact in Open Orchestra, transitions are rights. So to create a new
transition an administrator only have to create a new right. In Open Orchestra, rights are called
Roles.

The role form asks for the following information:

* **Name**: role name
* **Description**: role description in all available languages.

.. image:: ../../images/role_form.png

The selection of two status in the role form will define a transition role, and implicitly this transition.

.. image:: ../../images/role_transition.png

This role creates a transition between Draft status and Pending status. So users with this role will
be able to change the status of a node or content from Draft to Pending. They will do this via a small
widget on the node edit page.

.. image:: ../../images/status_transition.png

See also `group management`_ to know how to give roles to the users.

.. _group management: /en/user_guide/user.rst
