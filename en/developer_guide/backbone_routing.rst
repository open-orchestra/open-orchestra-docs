Backbone specific route
=======================

Context
-------

In the Open Orchestra Back office, all the routing is managed by the `Backbone routing`_ component

The routes already used in the Back office are already declared in some configuration file.

Adding a new route
------------------

In a configuration file, you could add a route to the router:

.. code-block:: javascript

    (function(router) {
        // Declare the route pattern and the name for the generation
        router.addRoutePattern('showFoo', 'foo/:fooId');

        // Factorise some code in the router (if needed)
        router.fooDisplay = function(fooId) {
            if (selectorExist($('#nav-foo-' + fooId))) {
                this.initDisplayRouteChanges('#nav-foo-' + fooId);
                showFoo($('#nav-foo-' + fooId).data('url'));
            } else {
                Backbone.history.navigate('');
            }
        };

        // Declare the route pattern for the matching process
        router.route('foo/show/:fooId', 'showFoo', function(fooId) {
            this.fooDisplay(fooId);
        });
    })(window.appRouter);

When you declare a new route in Backbone, you should first give the route pattern for the route generation.
Then you should declare the method used for the matching.

Finally, you should inject the router to the anonymous function.

.. _`Backbone routing`: http://backbonejs.org/#Routing