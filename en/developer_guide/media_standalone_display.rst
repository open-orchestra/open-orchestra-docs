Medias display
==============

Context
-------

To improve your website performances, a common way is to download the page data from
multiple servers. In fact, in the HTTP protocol, a browser can make only two parallel
requests to the same domain. Recent browsers (such as ``Chrome`` or ``Firefox`` can perform
up to 10 simultaneous requests). In the following documentation, we will just assume that
browsers can make only two simultaneous requests to the same domain.

An easy way to load and display the medias would be to add a new virtual host to your existing Open Orchestra
installation. This will allow your browser to increase the number of parallel requests that can be done as
several domain are available. It will then reduce the global latency of each page's download

Request scheme:

.. image:: ../../images/two_parallel.gif
.. image:: ../../images/four_parallel.gif

This solution is not ideal because you will need to boot the whole Open Orchestra
kernel each time you will request an image.

Open Orchestra Solution
-----------------------

A simple solution would be to install only the ``open-orchestra-media-bundle`` as a single
``Symfony`` application.

Basic installation
~~~~~~~~~~~~~~~~~~

In order to install all the Symfony packages, we recommend you to use the
``open-orchestra-base-bundle``. Your ``composer.json`` file should look like:

.. code-block:: json

    "require": {
        "incenteev/composer-parameter-handler": "~2.0",
        "open-orchestra/open-orchestra-base-bundle": "*",
        "open-orchestra/open-orchestra-media-bundle": "*"
    },

Then enable all the required bundles in your ``AppKernel.php`` file:

.. code-block:: php

    new Symfony\Bundle\FrameworkBundle\FrameworkBundle(),
    new Symfony\Bundle\SecurityBundle\SecurityBundle(),
    new Symfony\Bundle\TwigBundle\TwigBundle(),
    new Sensio\Bundle\FrameworkExtraBundle\SensioFrameworkExtraBundle(),

    new Doctrine\Bundle\MongoDBBundle\DoctrineMongoDBBundle(),
    new Knp\Bundle\GaufretteBundle\KnpGaufretteBundle(),

    new OpenOrchestra\BaseBundle\OpenOrchestraBaseBundle(),
    new OpenOrchestra\MediaBundle\OpenOrchestraMediaBundle(),
    new OpenOrchestra\MediaModelBundle\OpenOrchestraMediaModelBundle(),

Installation with the database
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In the case that you will require to request the database to extract more
information about the ``media`` object for instance, you will need to create two
documents implementing the interfaces : ``EmbedKeywordInterface`` and
``TranslatedValueInterface``. Those documents should be created because the ``Media``
document has some relations to some documents in an external bundle.

The ``EmbedKeyword`` document :

.. code-block:: php

    use Doctrine\ODM\MongoDB\Mapping\Annotations as ODM;
    use OpenOrchestra\ModelInterface\Model\EmbedKeywordInterface;
    use OpenOrchestra\ModelInterface\Model\KeywordInterface;

    /**
     * @ODM\EmbeddedDocument
     */
    class EmbedKeyword implements EmbedKeywordInterface, KeywordInterface
    {
        public static function createFromKeyword(KeywordInterface $keyword)
        {
            trigger_error('this method should not be used in the demo');

            $keyword = new EmbedKeyword();
            $keyword->setLabel($keyword->getLabel());

            return $keyword;
        }

        /**
         * @ODM\Id()
         */
        protected $id;

        /**
         * @ODM\Field(type="string")
         */
        protected $label;

        public function getId()
        {
            return $this->id;
        }

        public function getLabel()
        {
            return $this->label;
        }

        public function setLabel($label)
        {
            $this->label = $label;
        }
    }

The ``TranslatedValue`` document :

.. code-block:: php

    use Doctrine\ODM\MongoDB\Mapping\Annotations as ODM;
    use OpenOrchestra\ModelInterface\Model\TranslatedValueInterface;

    /**
     * @ODM\EmbeddedDocument
     */
    class TranslatedValue implements TranslatedValueInterface
    {
        /**
         * @ODM\Field(type="string")
         */
        protected $language;

        /**
         * @ODM\Field(type="string")
         */
        protected $value;

        public function setLanguage($language)
        {
            $this->language = $language;
        }

        public function getLanguage()
        {
            return $this->language;
        }

        public function setValue($value)
        {
            $this->value = $value;
        }

        public function getValue()
        {
            return $this->value;
        }
    }

Once the document has been created inside your bundle, you should configure the interface
resolution in the ``config.yml`` file:

.. code-block:: yaml

    doctrine_mongodb:
        resolve_target_documents:
                OpenOrchestra\ModelInterface\Model\TranslatedValueInterface: OpenOrchestra\MediaDemoBundle\Document\TranslatedValue
                OpenOrchestra\ModelInterface\Model\EmbedKeywordInterface: OpenOrchestra\MediaDemoBundle\Document\EmbedKeyword

You have now the opportunity to query the database to get any of the media stored inside.

Ease your installation
~~~~~~~~~~~~~~~~~~~~~~

To facilitate this installation, we provide you with the ``open-orchestra-media-demo``
repository which implements all those modifications.

To install it :

.. code-block:: bash

    composer create-project open-orchestra/open-orchestra-media-demo ./
