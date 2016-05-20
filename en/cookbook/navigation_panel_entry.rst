How to Create a Navigation Panel Entry
======================================

Suppose you created a dedicated custom collection in your mongo database, ``country``.

You want to create a entry, ``Country``, in the OpenOrchestra Back Office navigation menu to display all the records of the country collection in the data table used in OpenOrchestra.

You want this entry under a more generic one, ``Reference data``, which is just a menu container for all your reference data collections but display no information to Back Office screen when clicked.
     

Top Menu
~~~~~~~~

First one, you will create the top menu, Reference Data.

.. code-block:: yaml

    # src/Acme/Bundle/BackBundle/Resources/config/navigation_panel.yml

    services:

        # ...

        acme.navigation_panel.reference:
            class: OpenOrchestra\Backoffice\NavigationPanel\Strategies\TopMenuPanelStrategy
            arguments:
                - reference
                - 300
            tags:
                - { name: open_orchestra_backoffice.navigation_panel.strategy }

Of course, all yaml should be loaded, for example, in the Dependency Injection Extension of your bundle (`Symfony Dependency Injection Extension`_).

Argument ``reference`` specifies a nickname for your entry. One of the purposes of this argument is to use this nickname to attach another menu entry at this entry.

Argument ``300`` specifies an order for your entry. A lower value will be displayed first.

The tag ``open_orchestra_backoffice.navigation_panel.strategy`` specifies that this service defines a menu entry.

Second Level Menu
~~~~~~~~~~~~~~~~~

The class ``OpenOrchestra\Backoffice\NavigationPanel\Strategies\AdministrationPanelStrategy`` is used in OpenOrchestra to create the data table entries.

But this class automatically display a twig from ``OpenOrchestraBackofficeBundle:BackOffice:Include/NavigationPanel/Menu/Administration/country.html.twig`` with country as nickname for the menu entry service.

So you need to extend ``OpenOrchestra\Backoffice\NavigationPanel\Strategies\AbstractNavigationStrategy``

.. code-block:: php

    // src/Acme/Bundle/BackBundle/NavigationPanel/Strategies/CountryPanelStrategy.php
    
    namespace Acme\Bundle\BackBundle\NavigationPanel\Strategies;
    
    use OpenOrchestra\Backoffice\NavigationPanel\Strategies\AbstractNavigationStrategy;
    use Symfony\Component\Translation\TranslatorInterface;
    
    /**
     * Class CountryPanelStrategy
     */
    class CountryPanelStrategy extends AbstractNavigationStrategy
    {
        /**
         * @return string
         */
        public function show()
        {
            return $this->render('AcmeBackBundle:AdministrationPanel:country.html.twig', array('datatableParameterName' => $this->name));
        }
    }

And then create your twig

.. code-block:: twig

    {# src/Acme/Bundle/BackBundle/Resources/views/AdministrationPanel/country.html.twig #}

    <li>
        <a
            href="#country/list"
            id="nav-country"
            data-url="{{ path('acme_api_country_list') }}"
            data-add="{{ path('acme_api_country_new') }}"
            data-datatable-parameter-name="{{ datatableParameterName }}"
            title="{{ 'acme.country'|trans }}"
            >
            {{ 'acme.country'|trans }}
        </a>
    </li>

Be carreful that the hash ``#country/list`` will be intercept by a backbone router with the pattern ``:entityType/list``.

The router will search the link with the html id ``nav-:entityType``, in this case ``nav-country`` to create the view.

Now you can create the service corresponding to your strategy.

.. code-block:: yaml

    # src/Acme/Bundle/BackBundle/Resources/config/navigation_panel.yml

    services:

        # ...

        acme.navigation_panel.country:
            class: Acme\Bundle\BackBundle\NavigationPanel\Strategies\CountryPanelStrategy
            arguments:
                - country
                - 350
                - reference
                - ROLE_ACCESS_COUNTRY
                - %acme.navigation_panel.country.parameters%
                - @translator
            tags:
                - { name: open_orchestra_backoffice.navigation_panel.strategy }

Argument ``country`` specifies a nickname for your entry.

Argument ``350`` specifies an order for your entry.

Argument ``reference`` specifies the parent menu by using his nickname.

Argument ``ROLE_ACCESS_COUNTRY`` specifies the role that the Back Office user needs to see this entry.

Argument ``%acme.navigation_panel.country.parameters%`` AND ``@translator`` are used to set the parameters of the data table (see `Navigation panel`_).

Here is an example for ``%acme.navigation_panel.country.parameters%``

.. code-block:: yaml

    # src/Acme/Bundle/BackBundle/Resources/config/datatable_parameter.yml

    parameters:
        open_orchestra_backoffice.navigation_panel.content_type.parameters :
            -
              name : country_id
              title : acme.table.country.id
              activateColvis : true
              searchField : text
            -
              name : country_name
              title : acme.table.country.label
              activateColvis : true
              searchField : text

The tag ``open_orchestra_backoffice.navigation_panel.strategy`` specifies that this service defines a menu entry.

.. _`Symfony Dependency Injection Extension`: http://symfony.com/doc/current/cookbook/bundles/extension.html
.. _`Navigation panel`: en/developer_guide/navigation_panel.rst 

