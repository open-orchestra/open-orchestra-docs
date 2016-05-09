ESI blocks
==========

Open Orchestra leverages the power of ESI blocks to optimize page rendering and increase performance.
ESI blocks are a way to split the rendering of a page into different elements
that will be rendered in separate requests by the web server.
This behavior allows the application to apply HTTP cache to some parts of the page
and refresh only the outdated parts when needed.

In the Front Office application, each block is rendered in an ESI block using the render_esi() twig function.
The blocks will therefore be cached by an HTTP cache unless
the method ``DisplayBlockInterface::isPublic()`` returns false.

Setup
-----

In order to use the power of ESI blocks, it's needed to have a reverse proxy
in front of the web application that will be able to process them.
Examples of reverse proxies are Varnish or the HttpCache component of Symfony.

If there is no ESI-capable reverse proxy configured,
Symfony will still be able to render your pages with just HTML so the application won't suffer any drawbacks.

HttpCache configuration
~~~~~~~~~~~~~~~~~~~~~~~

The configuration of Symfony for using HttpCache is explained in the `Http cache documentation`_


Varnish configuration
~~~~~~~~~~~~~~~~~~~~~

To let Symfony know that there is an ESI-capable server (Varnish) installed in front of the PHP webserver,
this ESI server should set an HTTP header in the request to be passed to the application,
and parse the response to check for ESI usage.

This is done inside the varnish configuration file.

.. code-block:: none

    sub vcl_recv {
        set req.http.Surrogate-Capability = "varnish=ESI/1.0";
    }

    sub vcl_fetch {
        if (beresp.ttl > 0s) {
            unset beresp.http.Set-Cookie;
            return(deliver);
        }
    }

Selective flushing with tags
----------------------------

**This feature is not available with the Symfony HttpCache component.**

Principle
~~~~~~~~~

The main interest of ESI tags is to give the possibility to flush some parts
of a cached page at different times. While it's interesting to use this
ability by setting a time-to-live (TTL) to define the lifetime of a block,
Open Orchestra uses Varnish's ability to flush ESI blocks on the fly on certain conditions.

Whenever an ESI block is cached in Varnish, the HTTP headers of the response will
be saved along with the content. This mechanism allows to set an X-Cache-Tags header
with its value being a set of tags that indicate in which conditions it would be flushed.
Therefore, when an action leads to one of the tags being marked as outdated,
a request is sent to varnish so it will ban all cached data linked to this tag.

Behavior for nodes and blocks
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When caching a node, the tags that are used refer to the identifier of the node,
the language and id of the associated website.

For blocks, two kind of tags are applied : generic ones and specific ones.

The generic tags are added for all kind of blocks, they depend on :
* the block type
* the node which contains the block
* the language
* the website

Additionally, each rendering strategy for blocks can define a list of specific tags
by implementing the method ``DisplayBlockInterface::getCacheTags()``.

By default, Open Orchestra provides some tag that can be used in the rendering strategies:

* ``node- + NODE_ID`` : Invalidate when node status is updated.
* ``contentType- + CONTENT_TYPE`` : Invalidate when content type is updated or deleted.
* ``contentId- + CONTENT_ID`` : Invalidate when content status is updated or content is deleted.
* ``mediaId- + MEDIA_ID`` : Invalidate when media is updated or deleted.
* ``menu- + SITE_ID`` : Invalidate when a node of this site is deleted, restored, his status changed or his path updated.

These tags are gathered in the ``OpenOrchestra\BaseBundle\Manager\TagManager`` class.

If this tags isn't enough,
It's possible to define new cache tags for some data to be flushed at optimal times,
depending on the specifics of the application. These tags can then be flushed by calling
``OpenOrchestra\DisplayBundle\Manager\CacheableManager::invalidateTags()`` when needed.

.. _`Http cache documentation`: http://symfony.com/doc/current/book/http_cache.html#edge-side-includes
