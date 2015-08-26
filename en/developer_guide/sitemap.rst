Using sitemap.xml
=================

As Open Orchestra is a multisite platform, you will have to manage several sitemap.xml files for a
single installation. To simplify the maintenance of their content, information contained in the files
can be directly edited in the Back Office. But contribution is only the first step. To be available,
these information require to be dumped in files and to be correctly served to the client.

Creation of ``sitemap.xml`` files with Open Orchestra is achieved in 3 steps:

- `files contribution`_
- `files generation`_
- `files routing`_

.. _files contribution:

Files contribution
------------------
Contributing the content of a ``sitemap.xml`` file is done in the Backoffice, and two locations
are involved: one for the default values, and one for the specific values.

The first place to go is website edition. In the website edition form, you can set up the default
values for all pages of the site. These settings are the periodicity of change of a page (the
changefreq setting) and the relative importance of a page compared to the other pages (the priority
setting). When set, these values are used when a page does not specify its own settings.

To provide specific settings for a page, you have to edit the matching node setting form. Here you
can set the priority and the changefreq only for this page. The settings given here override the
website default values. For more info about node configuration you can read the `node configuration
documentation`_.

.. _files generation:

Files generation
----------------
Once contributed, the content of the ``sitemap.xml`` is only known from the database. To serve it to
a client requesting it, two approaches are possible: use a controller action looking in the database
for the information matching the current site, or serve a previously generated file containing these
information.

To enhance perfomances, Open Orchestra choose the second option. This solution prevents any PHP action
and database access. As these files are static they can easily be cached by a reverse proxy.

Once a ``sitemap.xml`` data is contributed, you have to manually dump it into a file. Open Orchestra
provides a console command, available on your Front installation:

    app/console orchestra:sitemaps:generate [--siteId=SITEID]

This command dumps one or all the ``sitemap.xml`` files depending on the siteId parameter presence.
To be accessible by web client, the generated files are stored in the web directory of your
application. Each file is stored in a sub-directory named by the site Id, then by the alias
Id. For instance if you have two sites whose are is 'site-1', 'site-2', that 'site-1' get two aliases
and 'site-2' has one, the ``sitemap.xml`` files will be dumped here:

- web/site-1/alias-0/sitemap.xml
- web/site-1/alias-1/sitemap.xml
- web/site-2/alias-0/sitemap.xml

Note that the alias indexes (alias-0, alias-1, etc...) refers to the position of the aliases in the
website edit form.

A good practice is to use that command in a cron, to refresh periodically the content of the files.

.. _files routing:

Files routing
-------------
When a client requests a ``sitemap.xml``, it should be located at the root of the domain. But the
files are generated somewhere else. As a result the webserver must be configured to redirect to the
matching file: this can be done by a rewrite rule . The type of configuration to tweak depends on
your server type, for instance on Apache this is done via the Virtual Host mechanism.

Here is a configuration example for ``Apache``, in the case of the first alias of a site with id 'my-site':

    <IfModule mod_rewrite.c>
        RewriteEngine On
        RewriteRule ^/sitemap.xml /my-site/alias-0/sitemap.xml [L]
    </IfModule>
    
Once Apache is reloaded, the rewrite rule is used and the ``sitemap.xml`` file is accessible.

Every further modification will modify the file content but not its name, so you don't have to modify
the rewrite rule. Since then you can update the file periodically without having to restart the
webserver.

.. _`node configuration documentation`: /en/user_guide/node_configuration.rst
