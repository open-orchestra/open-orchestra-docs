HOW TO CREATE A NEW MEDIA TYPE
==============================

When a user upload a file in the media libray, a media document is created to manage it. The media library
assign automatically the file to a media type. Out of the box, Open Orchestra supports the following types:

 - Image (all files with mime-type 'image/*')
 - Audio (all files with mime-type 'audio/*')
 - Video (all files with mime-type 'video/*')
 - Pdf (all files with mime-type 'application/pdf')

All other type of file are mapped to a special fallback type: Default.

This cookbook shows you how to add your own media type to the media library.

Use Case
--------

To do this we will work with a non natively supported file type: the zip archive. Defining a media types
involves 3 steps:

 - Coding the creation of the document (via a file alternatives strategy)
 - Generating the thumbnail and alternatives (via a file alternatives strategy)
 - Coding the renderings of the alternatives, both in BO and FO (via a display media strategy)

For this exemple, the zip type have one alternative: a tar.gz version. The thumbnail in the media libray will
be as basic as a generic pictogram, the same for all zip media.

On the Front Office, the rendering of a zip media will be as simple as a link to download the file, regardless
it is the zip version or the tar.gz version. At last, in the Back Office, the zip archive will be presented
with a generic archive pictogram.

Creation of the document
------------------------

To create a FileAlternativeStrategy, you need to code a class implementing
`OpenOrchestra\MediaAdmin\FileAlternatives\FileAlternativesStrategyInterface`. For our need we can simplify
this extending the `OpenOrchestra\MediaAdmin\FileAlternatives\Strategy\AbstractFileAlternativesStrategy`.

.. code-block:: PHP

    <?php

    namespace AcmeDemo\MediaAdmin\FileAlternatives\Strategy;

    use OpenOrchestra\MediaAdmin\FileAlternatives\Strategy\AbstractFileAlternativesStrategy;
    use OpenOrchestra\Media\Model\MediaInterface;

    /**
     * Class ZipStrategy
     */
    class ZipStrategy extends AbstractFileAlternativesStrategy
    {
        const MEDIA_TYPE = 'zip';
        const MIME_TYPE = 'application/zip';

        /**
         * @param MediaInterface $media
         *
         * @return bool
         */
        public function support(MediaInterface $media)
        {
            return $media->getMimeType == self::MIME_TYPE;
        }

        /**
         * @return string
         */
        public function getName()
        {
            return 'zip_alternatives_strategy';
        }
    }

The important points are:

 - MEDIA_TYPE define the media type name stored in the media document and allows to filter media in the
   repository by type
 - The support method indicates if a given media can be managed by this strategy or not. In our case, if the
   mime-type is 'application/zip' it's ok, otherwise Open Orchestra must look for another strategy to manage
   the newly uploaded file.
 - Each strategy must have a unique name, return by the getName method.


To activate this strategy we need to declare it in a configuration file:

.. code-block:: yaml

    # AcmeDemoBundle/Resources/service.yml
    services:
        acme_demo_media_admin.file_alternatives.strategy.zip:
            class: AcmeDemo\MediaAdmin\FileAlternatives\Strategy\ZipStrategy
            tags:
                - { name: open_orchestra_media_admin.file_alternatives.strategy }

The important point is:

 - To get recognized as a file alternative strategy, the service must be taggued
   `open_orchestra_media_admin.file_alternatives.strategy`

Out of the box, the upload of a zip file is not allowed on Open Orchestra. To allow it, you need to update the
config by adding an entry in the container

.. code-block:: yaml

    parameter:
        open_orchestra_media_admin.allowed_mime_type:
            # Here goes the list of allowed mime types on your platform
            # don't forget to add the zip mime type
            - application/zip


Thumbnail and alternatives
--------------------------

Once the media document is created, an event is fired to generate the thumbnail and the alternatives. These
generations for a zip media are also coded in the `ZipStrategy`. So let's evoluate the code:

.. code-block:: PHP
    /**
     * Class ZipStrategy
     */
    class ZipStrategy extends AbstractFileAlternativesStrategy
    {
        // [...]
        const ALTERNATIVE_KEY = 'TAR';
        protected $thumbnail;
        protected $archiveManager;

        /**
         * @param string $thumbnail
         * @param object $archiveManager
         */
        public function __construct($thumbnail) {
            $this->thumbnail = $thumbnail;
            $this->archiveManager = $archiveManager;
        }

        // [...]

        /**
         * @param MediaInterface $media
         */
        public function generateThumbnail(MediaInterface $media)
        {
            $media->setThumbnail($this->thumbnail);
        }

        /**
         * Delete the thumbnail of $media
         * That strategy does nothing as the thumbnail is the same for all default type medias
         *
         * @param MediaInterface $media
         */
        public function deleteThumbnail(MediaInterface $media)
        {
        }

        /**
         * Generate all alternatives for $media
         *
         * @param MediaInterface $media
         */
        public function generateAlternatives(MediaInterface $media)
        {
            $zipFilePath = $this->tmpDir . DIRECTORY_SEPARATOR . $media->getFilesystemName();
            $tarFilePath = $this->archiveManager->generateTarVersion($zipFilePath);

            $tarName = '';
            if ($tarFilePath != '') {
                $tarName = self::ALTERNATIVE_KEY . tarFilePath;
                $this->mediaStorageManager->uploadFile($tarName, $tarFilePath);
            }

            $media->addAlternative(self::ALTERNATIVE_KEY, $tarName);
        }

        /**
         * Delete the alternatives of $media
         *
         * @param MediaInterface $media
         */
        public function deleteAlternatives(MediaInterface $media)
        {
            $alternatives = $media->getAlternatives();

            $this->deleteFile($alternatives[self::ALTERNATIVE_KEY]);

            parent::deleteAlternatives($media);
        }

        // [...]
    }

The important points are:

 - The method `generateThumbnail` is called to generate the thumbnail of the media used in the gallery of
   the media library. You can use any image already stored in the media storage, event create a new one. In
   our case we simply use an already stored pictogram and we store in the media the key to retrieve it from
   the media storage ($thumbnail). We found the key from the service definition, it's why it is injected in
   the constructor.
 - The method `deleteThumbnail` is designed to destroy the generated thumbnail when deleting the media. In our
   case, as the thumbnail used is generic to all zip media, we don't want to remove it from the storage, it's
   why we don't implement anything in this method.
 - The method `generateAlternatives` is designed to generate all alternatives of the media. In our case we
   only have one to generate: the tar.gz version. As the mechanism to generate a tar.gz is not the point of
   this cookbook, we use a mystic ArchiveManager that knows how to do that. It is injected in the constructor
   and thus defined in the service. The tar.gz version is generated locally to the server, so we need to
   upload it to the media storage. When it's done, we only need to set the altenartive key in the media
   document.
 - The method `deleteAlternatives` is used to destroy the alternatives from the media storage when the media
   is deleted. To do this we can use the protected method `deleteFile` described in the abstract strategy
   giving it the storage key of the alternative. The abstract method `deleteAlternatives` is called at the end,
   because it is responsible for destroying the original file.
 - A last method must be coded to respect the interface: `overrideAlternative`. It is used to replace an
   alternative with an other on a process of updating an alternative. As our zip type doesn't provide such a
   feature, we don't override the method coded in the abstract strategy which do nothing.

As seen in the description, the service must be updated:


.. code-block:: yaml

    # AcmeDemoBundle/Resources/service.yml
    services:
        acme_demo_media_admin.file_alternatives.strategy.zip:
            class: AcmeDemo\MediaAdmin\FileAlternatives\Strategy\ZipStrategy
            arguments:
                - 'TheKeyOfTheZipIconInTheMediaStorage'
                - @archiveManager
            tags:
                - { name: open_orchestra_media_admin.file_alternatives.strategy }


Rendering
---------

Each media type have a specific rendering. A video is presented in a <video> html tag when an image is rendered
with a <img> tag. To render our zip media and or its tar.gz alternative, we need to code a strategy
implementing `OpenOrchestra\Media\DisplayMedia\DisplayMediaInterface`.

Here is what it looks like for our zip type:

.. code-block:: PHP
    <?php

    namespace AcmeDemo\Media\DisplayMedia\Strategies;

    use OpenOrchestra\Media\DisplayMedia\Strategies\AbstractStrategy;
    use OpenOrchestra\Media\Model\MediaInterface;

    /**
     * Class ZipStrategy
     */
    class ZipStrategy extends AbstractStrategy
    {
        const MIME_TYPE = 'application/zip';

        /**
         * @param MediaInterface $media
         *
         * @return bool
         */
        public function support(MediaInterface $media)
        {
            return $media->getMimeType == self::MIME_TYPE_FRAGMENT_AUDIO;
        }

        /**
         * @param MediaInterface $media
         * @param string         $format
         * @param string         $style
         *
         * @return String
         */
        public function displayMedia(MediaInterface $media, $format = '', $style = '')
        {
            return $this->render(
                'AcmeDemoBundle:DisplayMedia/FullDisplay:zip.html.twig',
                array(
                    'media_url' => $this->getFileUrl($media->getFilesystemName()),
                    'media_name' => $media->getName()
                )
            );
        }

        /**
         * @param MediaInterface $media
         *
         * @param MediaInterface $media
         * @param string         $format
         * @param string         $style
         *
         * @return string
         */
        public function displayMediaForWysiwyg(MediaInterface $media, $format = '', $style = '')
        {
            return $this->render(
                'AcmeDemoBundle:BBcode/WysiwygDisplay:zip.html.twig',
                array('media_id' => $media->getId())
            );
        }

        /**
         * @param MediaInterface $media
         * @param string         $format
         *
         * @return string
         */
        public function getMediaFormatUrl(MediaInterface $media, $format)
        {
            return $this->displayPreview($media);
        }

        /**
         * @return string
         */
        public function getName()
        {
            return 'zip';
        }
    }



