==========================
Lesson 3 - Lists (At Last)
==========================

------------
Introduction
------------

eLisp is a dialect of Lisp - the LISt Processing language.

You will have noticed that all the expressions we have used so far has been of the form ``(something somethingelse anotherthing)``. That basic form is a list - defined by the opening and closing brackets. All the expressions we have looked at so far have been programmes - lists where the first element is an operator and the remaining elements are data. But a list can also be simple data.

----------
Data Lists
----------

The eLisp interpreter has to be told that it is a data list. This is done by **quoting** it with a single quote.

:You Type: ``'(1 2 3)``
:Result: ``(1 2 3)``

The apostrophe ``'`` is syntactic sugare for the quote operator which can be invoked like a normal operator:

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


