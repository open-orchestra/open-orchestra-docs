Requirements
============

Front servers
-------------

Production server
~~~~~~~~~~~~~~~~~

It's required to have a PHP webserver in order to run Open Orchestra.

* PHP 5.4+
* Apache 2 or NginX
* Varnish 3 reverse proxy (optionnal)
* Nodejs

Development server
~~~~~~~~~~~~~~~~~~

To have a more usefull development server, we recommand you to add some packages :

* Blackfire
* Selenium/Xvfb

Database
--------

While MongoDB is the only database system to be natively supported,
it's possible to use other systems such as MySQL or PostgreSQL with extra development.
