Form Type List :
================

Open Orchestra consists of many modules each comprising a certain number of form, here are the
list of different form type.

- `cms bundle`_
- `backofficebundle bundle`_
- `group bundle`_
- `user admin bundle`_
- `display bundle`_
- `media admin bundle`_
- `model bundle`_
- `model interface bundle`_
- `user bundle`_
- `workflow function bundle`_

Table legend :
- Class Name : it's the class name object
- Alias / Form type name : it's form name, he is specified in the object or in the configuration files
- Use to : it's the use case
- Type : More directly, in what form we find

.. _cms bundle:

CMS Bundle :
------------

.. _backofficebundle bundle:

BackofficeBundle:
~~~~~~~~~~~~~~~~~
.. code-block:: yaml

    # open-orchestra-cms-bundle/BackofficeBundle/Form/Type

+-----------------------------------+-----------------------------------+---------------------------+-------+
| Class Name                        | Alias / Form type name            | Use to                    | Type  |
+===================================+===================================+===========================+=======+
| ``AbstractGroupChoiceType``       | ``oo_group_choice``               |Add group list field       | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``ApiClientType``                 | ``oo_api_client``                 |Create the API Client Form | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``AreaType``                      | ``oo_area``                       |Area and sub area template | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``BlockChoiceType``               | ``oo_block_choice``               |Generate a choice field to | field |
|                                   |                                   |the list of existing block |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``BlockType``                     | ``oo_block``                      |Create the Block Form      | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``ColorPickerType``               | ``oo_color_picker``               |Add colopiker module on    | field |
|                                   |                                   |video type field           |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``ContentType``                   | ``oo_content``                    |Create the Contents Form   | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``ContentTypeType``               | ``oo_content_type``               |Create Content Type Form   | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``ExistingBlockChoiceType``       | ``oo_existing_block``             |Add existing block list    | field |
|                                   |                                   |field                      |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``FieldOptionType``               | ``oo_field_option``               |Add a field in             | field |
|                                   |                                   |FieldTypeType by           |       |
|                                   |                                   |Subscriber                 |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``FieldTypeType``                 | ``oo_field_type``                 |Add a fields form parts on | field |
|                                   |                                   |Content Type by Subscriber |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``GroupType``                     | ``oo_group``                      |Create Group Form          | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``KeywordType``                   | ``oo_keyword``                    |Create Keyword Form        | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``NodeType``                      | ``oo_node``                       |Create Node Form           | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``OrchestraChoiceType``           | ``choice``                        |Add generic list field     | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``RedirectionType``               | ``oo_redirection``                |Create Redirection Form    | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``RoleType``                      | ``oo_role``                       |Create Roles Form          | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``SiteAliasType``                 | ``oo_site_alias``                 |Add alias field on Site    | field |
|                                   |                                   |Form                       |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``SiteType``                      | ``oo_site``                       |Create Site Form           | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``StatusType``                    | ``oo_status``                     |Create Status Form         | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``TemplateType``                  | ``oo_template``                   |Create Template Form       | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``ThemeType``                     | ``oo_theme``                      |Create Theme Form          | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``TinymceType``                   | ``oo_tinymce``                    |Add tinymce textarea field | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``TranslatedValueCollectionType`` | ``oo_translated_value_collection``|Add translated list field  | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``TranslatedValueType``           | ``oo_translated_value``           |Add language field on      | field |
|                                   |                                   |translated value           |       |
|                                   |                                   |collection                 |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``VideoType``                     | ``oo_video``                      |Add a form part to the     | field |
|                                   |                                   |video configuration        |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+

.. code-block:: yaml

    # open-orchestra-cms-bundle/BackofficeBundle/Form/Type/Component

+-----------------------------------+-----------------------------------+---------------------------+-------+
| Class Name                        | alias / form type name            | Use to                    | Type  |
+===================================+===================================+===========================+=======+
| ``ChoicesOptionType``             | ``oo_choices_option``             |Add options list           | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``ContentChoiceType``             | ``oo_content_choice``             |                           | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``ContentSearchType``             | ``oo_content_search``             |Add content search field   | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``ContentTypeChoiceType``         | ``oo_content_type_choice``        |Add content type list      | field |
|                                   |                                   |field                      |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``DateWidgetOptionType``          | ``oo_date_widget_option``         |                           | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``FieldChoiceType``               | ``oo_field_choice``               |                           | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``KeywordsChoiceType``            | ``oo_keywords_choice``            |Add a keyword field        | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``NodeChoiceType``                | ``oo_node_choice``                |Add content list field     | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``OperatorChoiceType``            | ``oo_operator_choice``            |Add logic operator list    | field |
|                                   |                                   |field                      |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``RoleChoiceType``                | ``oo_role_choice``                |Add roles list field       | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``SiteChoiceType``                | ``oo_site_choice``                |Add sites list field       | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``ThemeChoiceType``               | ``oo_theme_choice``               |Add template and source    | field |
|                                   |                                   |page fields                |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+

.. _group bundle:

GroupBundle:
~~~~~~~~~~~~

.. code-block:: yaml

    # open-orchestra-cms-bundle/GroupBundle/Form/Type

+-----------------------------------+-----------------------------------+---------------------------+-------+
| Class Name                        | alias / form type name            | Use to                    | Type  |
+===================================+===================================+===========================+=======+
| ``GroupDocumentType``             | ``oo_group_choice``               |Add groups list            | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+

.. _user admin bundle:

UserAdminBundle:
~~~~~~~~~~~~~~~~
.. code-block:: yaml

    # open-orchestra-cms-bundle/UserAdminBundle/Form/Type

+-----------------------------------+-----------------------------------+---------------------------+-------+
| Class Name                        | alias / form type name            | Use to                    | Type  |
+===================================+===================================+===========================+=======+
| ``RegistrationUserType``          | ``oo_registration_user``          |Create User Registration   | form  |
|                                   |                                   |Form                       | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``UserType``                      | ``oo_user``                       |Create User Form           | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+

.. _display bundle:

Display Bundle:
---------------

DisplayBundle:
~~~~~~~~~~~~~~

.. code-block:: yaml

    # open-orchestra-display-bundle/DisplayBundle/Form/Type

+-----------------------------------+-----------------------------------+---------------------------+-------+
| Class Name                        | alias / form type name            | Use to                    | Type  |
+===================================+===================================+===========================+=======+
| ``ContactType``                   | ``Contact``                       |Create Contact Form        | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+

.. _media admin bundle:

Media Admin Bundle:
-------------------

MediaAdminBundle:
~~~~~~~~~~~~~~~~~

.. code-block:: yaml

    # open-orchestra-media-admin-bundle/MediaAdminBundle/Form/Type

+-----------------------------------+-----------------------------------+---------------------------+-------+
| Class Name                        | alias / form type name            | Use to                    | Type  |
+===================================+===================================+===========================+=======+
| ``FolderType``                    | ``oo_folder``                     |Create Media Folder Form   | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``MediaCropType``                 | ``oo_media_crop``                 |Create Media Crop Form     | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``MediaMetaType``                 | ``oo_media_meta``                 |Create Media Meta Data     | form  |
|                                   |                                   |Form                       |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``MediaType``                     | ``oo_media``                      |Create Media File Upload   | form  |
|                                   |                                   |Form                       |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``SiteForFolderChoiceType``       | ``oo_site_for_folder_choice``     |Add sites list field       | field |
|                                   |                                   |to Media Folder Form       |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+

.. code-block:: yaml

    # open-orchestra-media-admin-bundle/MediaAdminBundle/Form/Type/Component

+-----------------------------------+-----------------------------------+---------------------------+-------+
| Class Name                        | alias / form type name            | Use to                    | Type  |
+===================================+===================================+===========================+=======+
| ``MediaChoiceType``               | ``oo_media_choice``               |Add media list field by    | field |
|                                   |                                   |modal                      |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+

.. _model bundle:

Model Bundle:
-------------

modelBundle:
~~~~~~~~~~~~

.. code-block:: yaml

    # open-orchestra-model-bundle/ModelBundle/Form/Type

+-----------------------------------+-----------------------------------+---------------------------+-------+
| Class Name                        | alias / form type name            | Use to                    | Type  |
+===================================+===================================+===========================+=======+
| ``GroupSiteChoiceType``           | ``oo_group_site_choice``          |Add sites list field to    | field |
|                                   |                                   |the Group Form             |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``SiteThemeChoiceType``           | ``oo_site_theme_choice``          |Add themes list field to   | field |
|                                   |                                   |the Site Form              |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``StatusChoiceType``              | ``oo_status_choice``              |Add status field (draft,   | field |
|                                   |                                   |pending, published) to     |       |
|                                   |                                   |the Roles Form             |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``WorkflowRoleChoiceType``        | ``oo_workflow_role_choice``       |Add roles list field       | field |
|                                   |                                   |to the Workflow Function   |       |
|                                   |                                   |Form                       |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+

.. _model interface bundle:

Model Interface Bundle:
-----------------------

ModelInterfaceBundle:
~~~~~~~~~~~~~~~~~~~~~

.. code-block:: yaml

    # open-orchestra-model-interface-bundle/ModelInterfaceBundle/Form/Type

+-----------------------------------+-----------------------------------+-------------------------------+-------+
| Class Name                        | alias / form type name            | Use to                        | Type  |
+===================================+===================================+===============================+=======+
| ``AbstractGroupSiteChoiceType``   | ``oo_group_site_choice``          | see  ``GroupSiteChoiceType``  | field |
+-----------------------------------+-----------------------------------+-------------------------------+-------+
| ``AbstractSiteThemeChoiceType``   | ``oo_site_theme_choice``          | see  ``SiteThemeChoiceType``  | field |
+-----------------------------------+-----------------------------------+-------------------------------+-------+
| ``AbstractStatusChoiceType``      | ``oo_status_choice``              | see  ``StatusChoiceType``     | field |
+-----------------------------------+-----------------------------------+-------------------------------+-------+
| ``AbstractWorkflowRoleChoiceType``| ``oo_workflow_role_choice``       | see                           | field |
|                                   |                                   | ``WorkflowRoleChoiceType``    |       |
+-----------------------------------+-----------------------------------+-------------------------------+-------+

.. _user bundle:

User Bundle:
------------

UserBundle:
~~~~~~~~~~~

.. code-block:: yaml

    # open-orchestra-user-bundle/UserBundle/Form/Type

+-----------------------------------+-----------------------------------+---------------------------+-------+
| Class Name                        | alias / form type name            | Use to                    | Type  |
+===================================+===================================+===========================+=======+
| ``ChangePasswordUserType``        | ``oo_user_change_password``       |Change Password User Form  | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+

.. _workflow function bundle:

Workflow Function Bundle:
-------------------------

WorkflowFunctionBundle:
~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: yaml

    # open-orchestra-workflow-function-bundle/WorkflowFunctionBundle/Form/Type

+-----------------------------------+-----------------------------------+---------------------------+-------+
| Class Name                        | alias / form type name            | Use to                    | Type  |
+===================================+===================================+===========================+=======+
| ``WorkflowFunctionType``          | ``oo_workflow_function``          |Create Workflow Function   | form  |
|                                   |                                   |Form                       | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``WorkflowRightType``             | ``oo_workflow_right``             |Create Workflow Right Form | form  |
+-----------------------------------+-----------------------------------+---------------------------+-------+

.. code-block:: yaml

    # open-orchestra-workflow-function-bundle/WorkflowFunctionBundle/Form/Type/Component

+-----------------------------------+-----------------------------------+---------------------------+-------+
| Class Name                        | alias / form type name            | Use to                    | Type  |
+===================================+===================================+===========================+=======+
| ``AuthorizationType``             | ``oo_authorization``              |Add checkbox list by       | field |
|                                   |                                   |content type               |       |
+-----------------------------------+-----------------------------------+---------------------------+-------+
| ``WorkflowFunctionChoiceType``    | ``oo_workflow_function_choice``   |Add workflow choice field  | field |
+-----------------------------------+-----------------------------------+---------------------------+-------+
