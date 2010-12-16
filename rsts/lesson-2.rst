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

---------------------------
What This Lesson Will Cover
---------------------------

This lesson will cover the following data types:

* character
* string
* bool-vectr

The integer and float data types have already been introduced in the previous lesson and they will also be used here.

--------
Booleans
--------

The boolean data-type represents *true* and *false*. 

:You Type: ``(= 1 1)``
:Result: ``t``
:This Means: This function tests for equality. The value ``t`` is a boolean (ie means *true*).

This expression (which means *is 1 equal to 1*) is easy to switch to test for false.

:You Type: ``(= 1 2)``
:Result: ``nil``
:This Means: The value ``nil`` is the second boolean it means *false*

The two values ``t`` and ``nil`` are *constant values* that always evaluate to themselves.


:You Type: 
:Result: 
:This Means: 


------------------
Additional Reading
------------------

There is a section on data types in the `GNU Emacs Lisp Reference Manual`_.

----------------
Extra Activities
----------------

List gets its name from LIS(t) P(rocessing) - and yet lists don't appear as a primitive data types. From the additional reading can you work out why?


.. _GNU Emacs Lisp Reference Manual: http://www.gnu.org/software/emacs/emacs-lisp-intro/elisp/Lisp-Data-Types.html#Lisp-Data-Types
