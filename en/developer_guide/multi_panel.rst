Add panel to an administration view
===================================

Context
-------

In Open Orchestra, if you want to edit an element, you can only display the full form. In some cases
you want to embillish the edition by splitting the full form in some smaller one.

Open Orchestra already provides you a way to `use a custom Backbone view`_.
This solution may be possible but will require a large customization of the form view.

To prevent you from doing this work, Open Orchestra provides a way to add multiple tab in your edition form.

Panel System
~~~~~~~~~~~~

Each element facade contains a list of links that may be used to display more specific information about them.
To display a new panel, add a link to the facade, prefixed by ``_self_panel``.

.. code-block:: php

    $linkName = "_self_panel_" + $position + "_" + $panelTitle;
    $facade->addLink($linkName, $route);

The link name is a key to find the link later.
Open Orchestra also uses this key to configure your panel:

- Add a number after "_self_panel" prefixed by "_" to choose the position of your tab (begin with 1 because
 the ``_self_form`` link will always be in position 0)
- Add the title of your panel after the position prefixed by "_" to choose the tab name

Example
~~~~~~~

Here is an example of how the panel is used to add a workflow form to Users page.

.. image:: ../../images/user_panel_form.png

To add this link without modifying the ``UserTransformer``, we recommand to dispatch an event subscriber
like ``UserFacadeEvents::POST_USER_TRANSFORMATION`` :

.. code-block:: php

    class AddWorkFlowLinkSubscriber implements EventSubscriberInterface
    {
        protected $router;

        /**
         * @param UrlGeneratorInterface $router
         */
        public function __construct(UrlGeneratorInterface $router)
        {
            $this->router = $router;
        }

        /**
         * @param UserFacadeEvent $event
         */
        public function postUserTransformation(UserFacadeEvent $event)
        {
            $facade = $event->getUserFacade();
            $facade->addLink('_self_panel_2_workflow_right',
                $this->router->generate($workflowRouteName,
                    $workflowParams,
                    UrlGeneratorInterface::ABSOLUTE_URL));
        }

        /**
         * @return array The event names to listen to
         */
        public static function getSubscribedEvents()
        {
            return array(
                UserFacadeEvents::POST_USER_TRANSFORMATION => 'postUserTransformation',
            );
        }
    }

Register the event subscriber as a service in a configuration file :

.. code-block:: yml

    parameters:
        open_orchestra_workflow_function_admin.subscriber.add_workflow_link.class: OpenOrchestra\WorkflowFunctionAdminBundle\EventSubscriber\AddWorkFlowLinkSubscriber
    services:
        open_orchestra_workflow_function_admin.subscriber.add_workflow_link:
            class: %open_orchestra_workflow_function_admin.subscriber.add_workflow_link.class%
            arguments:
                - @router
            tags:
                - { name: kernel.event_subscriber }

.. _`use a custom Backbone view`: /en/developer_guide/specific_backbone_view.rst
