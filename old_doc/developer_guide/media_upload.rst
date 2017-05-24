Media
=====

When a media is uploaded in the media library from the Back Office, 2 things happen. First a thumbnail is
generated to display it in the media library. Then, according to the media type, several alternatives can be
generated too. For instance, for an image, some alternative formats are generated. You could imagine a video
being reencoded in different formats at this step.

Media storage
-------------

All files (originals uploaded by the user, the thumbnails and the alternatives) are stored via the Gaufrette
component and the `KnpGaufretteBundle`_ which binds Gaufrette to Symfony. Gaufrette is an abstraction layer
for accessing files wherever the physical copy is located (locally on the disk, on an FTP server, in the
cloud...).

By default, Open Orchestra stores the media locally on the webserver of the application. But if it is required
to change the location of the files, the configuration can be updated to change the adapter used by Gaufrette.

All adapters that can be natively used are described in the `configuration documentation`_, along with the
details of the configuration to set up.

If another Gaufrette filesystem is used instead of the default one, it should be notified to Open Orchestra
through the ``open_orchestra_media.filesystem`` configuration parameter, which expects the identifier of the
new filesystem to use.

Upload strategies
-----------------
When a new file is uploaded, a media document is created and the file is moved to the storage via Gaufrette.
But some required process are also made, and some other optional can be too. For instance, to be rendered in
the Back Office gallery, a preview thumbnail must be generated. If the media is an image, several alternatives
in different sizes are also generated. If the file is a sound, maybe some new variants could be generated with
different bitrates. Those operations are completed by the alternative strategies. A strategy exists for each
supported mime-type.

When a new media is created due to a file upload, the ``MediaEvents::MEDIA_ADD`` event is fired. The
``OpenOrchestra\MediaAdmin\EventSubscriber\MediaCreatedSubscriber`` catch this event to track the created
media. Later after the response matching the media creation has been sent to the client, this subscriber also
catch the ``KernelEvents::TERMINATE`` event. It then asks the
``OpenOrchestra\MediaAdmin\FileAlternatives\FileAlternativesManager`` to generate a thumbnail and the
alternatives. So, the manager search a strategy able to deal with the uploaded file.

You can alter the alternatives generation by extending the existing strategies or by creating new ones.

The image alternatives
----------------------

A media image can be displayed in different formats depending on the needs of the application. So when an
image is uploaded to the media library, several alternatives are generated according to the configured formats.
A format is simply a configuration entry combining one or severall parameters among the following:

* max_height: defines the maximum height of the image to generate, the width is calculated to keep a correct
  ratio
* max_width: defines the maximum width of the image to generate, the height is calculated to keep a correct
  ratio
* compression_quality: defines the compression rate of the alternative. This parameter is always required when
  defining a new format

Open Orchestra comes with three default formats (Fixed height, Fixed width and Rectangle) which are mostly
samples to show what is possible. You should always replace these sample formats by the one required by your
application. To do this just add your formats in the ``app/config/config.yml`` file

Here is an example of configuration defining two custom alternative formats:

.. code-block:: yaml

    open_orchestra_media_admin:
      files:
        alternatives:
          image:
            formats:
              my_custom_max_height:
                max_height: 100
                compression_quality: 95
              my_custom_rectangle:
                max_height: 200
                max_width: 300
                compression_quality: 95

You can create as many formats as required, as soon as you create only one, it will replace the Open Orchestra
sample formats.

To complete your customization, you should think about adding a translated label to your custom settings as
these formats are used in several locations of the Back Office. The translation key used is
``open_orchestra_media_admin.form.media.MY_CUSTOM_FORMAT_KEY`` where MY_CUSTOM_FORMAT_KEY is the key of the
format used in the ``app/config/config.yml`` description, for instance my_custom_max_height and
my_custom_rectangle in the previous example.

Front display
-------------

Each media file is identified by a unique hash key used by Gaufrette to retrieve the physical file in the
configured storage. To generate the HTML tag rendering a media, Open Orchestra provides the Twig function
``display_media``.

Instead of a direct access to the file, we recommand you to use the ``MediaController`` from the
``MediaFileBundle``. The ``show`` action will retrieve the binary data with Gaufrette and send it back to the
browser.

.. _`KnpGaufretteBundle`: https://github.com/KnpLabs/KnpGaufretteBundle
.. _`configuration documentation`: https://github.com/KnpLabs/KnpGaufretteBundle#configuration
