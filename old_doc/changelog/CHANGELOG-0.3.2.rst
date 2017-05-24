CHANGELOG for 0.3.2
===================

Url to see changes:

- `Cms bundle`_
- `Display bundle`_
- `Model bundle`_
- `Model interface`_
- `Front bundle`_
- `Base bundle`_
- `Base api bundle`_
- `Base api model bundle`_
- `Media bundle`_
- `User bundle`_
- `Theme bundle`_
- `Worflow function bundle`_

Possible BC breaker
-------------------

- The `Api\Serialize()` annotation should be given to the full class now
- Reference to ``LeftPanel`` in class are replace by ``NavigationPanel``
- You can use the annotation `OpenOrchestra\Mapping\Annotations\Search` for the mapping your entity for the dataTable search, 
  `futher informations in the documentation`_
- The annotation `OpenOrchestra\ModelInterface\Mapping\Annotations\Document` is moved to `open-orchestra-libs` (`OpenOrchestra\Mapping\Annotations\Document`)
- `OpenOrchestra\ModelInterface\Exceptions\MethodNotFoundException` is moved to `Mapping\Exceptions\MethodNotFoundException`
- `OpenOrchestra\ModelInterface\Exceptions\PropertyNotFoundException` is moved to `Mapping\Exceptions\PropertyNotFoundException`

Bug fixes
---------

New features
------------

Other changes
-------------

- You can now duplicate the node version you want
- You can duplicate the current version of the node
- I can specify that you have the workflow right on the content you have created

Deprecated method
-----------------

- In the `NodeInterface`, the methode `isEditable` has been replaced by the `AuthorizeEditionManager`

Suppressed method
-----------------

Configuration changes
---------------------

.. _`Cms bundle`: https://github.com/open-orchestra/open-orchestra-cms-bundle/compare/v0.3.1...v0.3.2
.. _`Display bundle`: https://github.com/open-orchestra/open-orchestra-display-bundle/compare/v0.3.1...v0.3.2
.. _`Model bundle`: https://github.com/open-orchestra/open-orchestra-model-bundle/compare/v0.3.1...v0.3.2
.. _`Model interface`: https://github.com/open-orchestra/open-orchestra-model-interface/compare/v0.3.1...v0.3.2
.. _`Front bundle`: https://github.com/open-orchestra/open-orchestra-front-bundle/compare/v0.3.1...v0.3.2
.. _`Base bundle`: https://github.com/open-orchestra/open-orchestra-base-bundle/compare/v0.3.1...v0.3.2
.. _`Base api bundle`: https://github.com/open-orchestra/open-orchestra-base-api-bundle/compare/v0.3.1...v0.3.2
.. _`Base api model bundle`: https://github.com/open-orchestra/open-orchestra-base-api-mongo-model-bundle/compare/v0.3.1...v0.3.2
.. _`Media bundle`: https://github.com/open-orchestra/open-orchestra-media-bundle/compare/v0.3.1...v0.3.2
.. _`User bundle`: https://github.com/open-orchestra/open-orchestra-user-bundle/compare/v0.3.1...v0.3.2
.. _`Theme bundle`: https://github.com/open-orchestra/open-orchestra-theme-bundle/compare/v0.3.1...v0.3.2
.. _`Worflow function bundle`: https://github.com/open-orchestra/open-orchestra-worflow-function-bundle/compare/v0.3.1...v0.3.2
.. _`futher informations in the documentation`: ../developer_guide/entity_list_ajax_pagination.html
