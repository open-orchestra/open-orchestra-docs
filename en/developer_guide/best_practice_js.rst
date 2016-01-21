Best practices :
================

JavaScript is the main client-side scripting language used by many of open-source projects. This style guide is a list
of dos and don'ts for JavaScript programs.

Basic :
=======

Conventions:
------------

Variable declarations :
-----------------------

Declarations with var: Always

When you fail to specify var, the variable gets placed in the global context, potentially altering existing values.
Also, if there's no declaration, it's hard to tell in what scope a variable lives. So always declare with var.

Constant declarations:
----------------------

Use `NAMES_LIKE_THIS` for constant values.
Use `@const` to indicate, on comment, a constant (non-overwritable) pointer (a variable or property).
Never use the `const` keyword as it's not supported in Internet Explorer before version 11 or not full supported.
http://caniuse.com/#feat=const

Semilicons:
-----------

Semicolons should be included at the end of function expressions, but not at the end of function declarations. The distinction is best illustrated with an example:

var foo = function() {
  return true;
};  // semicolon here.

function foo() {
  return true;
}  // no semicolon here.


Standards Feature:
------------------

Always preferred over non-standards features

For maximum portability and compatibility, always prefer standards features over non-standards features
(e.g., string.charAt(3) over string[3], ...).

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
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String?redirectlocale=en-US&redirectslug=JavaScript/Reference/Global_Objects/String#Distinction_between_string_primitives_and_String_objects

Function declarations within blocks:
------------------------------------

Do not do this:

.. code-block:: js
    if (x) {
      function foo() {}
    }

While most script engines support Function Declarations within blocks it is not part of ECMAScript
(see ECMA-262, clause 13 and 14). Worse implementations are inconsistent with each other and with future
EcmaScript proposals. ECMAScript only allows for Function Declarations in the root statement list of a script or
function. Instead use a variable initialized with a Function Expression to define a function within a block:

.. code-block:: js
    if (x) {
      var foo = function() {};
    }

Exception and custom exception:
-------------------------------
You basically can't avoid exceptions if you're doing something non-trivial. <go for it.

Without custom exceptions, returning error information from a function that also returns a value can be tricky, not to mention inelegant. Bad solutions include passing in a reference type to hold error information or always returning Objects with a potential error member. These basically amount to a primitive exception handling hack. Feel free to use custom exceptions when appropriate.

Multi level prototype:
----------------------

Not preferred by Google.
These hierarchies are much harder to get right than they first appear!
For that reason, it is best to use `goog.inherits()` from the Closure Library or a similar library function.



Source and other documents:
---------------------------

- Conventions:
 - Document proposed by google : https://google.github.io/styleguide/javascriptguide.xml
 - Other document produced by the comunity : https://github.com/rwaldron/idiomatic.js
 (*different tools to validate as jshint*)

- Comment js (example http://usejsdoc.org/)
- Namespace : on Open Orchestra a big part of js and the global scope, a integrator may end up inadvertently
  override a function
- Cutting modules (AMD, ES6 Modules) of the code but also at the file architecture.
- Tests
- files Naming; no special convention exist

*Many links on best practices, books, pattern, framework, test and article on this site :*
http://jstherightway.org/#reading
