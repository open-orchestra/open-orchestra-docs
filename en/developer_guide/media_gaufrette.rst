Medias
======

Medias in Open Orchestra are physically managed by the Gaufrette component and
the `KnpGaufretteBundle`_ which binds Gaufrette to Symfony. Gaufrette is an abstraction
layer for accessing files wherever the physical copy is located (locally on the disk,
on an FTP server, in the cloud...).

Media storage
-------------

By default, Open Orchestra stores the media on disk of the webserver of the application.
If it is needed to change the location of the files, the configuration should be updated
to change the adapter that Gaufrette must use for the file storage.

All adapters that can be natively used are described in the `configuration documentation`_,
along with the details of the configuration to set up.

If another Gaufrette filesystem is used instead of the default one, it should be
notified to Open Orchestra through the ``open_orchestra_media.filesystem`` configuration parameter,
which expects the identifier of the new filesystem to use.

Upload and resizing of images
-----------------------------

An uploaded media from the media library can be displayed in different formats (called thumbnails)
depending on the needs of the application. A format is simply a configuration entry
defining parameters in one of the three following ways:

* A ``max_height`` key that defines the maximum height of the thumbnail, the width
  is calculated from the image ratio
* A ``max_width`` key that defines the maximum width of the thumbnail, the height
  is calculated from the image ratio
* Two keys ``height`` and ``width`` which will define the rectangle area in which the image should fit

Here is an example of configuration defining three custom thumbnail formats:

.. code-block:: yaml

    open_orchestra_media:
        thumbnail:
            my_custom_max_width:
                max_width: 250
            my_custom_max_height:
                max_height: 100
            my_custom_rectangle:
                height: 200
                width: 300

The resizing of the image will be done automatically during the original file upload.

Front display
-------------

Each media file is identified by a unique hash key from which Gaufrette can retrieve
the physical file in the configured storage. To generate the HTML tag for a
Front Office display, Open Orchestra provides a Twig function ``display_media``
that will generate the media link from the identifier.

Because of the wide variety of storage options for media files, it's possible
that a file cannot be read directly from a web browser because of access restrictions.
This is why the generated link actually calls the ``MediaController`` from the ``MediaBundle``,
which will retrieve the binary data with Gaufrette and send it back to the browser.


.. _`KnpGaufretteBundle`: https://github.com/KnpLabs/KnpGaufretteBundle
.. _`configuration documentation`: https://github.com/KnpLabs/KnpGaufretteBundle#configuration
