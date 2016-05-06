Add panel to an administration view
===================================

Context
-------

In Open Orchestra, if you want to edit an element, you can only display the full form. In some cases
you want to embellish the edition by splitting the full form into some smaller one.

Open Orchestra already provides you a way to `use a custom Backbone view`_.
This solution may be possible but will require a large customization of the form view.

To prevent you from doing this work, Open Orchestra provides a way to add multiple tabs in your edition form like in the user edit page.

.. image:: ../../images/user_panel_form.png

Panel System
~~~~~~~~~~~~

Each element facade contains a list of meta links that may be used to display specifics meta-information
or forms to add, modify or delete them.
The most commons links are :

- ``_self_add`` url to the add form action
- ``_self_form`` url to the edit form action
- ``_self_delete`` url to the delete form action
- ``_self_meta`` url to meta-information

All of these links are used by Open Orchestra Javascript code to send ajax calls and display different administration forms.
Edit page of administration items uses ``_self_form`` link to display the edit page.

To add a new panel with your own form to this one, add a link to the facade, prefixed by ``_self_panel``.

.. code-block:: php

    $facade->addLink("_self_panel_" + $linkName, $route);

Then add panel's title to the form template in the Controller of the panel

.. code-block:: php

         return $this->renderAdminForm($form, array('title' => $title));

Example
~~~~~~~

Here is an example of how the panel is used to add a workflow form to Users page.

To add this link without modifying the ``UserTransformer`` which creates the facade, we recommend to listen
``UserFacadeEvents::POST_USER_TRANSFORMATION`` with an event subscriber to modify the facade by your own after
the ``UserTransformer`` work:

.. code-block:: php

    class AddWorkFlowLinkSubscriber implements EventSubscriberInterface
    {
        protected $router;

        public function __construct(UrlGeneratorInterface $router)
        {
            $this->router = $router;
        }

        public function postUserTransformation(UserFacadeEvent $event)
        {
            $facade = $event->getUserFacade();
            $facade->addLink('_self_panel_workflow_right',
                $this->router->generate($workflowRouteName,
                    $workflowParams,
                    UrlGeneratorInterface::ABSOLUTE_URL));
        }

        public static function getSubscribedEvents()
        {
            return array(
                UserFacadeEvents::POST_USER_TRANSFORMATION => 'postUserTransformation',
            );
        }
    }

Register the event subscriber as a service in a configuration file:

.. code-block:: yaml

    parameters:
        open_orchestra_workflow_function_admin.subscriber.add_workflow_link.class: OpenOrchestra\WorkflowFunctionAdminBundle\EventSubscriber\AddWorkFlowLinkSubscriber
    services:
        open_orchestra_workflow_function_admin.subscriber.add_workflow_link:
            class: "%open_orchestra_workflow_function_admin.subscriber.add_workflow_link.class%"
            arguments:
                - \@router
            tags:
                - { name: kernel.event_subscriber }

Then add title to the ``formAction`` function in the ``WorkflowRightController``

.. code-block:: php

     /**
      * @Config\Route("/form/{userId}", name="open_orchestra_backoffice_workflow_right_form")
      * @Config\Method({"GET", "POST"})
      */
     public function formAction(Request $request, $userId)
     {
        // Generate the form

        $title = 'open_orchestra_user_admin.form.title';
        $title = $this->get('translator')->trans($title);

        return $this->renderAdminForm($form, array('title' => $title));
     }

.. _`use a custom Backbone view`: /en/latest/developer_guide/specific_backbone_view.html
