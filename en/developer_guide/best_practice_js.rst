Best practices :
================

JavaScript is the main client-side scripting language used by many of open-source projects. This style guide is a list
of dos and don'ts for JavaScript programs.

Conventions :
=============

General Naming:
---------------

camelCase should be used for :

- variable
- function
- object

UPPERCASE_AND_UNDERSCORE should be used for :

- constant

PascalCase should be used for :

- constructor
- prototype
- etc

lowercase should be used for :

- file name

.. code-block:: js

    functionNames;
    variableNames;
    ConstructorNames;
    EnumNames;
    methodNames;
    SYMBOLIC_CONSTANTS;

indentation:
------------

Operators must have a space before and after them.

.. code-block:: js

    var x = y % 2;

A space must be added after each enumeration separator

.. code-block:: js

    var array = [“first”, “second”, “third”];

Use a indention of 2 spaces to the blocks.

.. code-block:: js

    function () {
      return true;
    }

Comments:
---------

The comments can use on one line to explain the code with `//`.
Or use to create a advanced block with `/**/` to describe the functional, parameters, return, etc.. Also see `JsDoc`_, `GoogleDev`_
and `Google Style Guide`_.

.. code-block:: js

    /** @const */ var MY_BEER = 'stout';

    /**
     * Determines whether a node is a field.
     * @return {boolean} True if the contents of
     *     the element are editable, but the element
     *     itself is not.
     * @deprecated Use isField().
     */
    BN_EditUtil.isTopEditableField = function(node) {
      ...
    };


Variable declarations :
-----------------------

Declarations with var: Always

When you fail to specify var, the variable gets placed in the global context, potentially altering existing values.
Also, if there's no declaration, it's hard to tell in what scope a variable lives. So always declare with var.

There is also the key word " `Let`_ " to declare a variable. The lifetime of this variable is that the block that declares
it. Although promising it is not enough to be used implented.


Constant declarations:
----------------------

Use `NAMES_LIKE_THIS` for constant values. Use `@const` to indicate, on comment, a constant
(non-overwritable) pointer (a variable or property). Never use the " `const`_ " keyword as
it's not supported in Internet Explorer before version 11 or not full supported.


Semilicons:
-----------

Semicolons should be included at the end of function expressions, but not at the end of
function declarations. The distinction is best illustrated with an example:

.. code-block:: js

    var foo = function() {
      return true;
    };  // semicolon here.

    function foo() {
      return true;
    }  // no semicolon here.


Standards Feature:
------------------

Always preferred over non-standards features

For maximum portability and compatibility, always prefer standards features over non-standards
features (e.g., string.charAt(3) over string[3], ...).

Wrapper objects and primitive types:
------------------------------------

Always preferred use primitive types.

.. code-block:: js

    // var string1 = String("Hello world");
    var string1 = “Hello world”;
    var string2 = new String(“Hello world”);

    string1 === string2 // return false
    string1 === string2.valueOf() // return true
    string1.valueOf() === string2.valueOf() // return true

    typeof String(0) == 'string';
    typeof new String(0) == 'object';


This is very useful for casting things to number, string and boolean.

See : `Distinction between string primitives and String objects`_ by Mozilla.org.

For-in Loop:
------------

Only for iterating over keys in an object/map/hash.
Always use normal for loops when using arrays.

.. code-block:: js
    function printArrayForIn(arr) {
      for (var key in arr) {
        print(arr[key]);
      }
    }
    function printArray(arr) {
      var l = arr.length;
      for (var i = 0; i < l; i++) {
        print(arr[i]);
      }
    }

    printArrayForIn([0,1,2,3]);  // This works.
    printArray([0,1,2,3]);       // This works.

    var a = new Array(10);
    printArrayForIn(a);    // This is wrong.
    printArray(a);         // This works.




Tips :
------
Don't Use new Object()
Use {} instead of new Object()
Use "" instead of new String()
Use 0 instead of new Number()
Use false instead of new Boolean()
Use [] instead of new Array()
Use /()/ instead of new RegExp()
Use function (){} instead of new function()

.. code-block:: js

    var x1 = {};           // new object
    var x2 = "";           // new primitive string
    var x3 = 0;            // new primitive number
    var x4 = false;        // new primitive boolean
    var x5 = [];           // new array object
    var x6 = /()/;         // new regexp object
    var x7 = function(){}; // new function object

Function declarations within blocks:
------------------------------------

Do not do this:

.. code-block:: js

    if (x) {
      function foo() {}
    }

While most script engines support Function Declarations within blocks it is not part of
ECMAScript (see ECMA-262, clause 13 and 14). Worse implementations are inconsistent with
each other and with future EcmaScript proposals. ECMAScript only allows for Function
Declarations in the root statement list of a script or function. Instead use a variable
initialized with a Function Expression to define a function within a block:

Namespace:
----------

The first step to good JavaScript object management is having a namespace, or a JavaScript
object that contains our code and data, that you know will not conflict with other extensions.

.. code-block:: js

    /**
     * myNamespace namespace.
     */
    if (typeof myNamespace == "undefined") {
        var myNamespace = {};

        foo: function() {
        },

        bar: function() {
        }
    };

    myNamespace.foo();


Exception and custom exception:
-------------------------------

You basically can't avoid exceptions if you're doing something non-trivial. go for it.

Without custom exceptions, returning error information from a function that also returns
a value can be tricky, not to mention inelegant. Bad solutions include passing in a
reference type to hold error information or always returning Objects with a potential error
member. These basically amount to a primitive exception handling hack. Feel free to use
custom exceptions when appropriate.

Multi level prototype:
----------------------

Not preferred by Google. These hierarchies are much harder to get right than they first appear!
For that reason, it is best to use `goog.inherits()` from the Closure Library or a similar
library function.

Source and other documents:
---------------------------

- Conventions:
 - Document proposed by google : https://google.github.io/styleguide/javascriptguide.xml
 - Other document produced by the comunity : https://github.com/rwaldron/idiomatic.js
 (*different tools to validate as jshint*)

- Comment js (example http://usejsdoc.org/)
- Namespace : on Open Orchestra a big part of js and the global scope, a integrator may
  end up inadvertently override a function
- Cutting modules (AMD, ES6 Modules) of the code but also at the file architecture.
- Tests
- files Naming; no special convention exist

*Many links on best practices, books, pattern, framework, test and article on this site :*
http://jstherightway.org/#reading

.. _Distinction between string primitives and String objects: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String?redirectlocale=en-US&redirectslug=JavaScript/Reference/Global_Objects/String#Distinction_between_string_primitives_and_String_objects
.. _Google Style Guide: https://google.github.io/styleguide/javascriptguide.xml?showone=Comments#Comments
.. _GoogleDev: https://developers.google.com/closure/compiler/docs/js-for-compiler?hl=en
.. _const: http://caniuse.com/#feat=const
.. _Let: http://caniuse.com/#feat=let
.. _JsDoc: http://usejsdoc.org/
