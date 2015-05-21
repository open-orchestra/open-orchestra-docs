Requirements
============

Open Orchestra is developped on a specific environment, making that environment our reference.
Open Orchestra is certified and supported on that reference environment. This document provides
you the different technologies required to reproduce that reference environment.

Basic Requirements
------------------
These requirements are mandatory to run Open Orchestra on a reference environment.

+----------------------+---------------------+
| Operating System     | Debian 7.6 (Wheezy) |
+----------------------+---------------------+
| Web server           | Apache/2.2.22       |
+----------------------+---------------------+
| Database             | Mongodb 2.6.9       |
+----------------------+---------------------+
| PHP (mod_php + cli)  | PHP 5.4.39          |
|                      | Mongo extension     |
|                      | Imagick extension   |
+----------------------+---------------------+
| npm                  | 1.4.28              |
+----------------------+---------------------+
| Node.js              | 0.10.30             |
+----------------------+---------------------+



Optional requirements
---------------------
These requirements are optionals to run Open Orchestra. They are used on our reference environment
for optionnal functionnalities.

+----------------------+---------------------+
| Reverse proxy        | Varnish 3.0.7       |
+----------------------+---------------------+

For a development server, we recommand you to add some packages:

+----------------------+---------------------+
| Blackfire            |                     |
+----------------------+---------------------+
| Selenium (with Xvfb) | 2.44.0              |
+----------------------+---------------------+
