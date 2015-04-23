SmartAdmin
==========

`SmartAdmin`_ is a responsive admin theme which uses Bootstrap made by Myorange.

Open Orchestra's back office uses the specific design of SmartAdmin
and only some of these JavaScript components (JarvisWidget and SmartNotification).

This doc will help you to add new features in the back office and respect its general design.

SmartConfirm
------------

Description
~~~~~~~~~~~

The ``smartConfirm`` function allows to display a confirmation message.
It uses the ``SmartMessageBox`` function of component SmartNotification.
It is called during various events like the deleting of an item (nodes, blocks, contents, ...).

It must be used in replacement of the standard JavaScript confirm.

A confirmation message is composed of a logo, a title, a description and two buttons (Yes/No).

.. image:: ../../images/smartconfirm.png

The function ``smartConfirm`` takes 4 parameters:

1.  the logo css class.
2.  the message title.
3.  the message description.
4.  an array of callback functions to be called when buttons are clicked and the parameters of callbacks functions.

The array must contain three keys ``yesCallback``, ``NoCallback`` and ``callBackParams`` .

The keys ``yesCallback`` and ``NoCallback``
which refer respectively to the functions managing the click event on Yes and No buttons.
The key ``callBackParams`` is an array which contains the parameters for callbacks functions.

View
~~~~

SmartConfirm uses two templates, one for buttons (``smartConfirmButton._tpl.twig``) and another
to display the logo and the title (``smartConfirmTitle._tpl.twig``).
**The title does not need to include a question mark as the template adds one at the end of it**.

Translation
~~~~~~~~~~~

The translation of the buttons is done with the translation component of Symfony in the template.
For title and description, they must be translated before being passed to the ``smartConfirm`` function .

Example
~~~~~~~

This example in coffeeScript show a confirmation message.
The variables ``confirm_title`` and ``confirm_text`` contains the translated title and the translated description:

.. code-block:: coffeescript

  smartConfirm(
    'fa-trash-o',
    confirm_title,
    confirm_text,
    callBackParams:
      url: url
    yesCallback: (params) ->
      $.ajax
        url: params.url
        method: 'DELETE'
        success: (response) ->
          if redirectUrl != undefined
            displayMenu(redirectUrl)
          else
            redirectUrl = appRouter.generateUrl 'showDashboard'
            displayMenu(redirectUrl)
          return
        error: (response) ->
          $('.modal-footer', this.el).html response.responseJSON.error.message
          return
    noCallback: ->
      $("#OrchestraBOModal").modal "show"
  )

.. _`SmartAdmin`: https://bootstraphunter.com/theme/smartadmin-responsive-webapp-frontend-BSH01
