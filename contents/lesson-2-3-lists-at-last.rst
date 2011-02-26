============================
Lesson 2-3 - Lists (At Last)
============================

**Prerequesite:** This lesson presumes you know how to invoke Elisp expression as shown in Lesson 2-1.

------------
Introduction
------------

Elisp is a dialect of Lisp - the LISt Processing language.

You will have noticed that all the expressions we have used so far have been of the form ``(something somethingelse anotherthing)``. That basic form is a list - defined by the opening and closing brackets. All the expressions we have looked at so far have been the simplest sort of programmes - lists where the first element is an operator and the remaining elements are data. But a list can also be simple data.

----------
Data Lists
----------

The Elisp interpreter has to be told that it is a data list. This is done by **quoting** it with a single quote.

:You Type: ``'(1 2 3)``
:Result: ``(1 2 3)``

The apostrophe ``'`` is syntactic sugar for the quote operator which can be invoked like a normal operator:

:You Type: ``(quote (1 2 3))``
:Result: ``(1 2 3)``

You can also make a list with the list operator:

:You Type: ``(list 1 2 3)``
:Result: ``(1 2 3)``

It all seems so reasonable, but wait, lets try that again.

:You Type: ```(1 2 3)``
:Result: ``(1 2 3)``

"*Ah, we have just done that*" sez you - except we haven't. This last example has a **backtick** ````` and not a **single quote** ``'``. The backtick is a different operator which, in this instance, just produces a list. In other circumstances it behaves very differently to the single quote operator.

------------------
Nested Expressions
------------------

You can nest expressions.

:You Type: ``(+ 1 (* 2 3))``
:Result: ``7``

The inner expression is evaluated first:

:Inner: ``(* 2 3)``
:Result: ``6``

This is then put into the outer expression which is then evaluated:

:Outer: ``(+ 1 6)``
:Result: ``7``

---------------------
What You Have Learned
---------------------

One of the great simplicities of Lisp is that data and programmes are very similar - both are lists - and that you can manipulate programmes as if they were data.

We have previously seen *lists-as-programmes* and this section has looked at *lists-as-data* and the nesting of lists.

----------------
Extra Activities
----------------

There are three additional functions that can be used to make and break lists ``cons``, ``car`` and ``cdr``.

``cons`` is short for constructs and is used to build lists. ``car`` and ``cdr`` take their name from assembly code instructions whose meanings may as well be lost in the mists of time.

You build a lists with ``cons`` like this:

:You Type: ``(cons 1 '(2 3))``
:Result: ``(1 2 3)``

``cons`` adds a new value to the start or *head* of a list. Note that the list to which you are adding it has to be quoted.

You can split a list into two parts - the first value (the *head*) and the remaining ones (the *tail*). The head is extracted with ``car``:

:You Type: ``(car '(1 2 3))``
:Result: ``1``

The tail is extracted with ``cdr``:

:You Type: ``(cdr '(1 2 3))``
:Result: ``(2 3)``


