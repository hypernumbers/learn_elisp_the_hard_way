==================================
Lesson 2-4 - Symbols And Variables
==================================

**Prerequisite:** This lesson presumes you know how to invoke Elisp expression as shown in Lesson 2-1.

----------------
Symbols Overview
----------------

Before you can start building functions we need to understand what symbols are. We have seen expressions like ``(concat "blah" "bleh")``. In that expression ``concat`` is a symbol - a symbol whose value is a function or an operator.

Symbols can contain different things:
 
* operators or functions
* data values
* property lists
* the print name of the symbol

Some symbols are also the so-called *constant variables* - they evaluate to themselves (their data value is their name) and they cannot have their datavalue set to anything else.

The constant values are used to define property lists.

-------------------------
Symbols As Function Names
-------------------------

Symbols can be the name of functions (or operators). We will look into how these are set in a later lesson.

--------------------
Symbols As Variables
--------------------

Instances of Data Types evaluate to themselves in Elisp:

:You Type: ``9``
:Result: ``9``

You can evaluate Symbols similarly

:You Type: ``fill-column``
:Result: ``70``

(It might not be ``70`` - but it probably will be). At a first glance it might appear that ``fill-column`` is a variable in Elisp with global scope - turn out it is a bit more subtle that that as will become apparent in Lesson 5-3. Later on we will see how this sort of variable will be used and have its value changed.

Variables don't just exist with default values. If you try and use a random symbol in an expression it will fail.

:You Type: ``(+ 1 do_tell)``
:Result: You are dropped into the debugger

::

 Debugger entered--Lisp error: (void-variable do_tell)
  (+ 1 do_tell)
  eval((+ 1 do_tell))
  eval-last-sexp-1(t)
  eval-last-sexp(t)
  eval-print-last-sexp()
  call-interactively(eval-print-last-sexp nil nil)

The variable ``do_tell`` has been created but its value is *void* and it cannot be used.

You give a symbol a value using the operators ``set`` and ``setq``. **These define global variables**.

:You Type: ``(set 'do_tell '11)``
:Result: ``11``

If we now evaluate the ``do_tell`` it no longer throws an error:

:You Type: ``do_tell``
:Result: ``11``

Notice that when the value of ``do_tell`` was set ``do_tell`` was quoted viz ``'do_tell``.  The quoting says to Elisp "*don't treat do_tell as a variable is a value to be passed to the operator set*". The operator ``setq`` just *absorbs* that quote and lets you not quote the first parameter.

:You Type: ``(setq do_tell '22)``
:Return: ``22``

We can now use this variable in an expression:

:You Type: ``(+ do_tell 33)``
:Return: ``55``

There is a variant on ``set`` and ``setq`` called ``defvar`` that defines a variable. It is different from them in that it only applies to uninitialised variables. If a variable is already defined it won't overwrite it.

:You Type: ``(defvar farmer_dell 123)``
:Return: ``farmer_dell``

We can now see what ``defvar`` has done to the variable ``farmer_dell`` by evaluating that:

:You Type: ``farmer_dell``
:Return: ``123``

But if we ``defvar`` on ``do_tell`` it won't take:

:You Type: ``(defvar do_tell 123)``
:Return: ``do_tell``

and now evaluate ``do_tell``:

:You Type: ``do_tell``
:Return: ``33``

(This only works if you have used ``set`` or ``setq`` to define ``do_tell`` in the \*scratch\* buffer earlier in the same editing session).

--------------------------------------
Constant Variables And Keyword Symbols
--------------------------------------

Some symbols can't be redefined. We have met a couple of them before ``nil`` and ``t``. Dy design all symbols which begin with ``:`` are also constant values.

If you try and set a symbol whose name starts with ``:`` you will get an error.

:You Type: ``(setq :hotdog 3)``
:Return: ``Debugger entered--Lisp error: (setting-constant :hotdog) ...``

An alternative name for a symbol which starts with ``:`` is a keyword symbol and these *constant variables* are commonly used as keywords in property lists.

--------------
Property Lists
--------------

Property lists are lists where each pair of concurrent values are regarded as a pair. The two values can be anything, but conventionally the first of them is a constant variable with a name beginning with ``:``. Here is an example:

``(:quality "great" :achievement "impressive")``

The relationship of property lists with symbols is a bit messy and is discussed in the *Extra Activities* section of this lesson.

---------------------
What You Have Learned
---------------------

You have learned how to set values of Symbols and then reuse those symbols in expressions.

------------------
Additional Reading
------------------

Symbols in Elisp are a bit more complex than symbols in other languages - there is a discussion of `Symbols`_ in the *Introduction To Emacs Lisp* manual.

You can read about `Symbol Properties`_ in the *Emacs Lisp Reference* manual.

------------------------
Extra Quoting Activities
------------------------

If we fail to quote variables properly with the set operator will generate errors. Can you work out what they mean?

| ``(set bleh '(1 2 3))``
| ``(set 'bleh (1 2 3))``

----------------------------
Extra Property List Activity
----------------------------

Property lists can be the *value* of a symbol and are associated with it by ``setq``:

:You Type: ``(setq hotdog '(:quality "great" :achievement "impressive"))``
:Return: ``(:quality "great" :achievement "impressive")``

But the symbol can also have its own *plist* which is created by the special function ``setplist``. (the symbol must already have been created.)

:You Type: ``(setplist 'hotdog '(:rhubarb "custard" :status "borked"))``
:Return: ``(:rhubarb "custard" :status "borked")``

However if we now evaluate the value of ``hotdog`` you will see that it is ``(:quality "great" :achievement "impressive")`` as that is the *value* we set previously:

:You Type: ``hotdog``
:Return: ``(:quality "great" :achievement "impressive")``

What happens if you try and set the property list of an undefined symbol?

.. _Symbols: http://www.gnu.org/software/emacs/emacs-lisp-intro/elisp/Symbol-Components.html#Symbol-Components

.. _Symbol Properties: http://www.gnu.org/software/emacs/elisp/html_node/Symbol-Plists.html#Symbol-Plists
