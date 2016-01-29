Extend document and repository
==============================

Use case
----------

Open Orchestra presents a list of model object to the integrators.
To customize those objects, it could be necessary to extend the implemented documents and repositories.
 

How to
------

These extensions will be done by creating extended classes for document (ODM context) or repository.
To reference these classes, the following lines will be added to config.yml.

.. code-block:: yaml

    open_orchestra_model:
        document:
            content:
                class: "MyBundle\Document\Content"
                repository: "MyBundle\Repository\ContentRepository"
 
The header of the two extended classes could be :
 
Extended Content
~~~~~~~~~~~~~~~~

 .. code-block:: php

    <?php
    namespace MyBundle\Document;
    
    use OpenOrchestra\ModelBundle\Document\Content as BaseContent;
    use Doctrine\ODM\MongoDB\Mapping\Annotations as ODM;
    /**
     * Extended Class Content
     * @ODM\Document(
     *   collection="content",
     *   repositoryClass="MyBundle\Repository\ContentRepository"
     * )
     */
    class Content extends BaseContent
    {

Extended Content Repository
~~~~~~~~~~~~~~~~~~~~~~~~~~~

 .. code-block:: php

    <?php
    namespace MyBundle\Repository;
    
    use OpenOrchestra\ModelBundle\Repository\ContentRepository as BaseContentRepository;
    /**
     * Class ContentRepository
     */
    class ContentRepository extends BaseContentRepository
    {
    
As OpenOrchestra use interface for dependency injection, it is necessary to update the configuration with the new extended class.

.. code-block:: yaml

    resolve_target_documents:
        OpenOrchestra\ModelInterface\Model\ContentInterface: MyBundle\Document\Content

