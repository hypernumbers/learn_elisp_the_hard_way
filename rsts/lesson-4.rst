================================
Lesson 4 - Symbols And Variables
================================

-------
Symbols
-------

Before you can start building functions we need to understand what symbols are. We have seen expressions like ``(concat "blah" "bleh")``. In that expression ``concat`` is a symbol - a symbol whose value is a function or an operator. Symbols can also have values which are data.

Instances of Data Types evaluate to themselves in eLisp:

:You Type: ``9``
:Result: ``9``

You can evaluate Symbols similarly

:You Type: ``fill-column``
:Result: ``70``

(It might not be ``70`` - but it probably will be). ``fill-column`` is a variable in eLisp with global scope. Later on we will see how this sort of variable will be used and have its value changed.

Variables don't just exist with default values. If you try and use a random symbol in an expression it will fail.

:You Type: ``(+ 1 do_tell)``
:Result: You are dropped into the debugger

| ``Debugger entered--Lisp error: (void-variable do_tell)``
|  ``(+ 1 do_tell)``
|  ``eval((+ 1 do_tell))``
|  ``eval-last-sexp-1(t)``
|  ``eval-last-sexp(t)``
|  ``eval-print-last-sexp()``
|  ``call-interactively(eval-print-last-sexp nil nil)``

The variable ``do_tell`` has been created but its value is *void* and it cannot be used.

You give a symbol a value using the operators ``set`` and ``setq``.

:You Type: ``(set 'do_tell '11)``
:Result: ``11``

If we now evaluate the ``do_tell`` it no longer throws an error:

:You Type: ``do_tell``
:Result: ``11``

Notice that when the value of ``do_tell`` was set ``do_tell`` was quoted viz ``'do_tell``.  The quoting says to eLisp "*don't treat do_tell as a variable is a value to be passed to the operator set*". The operator ``setq`` just *absorbs* that quote and lets you not quote the first parameter.

:You Type: ``(setq do_tell '22)``
:Return: ``22``

We can now use this variable in an expression:

:You Type: ``(+ do_tell 33)``
:Return: ``55``

---------------------
What You Have Learned
---------------------

We have learned how to set values of Symbols and then reuse those symbols in expressions.

----------------
Extra Activities
----------------

If we fail to quote variables properly with the set operator will generate errors. Can you work out what they mean?

| ``(set bleh '(1 2 3))``
| ``(set 'bleh (1 2 3))``
