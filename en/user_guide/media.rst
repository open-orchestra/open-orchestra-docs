Media Management
================

Open Orchestra allows you to manage medias uploaded by the users in the media library panel.
They can be easily used in other part of the website such as blocks or contents.
Natively, images, PDF and videos are supported by Open Orchestra.

Folder
------

All files are organised inside folders. It's possible to browse the folder tree to see files by clicking on the left panel.

Create
~~~~~~

Creating a folder is done by clicking on the "new folder" button in the left panel.

The creation form needs:

* name: name of the folder
* Websites: which websites are using the folder

Remove
~~~~~~

To remove a folder, select the folder and click on the trash button on the right panel.
It is not possible to delete a folder containing some medias

Manage files
------------

The add button in the folder's content allows you to upload files.

A trash icon appears on media preview hovering to delete the media.
The media can't be deleted if it is used in an element (block, content) which is in the final state.

Clicking on the media preview will a open a page with tow panels (for an image) : format version management (for images) and meta information

Image Crop
~~~~~~~~~~

When you upload an image, you can choose from some predetermined formats to improve rendering in front office :

* original: keep original format
* fixed height: adapt height and keep proportion
* fixed width: adapt width and keep proportion
* rectangle: reduce to fit in the rectangle format

These ones can be personalized on custom installation.

Once a format selected, the preview is updated and some choices are added:

* manual crop: to adjust your selection manually
* upload an alternative image: if user want to resize image himself, replace the selected thumbnail format by another image

.. image:: ../../images/crop.png

Meta
~~~~

Media meta information form have different fields :

* title: title of the media in different languages, appears on mouse hovering
* alt: description of the media in different languages, appears if media can't be loaded or for blinded monitor.
* media's copyright: the copyright on the media
* comment: comment on the media
* keyword: use to find media by tag in some blocks
