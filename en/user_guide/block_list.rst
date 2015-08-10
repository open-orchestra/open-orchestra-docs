Blocks natively available
=========================

Open Orchestra comes with a set of blocks that can be used as-is in a website and cover a wide range of use cases.

Content blocks
--------------

Content list
~~~~~~~~~~~~
The content list block displays a list of elements belonging to a given content type (see the documentation page for contributing new contents).
Usefull to list all the contributions for a specific content type that have been created.

Content
~~~~~~~
This block displays a single object of a specific content type.
It's commonly used to be on the target page when a user clicks on an item of a content list block.

On the page where it is used, there must be a ``contentId`` parameter in the URL so the content to display can be retrieved.

Configurable content
~~~~~~~~~~~~~~~~~~~~
Same as before, but here the content object to display will always be the same and will not rely on the URL.
Therefore it is directly configurable in the block parameters.

Rich text
~~~~~~~~~
Using a rich text editor, this block can be told to render nicely formatted text.
Usefull to display information that is not dynamic.

Media blocks
------------

Carrousel
~~~~~~~~~
The carousel is a block that will display auto-changing images at a given frequency.
The list of images that are displayed is chosen in the block configuration and must be part of the media library.

Gallery
~~~~~~~
The gallery block will display a set of images from the media library.

Video
~~~~~
This block can display a video hosted on YouTube, Dailymotion or Vine services.

Media list by keyword
~~~~~~~~~~~~~~~~~~~~~
Displays the medias from the library that are matching a given keyword.

Navigation blocks
-----------------

Language list
~~~~~~~~~~~~~
This block provides a select box that lets the user change the current language in which the website is displayed.
It will automatically display all languages available.

Menu
~~~~
The menu displays links to the pages that are set to appear in the menu (see the page configuration).
It manages the hierarchy between pages by using a submenus system if needed.

SubMenu
~~~~~~~
Similar to the previous one, except that only the children of a given page will be part of this menu.
It's therefore possible to create a menu for only a subset of pages, different from you main menu.

Footer
~~~~~~
Similarly to the Menu block, it will list all pages that have been set to appear in the footer.

Miscellaneous blocks
--------------------

Login
~~~~~
A block used for login purposes that provides two fields : username and password.

AddThis
~~~~~~~
This block implements social sharing through the AddThis service.

Audience analysis
~~~~~~~~~~~~~~~~~
The audience block is designed to track users behavior with Xiti or Google Analytics services.

Gmap
~~~~
The Gmap displays a google map centered on a preset geographic point.

Contact
~~~~~~~
In order for the visitors to contact the website administrator,
this block renders a form and sends the visitor's message as an email to a configured electronic address.
