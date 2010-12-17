===================================
Lesson 2 - Primitive Data Types (1)
===================================

-------
Context
-------

The previous lessons looked at performing basic arithmetic operations on various sorts of numbers.

This lessons will look at the other sorts of data types in eLisp. There are two different sorts of data types:

* primitive data types
* non-primitive data types

The diference between them is that non-primitive data types can be assembled from primitive ones.

The general set of primitive data types of eLisp are:

* integer
* float
* character
* string
* bool-vector
* symbol
* sequence
* cons
* array
* vector
* char-table
* hash-table
* function
* primitive function (or subr)
* macro
* byte-code
* auto-load

These primitive data types largely correspond to the primitive data types of other Lisps.

In addition eLisp has a number of primitive data types that are peculiar to it, because they pertain to the fact that eLisp is the scripting language of an editor. These primitive data types are:

* buffer
* marker
* window
* frame
* terminal
* window configuration
* frame configuration
* process
* stream
* keymap
* overlay
* font

.. warning:: 

   don't really understand types, primitive and otherwise...

---------------------------
What This Lesson Will Cover
---------------------------

This lesson will cover the following data types:

* character
* string

It will also show how boolean values are represented.

The integer and float data types have already been introduced in the previous lesson and they will also be used here.

This section will cover:
* testing for data types
* how eLisp casts values between data types 

--------
Booleans
--------

Booleans represents *true* and *false*. 

:You Type: ``(= 1 1)``
:Result: ``t``

This function tests for equality. The value ``t`` is a boolean (ie means *true*). This expression (which means *is 1 equal to 1*) is easy to switch to test for false.

:You Type: ``(= 1 2)``
:Result: ``nil``

The value ``nil`` is the second boolean it means *false*. The two values ``t`` and ``nil`` are *constant values* that always evaluate to themselves.

We can use the function ``if`` to investigate the boolean types. ``if`` takes three parameters, it is a standard ternary if function familiar from other langauges.

:You Type: ``(if t "it's true" "it's false")``
:Result: ``"it's true"``

The eLisp ``if`` behaves as you would expect, returning the 3rd paramater if the second is true, and the 4th if it is not.

:You Type: ``(if nil "it's true" "it's false")``
:Result: ``"it's false"``

However booleans are not types. They are called *Constant Variables*.

Handling *true/false* is not so simple however consider the following:

:You Type: ``(if () "it's true" "it's false")``
:Result:  ``nil``

The empty list ``()`` is also a synomym for false. ``if``, however, follows the convention that *that which is not false is true* as we can see from the following:

:You Type: ``(if 101 "it's true" "it's false")``
:Result: ``"it's true"``

There are a whole class of functions that operate on data types - the so-called *predicates*.

:You Type: ``(integerp 11)``
:Result: ``t``

This predicate function (like most predicate functions) can be recognised by the fact that it sends in p

:You Type: ``(integerp (+ 1 2.0))``
:Result: ``nil``

We see from this example that data types cast automatically. The sum of an integer and a float is a float - and the predicate therefore fails.

Certain functions expect certain types - for instance ``+`` expects numbers as it parameters.

:You Type: ``(+ 1 2 "three")``
:Result: The functions throws an error and dumps you into the debugger. This is in a window called \*backtrace\*. It is worth looking at the output in some detail.

| ``Debugger entered--Lisp error: (wrong-type-argument number-or-marker-p "three")``
|  ``+(1 2 "three")``
|  ``eval((+ 1 2 "three"))``
|  ``eval-last-sexp-1(t)``
|  ``eval-last-sexp(t)``
|  ``eval-print-last-sexp()``
|  ``call-interactively(eval-print-last-sexp nil nil)``
|  ``recursive-edit()``
|  ``byte-code(`` *byte stream redacted* and *big mess of arguments redacted* ``)``

:You Type: 
:Result: 




------------------
Additional Reading
------------------

There is a section on data types in the `GNU Emacs Lisp Reference Manual`_.

----------------
Extra Activities
----------------

List gets its name from LIS(t) P(rocessing) - and yet lists don't appear as a primitive data types. From the additional reading can you work out why?

What do the following predicate functions do:
floatp
numberp
zerop
wholenump

.. _GNU Emacs Lisp Reference Manual: http://www.gnu.org/software/emacs/emacs-lisp-intro/elisp/Lisp-Data-Types.html#Lisp-Data-Types
