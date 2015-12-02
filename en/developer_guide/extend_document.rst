Extend document and repository
==============================

Use case
----------

OpenOrchestra put to the users and developpers a set of entities, for example the content entity, functionnal kernel of a CMS.
For specific use, It could be necessary to extend the model of an entity and its repository, i.e. the class which allows to load the instances of this entity.
 

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

 .. code-block:: php
    <?php
    namespace MyBundle\Repository;
    
    use OpenOrchestra\ModelBundle\Repository\ContentRepository as BaseContentRepository;
    /**
     * Class ContentRepository
     */
    class ContentRepository extends BaseContentRepository
    {