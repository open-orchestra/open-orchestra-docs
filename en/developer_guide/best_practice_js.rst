Best practices :
================

Basic :
=======

- Conventions:
 - Document proposed by google : https://google.github.io/styleguide/javascriptguide.xml
 - Other document produced by the comunity : https://github.com/rwaldron/idiomatic.js
 (*different tools to validate as jshint*)

- Comment js (example http://usejsdoc.org/)
- Namespace : on Open Orchestra a big part of js and the global scope, a integrator may end up inadvertently
  override a function, example of using of namespace presented by @juchi in this PR
  (open-orchestra/open-orchestra-cms-bundle: `PR #1295`)
- Cutting modules (AMD, ES6 Modules) of the code but also at the file architecture.
- Tests
- files Naming; no special convention exist

*Many links on best practices, books, pattern, framework, test and article on this site :*
http://jstherightway.org/#reading

Open Orchestra in the Future:
=============================

Regarding Open Orchestra more specifically, the project need to review all js to add :

In the first time :
-------------------

- Namespace, there are solutions des solutions to be cleaner namespaces :
 https://github.com/MaksJS/Namespace-in-CoffeeScript
- Comment js
- The Coffeescript provides a syntax in the form of "class" which enhance readability (`example using`_)
- Distribute the various files by feature (This partly has already been initialized but there is still too much
 thing in the root folder)

In the second time :
--------------------

- Passer ECMAScript 6 ou type script (voir le message de cédric ci-dessous)
- Review the uses of Backbone Js, not using models and collections that are still the central point of backbone
  that could "plug" on the API.
- Cut functionality in AMD module or another depending on the previous point
- Perform tests once all will be well cut module

To Finish :
-----------

To use a framework more suitable for the views managements in backbone which is quite poor as marionnetteJS
(life cycle, regions that allow objects to easily permutations, communication between views that are already using a
bit with wqrer, application object, router with controllers etc) , example of minimalist application that displays a
user list from a json api OO: `Repo apps`_

.. _`PR #1295`: https://github.com/open-orchestra/open-orchestra-cms-bundle/pull/1295
.. _`example using`: https://github.com/open-orchestra/open-orchestra-cms-bundle/blob/01db397aa5b14c9675b14ca9b3fcb8412ec1eb87/BackofficeBundle/Resources/public/coffee/dataTable/DataTableView.coffee
.. _`Repo apps`: https://github.com/itkg-alavieille/marionette-test
