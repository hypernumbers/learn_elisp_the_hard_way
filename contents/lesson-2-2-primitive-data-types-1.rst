=====================================
Lesson 2-2 - Primitive Data Types (1)
=====================================

**Prerequisite:** This lesson presumes you know how to invoke Elisp expression as shown in Lesson 2-1.

-------
Context
-------

The previous lessons looked at performing basic arithmetic operations on various sorts of numbers.

This lessons will look at the other sorts of data types in Elisp. There are two different sorts of data types:

* primitive data types
* non-primitive data types

The difference between them is that non-primitive data types can be assembled from primitive ones.

The general set of primitive data types of Elisp are:

* integer
* float
* string
* character
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

In addition Elisp has a number of data types that are peculiar to it, because they pertain to the fact that Elisp is the scripting language of an editor. These data types are:

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

This lesson will look at:

* the representation of boolean values
* the integer and float data types which were introduced earlier
* the string data type
* testing for data types
* casting between values

--------
Booleans
--------

Booleans represent *true* and *false*. 

:You Type: ``(= 1 1)``
:Result: ``t``

This function tests for equality. The value ``t`` is a boolean (ie means *true*). This expression (which means *is 1 equal to 1*) is easy to switch to test for false.

:You Type: ``(= 1 2)``
:Result: ``nil``

The value ``nil`` is the second boolean it means *false*. The two values ``t`` and ``nil`` are *constant values* that always evaluate to themselves.

We can use the function ``if`` to investigate the boolean types. ``if`` takes three parameters, it is a standard ternary if function familiar from other langauges.

:You Type: ``(if t "it's true" "it's false")``
:Result: ``"it's true"``

You can read the if expression like this ``if t`` *is true then return* ``"it's true"`` *if it isn't then return* ``"it's false"``.

:You Type: ``(if nil "it's true" "it's false")``
:Result: ``"it's false"``

However booleans are not types. They are called *Constant Variables*.

Handling *true/false* is not so simple, however. Consider the following:

:You Type: ``(if () "it's true" "it's false")``
:Result:  ``"it's false"``

The empty list ``()`` is also a synomym for false. ``if``, however, follows the convention that *that which is not false is true* as we can see from the following:

:You Type: ``(if 101 "it's true" "it's false")``
:Result: ``"it's true"``

-------
Strings
-------

We have seen string data types being used in the previous tests - strings are represented by characters between double quotes. 

:You Type: ``(concat "ab" "cd")``
:Result: ``"abcd"``

``concat`` is just a string concatenation function. The strings can include single quotes and escaped double quotes.

:You Type: ``(concat "a`b" "c\"d")``
:Result: ``"a'bc\"d"``

The ``concat`` operator can have a indefinite number of arguments.

:You Type: ``(concat "ab" "cd" "ef" "12" "34" "45")``
:Result: ``"abcdef123445"``

-------------------------------------------------
Predicate Functions - Testing The Types Of Vaules
-------------------------------------------------

There are a whole class of functions that tests data types - the so-called *predicates*.

:You Type: ``(integerp 11)``
:Result: ``t``

This predicate function (like most predicate functions) can be recognised by the fact that it ends in p

:You Type: ``(integerp (+ 1 2.0))``
:Result: ``nil``

We see from this example that data types cast automatically. The sum of an integer and a float is a float - and the predicate therefore fails.

Certain functions expect certain types - for instance ``+`` expects numbers as it parameters.

:You Type: ``(+ 1 "two")``
:Result: The function throws an error and dumps you into the debugger.

This is in a window called \*backtrace\*. It is worth looking at the output in some detail.

::

 Debugger entered--Lisp error: (wrong-type-argument number-or-marker-p "two")
  +(1 "two")
  eval((+ 1 "two"))
  eval-last-sexp-1(t)
  eval-last-sexp(t)
  eval-print-last-sexp()
  call-interactively(eval-print-last-sexp nil nil)

The first line of this give us some details of the problem, it is a Lisp error - the predicate function ``number-or-marker-p`` on the parameter ``two`` threw a ``wrong-type-argument`` error. We will look at the debugger later on in the book. If you go back to the list of Emacs specific types you will see that there is one called marker. The operator ``+`` can operate on numbers or markers and so it uses this special predicate function to test the arguments before running the function.

-----------------------------
Converting Between Data Types
-----------------------------

Sometimes Elisp converts between data types. Consider mixed arithmetic with integers and floating point numbers:

:You Type: ``(+ 1 2.5)``
:Result: ``3.5``

The integer value of ``1`` has been *cast* to a floating point number.

You can force this casting with functions:

:You Type: ``(float 1)``
:Result: ``1.0``

You can turns numbers into string:

:You Type: ``(number-to-string 1234)``
:Result: ``"1234"``

You can also cast strings which contain the numerical characters into numbers:

:You Type: ``(string-to-number "1234")``
:Result: ``1234``

---------------------
What You Have Learned
---------------------

We have seen the list of primitive and composite data types and have looked at a couple of the most common of them in some detail. We have seen how to test what data type an object it, and how to cast one data type to another.

------------------
Additional Reading
------------------

There is a section on data types in the `GNU Emacs Lisp Reference Manual`_.

----------------
Extra Activities
----------------

List gets its name from LIS(t) P(rocessing) - and yet lists don't appear as a primitive data types. From the additional reading can you work out why?

What do the following predicate functions do:

* ``floatp``
* ``numberp``
* ``zerop``
* ``wholenump``

What do the following functions do:

* ``float``
* ``truncate``
* ``ceiling``
* ``floor``

.. _GNU Emacs Lisp Reference Manual: http://www.gnu.org/software/emacs/emacs-lisp-intro/elisp/Lisp-Data-Types.html#Lisp-Data-Types
