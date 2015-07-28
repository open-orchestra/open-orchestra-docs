Error pages
===========

Symfony allows a developper to customize error pages shown by the framework when a matching HTTP
status is returned. For instance a developper could create a specific Error 500 page.

Open Orchestra allows you to go further for two types of status : 404 (resource not found) and 503
(site under maintenance). You actually can contribute those pages directly in the Back Office,
customizing them on a per site / per language combination.
 
Site under maintenance: Error 503
---------------------------------
Displaying a custom 503 page for an Open Orchestra site requires 3 steps :

1. Contribute the matching nodes in the Back Office and publish it
2. Dump the node into a static html file via the command line (or let a cron task generate it)
3. Configure the Virtual Host to serve that file when the site is under maintenance

Contributing the 503 error page
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
To contribute the 503 error page, in the Back Office navigation menu, click on "Error pages", then
on "503". This will show a standard node configuration page. The node can be contributed for each
available language of the Front Office. To make the page available, it must be published.

Dump the node into statics files
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Open Orchestra comes with a command line to dump the error nodes into static files. You can execute
that command line at the root of your project or place the command in a cron task to dump the files
periodically.
The command is the following:

    app/console orchestra:errorpages:generate [siteId]

The siteId is an option allowing you to specify a specific site to limit the dump operation. Without
that option the pages are dumped for every site.

For each site, the command will look for error nodes and especially the published versions. The script
will then look to the available site aliases. When an error node is published in the site alias language,
the script generates the matching files.
For instance if mysite.com declares an alias in english and a second one in french, and if a 503 error
node is published in english, then the command generates a 503 file in english for the first alias.
Nothing is generated for the french alias as there's no 503 node published in french.

The generated files can be found under the following path:

    web/*siteId*/alias-*aliasId*/errorPage503.html

where *siteId* is the site id and *aliasId* the alias id.

Configuring the Virtual Host
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
To use the 503 static page, the apache Virtual Host of the site must be configured using the
ErrorDocument directive. Here comes a version of the configuration allowing you to avoid the Virtual
Host file edition each time you want to put on/off your site.

    <IfModule mod_rewrite.c>
        RewriteEngine On

        RewriteCond %{ENV:REDIRECT_STATUS} !=503
        RewriteCond "/local/path/to/application/maintenance.on" -f
        RewriteRule ^(.*)$ /$1 [L,R=503]
    </IfModule>

    ErrorDocument 503 /*siteId*/alias-*aliasId*/errorPage503.html

where *siteId* is the site id and *aliasId* the alias id.

With such a configuration, you don't have to rewrite the Virtual Host nor restart Apache on maintenance
operation. You only have to put a file named maintenance.on in the root directory of your application
to validate the maintenance rewrite and to remove it to put your site on back.

Error 404 - Page not found
--------------------------
The 404 error page requires less efforts than the 503 version to be used. Once a 404 node is contributed
and published, it immediately replaces the standard 404 error message from Symfony.

Be aware that if the node is published in only one language, it will only be available for the site aliases
using that language. That way, a site in several languages can present an Open Orchestra 404 page for one
language and a Symfony 404 page for others.

Note: like 503 pages, 404 pages are also dumped by the console command orchestra:errorpages:generate. They
can so be used with virtual hosts configuration on some cases if needed.

