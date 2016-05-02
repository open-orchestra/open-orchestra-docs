Server Configuration
====================

To know more about server configuration see `requirements`_.

Apache
------

To use Open Orchestra, you need to configure the different virtual hosts (Back Office and Front Office)
 in your Apache configuration.

Virtual Host
~~~~~~~~~~~~

Back Office Virtual Host:

.. code-block:: apacheconf

    <VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName admin.openorchestra.1-1.dev

        DocumentRoot  /path/to/your/open_orchestra/bo_installation/folder/web
        <Directory />
            Options FollowSymLinks
            AllowOverride None
        </Directory>
        <Directory /path/to/your/open_orchestra/bo_installation/folder/web>
            Options -Indexes +FollowSymLinks -MultiViews
            AllowOverride All
            Order allow,deny
            allow from all
        </Directory>

        <IfModule mod_rewrite.c>
            RewriteEngine On
        </IfModule>

        ErrorLog /var/log/apache2/admin.openorchestraError.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/admin.openorchestraAccess.log combined
    </VirtualHost>


Front Office Virtual Host:

.. code-block:: apacheconf

    <VirtualHost *:80>
        ServerAdmin webmaster\@localhost
        ServerName front.openorchestra.1-1.dev

        DocumentRoot /path/to/your/open_orchestra/front_installation/folder/web
        <Directory />
            Options FollowSymLinks
            AllowOverride None
        </Directory>
        <Directory /path/to/your/open_orchestra/front_installation/folder/web>
            Options -Indexes +FollowSymLinks -MultiViews
            AllowOverride All
            Order allow,deny
            allow from all
        </Directory>

        <IfModule mod_rewrite.c>
            RewriteEngine On
        </IfModule>

        ErrorLog /var/log/apache2/front.openorchestraError.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/front.openorchestraAccess.log combined
    </VirtualHost>

Varnish vcl
-----------

With Open Orchestra, you can use ``Varnish``. It is particularly useful for `ESI`_ rendering for instance.

This vcl is a basic configuration example to use the esi render.

.. code-block:: none

    acl purgers {
      "127.0.0.1";
    }

    acl invalidators {
      "127.0.0.1";
    }

    backend f1 {
      .host = "127.0.1.1";
      .port = "80";
    }

    director front round-robin {
        {
            .backend = f1;
        }
    }

    sub vcl_recv {
        set req.backend = front;

        if (req.http.Cache-Control ~ "no-cache" && client.ip ~ invalidators) {
            set req.hash_always_miss = true;
        }

        if (req.request == "BAN") {
            if (!client.ip ~ invalidators) {
                 error 405 "Ban not allowed";
            }

            if (req.http.X-Cache-Tags) {
                ban("obj.http.X-Host ~ " + req.http.X-Host
                    + " && obj.http.X-Url ~ " + req.http.X-Url
                    + " && obj.http.content-type ~ " + req.http.X-Content-Type
                    + " && obj.http.X-Cache-Tags ~ " + req.http.X-Cache-Tags
                );
            } else {
              ban("obj.http.X-Host ~ " + req.http.X-Host
                  + " && obj.http.X-Url ~ " + req.http.X-Url
                  + " && obj.http.content-type ~ " + req.http.X-Content-Type
              );
            }

            error 200 "Ban added";
        }

        if (req.request == "PURGE") {
            if (!client.ip ~ purgers) {
                 error 405 "Purge not allowed";
            }
            return(lookup);
         }

        if (req.http.Accept-Encoding) {
            if (req.url ~ "\.(jpg|png|gif|gz|tgz|bz2|tbz|mp3|ogg)$") {
                remove req.http.Accept-Encoding;
            } elsif (req.http.Accept-Encoding ~ "gzip") {
                set req.http.Accept-Encoding = "gzip";
            } elsif (req.http.Accept-Encoding ~ "deflate") {
                set req.http.Accept-Encoding = "deflate";
            } else {
                remove req.http.Accept-Encoding;
            }
        }

        if (req.http.User-Agent ~ "(?i)android") {
            set req.http.X-UA-Device = "android";
        }

        if(req.http.host ~ "(admin.openorchestra.1-1.dev)") {
            return (pass);
        }

        if (req.request == "POST") {
            return(pass);
        }

        if (req.url ~ "^/preview") {
            return (pass);
        }

        set req.http.Surrogate-Capability = "varnish=ESI/1.0";

        return(lookup);
    }

    sub vcl_fetch {
        set beresp.http.X-Url = req.url;
        set beresp.http.X-Host = req.http.host;

        if (beresp.status == 404 || beresp.status == 500 || beresp.status == 503) {
            set beresp.ttl = 30s;
        }

        if (beresp.http.Surrogate-Control ~ "ESI/1.0") {
            unset beresp.http.Surrogate-Control;
            set beresp.do_esi = true;
        }

        if (beresp.ttl > 0s) {
          unset beresp.http.Set-Cookie;
        }
    }

    sub vcl_deliver {
        if (!resp.http.X-Cache-Debug) {
            unset resp.http.X-Url;
            unset resp.http.X-Host;
            unset resp.http.X-Cache-Tags;
        }
    }

    sub vcl_hit {
        if (req.request == "PURGE") {
            purge;
            error 204 "Purged";
        }
    }

    sub vcl_miss {
        if (req.request == "PURGE") {
            purge;
            error 204 "Purged (Not in cache)";
        }
    }

    sub vcl_hash {
        if (req.http.X-UA-Device) {
            hash_data(req.http.X-UA-Device);
        }
    }


Cron jobs
---------

Cron jobs are used for tasks (commands or shell scripts) to run periodically at fixed times, dates, or intervals.
Cron jobs typically automate system maintenance.

Cron jobs on Open Orchestra
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Open Orchestra has 4 cron jobs created with the provisioning:

Site maps
~~~~~~~~~

Generate sitemap files for every sites, more information available in the `sitemap`_ documentation

.. code-block:: bash

    0 2 * * * php /var/www/front-open-orchestra/current/app/console -e=prod orchestra:sitemaps:generate 2>> /tmp/cron.error.message

Robots.txt
~~~~~~~~~~

Generate the robots.txt files for every sites,
further information about `robots`_

.. code-block:: bash

    0 2 * * * php /var/www/front-open-orchestra/current/app/console -e=prod orchestra:robots:generate 2>> /tmp/cron.error.message

Error pages
~~~~~~~~~~~

Generate the special error pages files for every sites (eg 404 & 503 status),
for more information about the 404 and 503 special pages see the documentation `customizing error pages`_


.. code-block:: bash

    0 2 * * * php /var/www/front-open-orchestra/current/app/console -e=prod orchestra:errorpages:generate 2>> /tmp/cron.error.message

Error cron
~~~~~~~~~~

This cron sends an email if any of above cron didn't correctly.

.. code-block:: bash

    59 0-23 * * * if [ -s '/tmp/cron.error.message' ]; then  cat /tmp/cron.error.message | mailx -s "cron error" contact@open-orchestra.com; fi; rm /tmp/cron.error.message;

Ansible
-------

If you don't want set the different configurations (Virtual Host, Varnish, Cron) manually, you can use the `provisioning`_.


.. _ESI: en/developer_guide/esi.rst
.. _requirements: /en/hosting_guide/requirements.rst
.. _sitemap: /en/developer_guide/sitemap.rst
.. _robots: /en/developer_guide/robots.rst
.. _customizing error pages: /en/developer_guide/error_pages.rst
.. _provisioning: en/hosting_guide/server_provisioning.rst
