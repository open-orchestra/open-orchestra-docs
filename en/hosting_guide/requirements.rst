Requirements
============

Open Orchestra is developped on a specific environment, making that environment our reference.
Open Orchestra is certified and supported on that reference environment. This document provides
you the different technologies required to reproduce that reference environment.

Basic Requirements
------------------
These requirements are mandatory to run Open Orchestra on a reference environment.

+----------------------+--------------------------+
| Operating System     | Debian 8.4 (Jessie)      |
+----------------------+--------------------------+
| Web server           | Apache/2.4.10            |
+----------------------+--------------------------+
| Database             | Mongodb 2.6.11           |
+----------------------+--------------------------+
| PHP (mod_php + cli)  | PHP 5.6                  |
+----------------------+--------------------------+
| PHP Extensions       | Mongo > 1.2.12, <1.7-dev |
|                      | Imagick                  |
|                      | OPcache > 7.0.6          |
|                      | Mbstring                 |
|                      | Curl                     |
|                      | Intl                     |
+----------------------+--------------------------+
| npm                  | 1.4.28                   |
+----------------------+--------------------------+
| Node.js              | 0.10.36                  |
+----------------------+--------------------------+

Optional requirements
---------------------
These requirements are optionals to run Open Orchestra. They are used on our reference environment
for optional functionalities.

+----------------------+--------------------------+
| Reverse proxy        | Varnish 3.0.7            |
+----------------------+--------------------------+

For a development server, we recommend you to add some packages:

+----------------------+--------------------------+
| Blackfire            |                          |
+----------------------+--------------------------+
| Selenium (with Xvfb) | 2.44.0                   |
+----------------------+--------------------------+
