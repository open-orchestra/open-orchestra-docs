Requirements
============

Open Orchestra is developped on a specific environement, making that environement our reference.
Open Orchestra is certified and supported on that reference environement. This document provides
you the different technologies required to reproduce that reference environement.

Basic Requirements
------------------
These requirements are mandatory to run Open Orchestra on a reference environement.

+---------------------+---------------------+
| Operating System    | Debian 7.6 (Wheezy) |
+---------------------+---------------------+
| Web server          | Apache/2.2.22       |
+---------------------+---------------------+
| Database            | Mongodb 2.6.9       |
+---------------------+---------------------+
| PHP (mod_php + cli) | PHP 5.4.39          |
|                     | Mongo extension     |
|                     | Imagick extension   |
+---------------------+---------------------+
| Node.js             | ????                |
+---------------------+---------------------+



Optional requirements
---------------------
These requirements are optionals to run Open Orchestra. They are used on our reference environement
for optionnal functionnalities.

+---------------------+---------------------+
| Reverse proxy       | Varnish 3.0.7       |
+---------------------+---------------------+

For a development server, we recommand you to add some packages:

+---------------------+---------------------+
| Blackfire           | ????                |
+---------------------+---------------------+
| Selenium / Xvfb     | ????                |
+---------------------+---------------------+
