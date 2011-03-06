==================================
Lesson 2-1 - First Elisp Programme
==================================

-----------------
Let's Get Started
-----------------

This lesson will show you how to execute your first Elisa programme.

* start Emacs 
* go to the scratch buffer by using the menu `Buffers -> \*scratch\*`

:You Type: ``(+ 1 2)``

Then put the cursor at the **end** of the expression - that is to say after the right bracket and type ``Control-j``

:Result: ``3``

What you typed in consists of an expression ``(+ 1 2)`` and a command to Emacs to execute it ``[Control-j]``. Expressions are sometimes called *forms*.

Elisp is a dialect of Lisp - which stands for List Processing. A list is any thing between two brackets ``(`` and ``)``

The programme that was executed consisted of an operator ``+`` and two constants ``1`` and ``2``

The command ``Control-j`` in Emacs is applied at the point where the cursor is - it evaluates all the Elisp in the window up to that point and prints the output.

Let's look at executing the same expression in a different way. Delete the expression in the \*scratch\* buffer and type in a new one.

:You Type: ``(+ 1.0 2.0)``

Now put the cursor in the **middle** of the expression - that is to say between the brackets and type ``Control-Alt-x``

:Result: In the window nothing will change. The result of the expression is now put in the *minibuffer* ``3.0``

It seems as if the way in which you evaluate the expression determines where the output goes - that is a bit of a simplification. See the *Advanced* sub-section for a deeper discussion. Also notice that the previous examples used integers like ``1`` and ``2`` and returned an integer value. This expression uses floating point numbers like ``1.0`` and returns a float as the result.

:You Type: ``(+ 1.0e+3 2.0e-2)``

Now put the cursor at the **end** of the expression and type ``Control-x Control-e``

:Result: In the window nothing will change by the value is now placed in the *minibuffer* ``1000.02``

You can express floating point numbers in scientific notation.

--------------------
What You Have Learnt
--------------------

You have learnt how to evaluate a basic Elisp expression (or form) in the scratch buffer. 

**In future lessons you will not be told how to evaluate an expression - be sure to remember the key sequences to do it.**

------------------
Additional Reading
------------------

There is a section on data types in the `GNU Emacs Lisp Reference Manual`_.

--------
Advanced
--------

Elisp, like all the Lisp family, is a functional language. In functional languages there is a strict differences between a pure function and a function which has side effects.

A pure function is one which takes some parameters and returns a value - the same input parameters reliably returning the same value.

A function with side-effects interacts with the outside world: it writes to a file, or it sets a global variable. Sometimes it lets the outside world in - for instance a function that returns a random number.

In this section we talk about evaluating expression and them returning values to the \*scratch\* buffer or the modeline. In fact, we evaluate a function which evaluates an expression and then, as a side effect, writes the return value to \*scratch\* or the modeline.

This might seem an esoteric distinction now, but it is important and will become even more later on.

----------------
Extra Activities
----------------

Try some expressions that add integers to floats. What is the result?

What happens if you use scientific integers like ``1e+10``?

Can you add negative numbers?

What do you think the following expressions will return?

| ``(- 3 4)``
| ``(* 4 5)``
| ``(/ 1.0 4.0)``

Evaluate the following expressions and try and work out why they return what they do?

| ``(/ 1 4)``
| ``(/ 1 4.)``

What do you think these symbols represent?

| ``#b10101010``
| ``#o127``
| ``#x12DE``
| (**Tip**: try using them in arithmetic expressions)

What do you think these symbols represent?

| ``1.0e+INF``
| ``-1.0e+INF``
| ``0.0e+NaN`` or ``-0.0e+NaN``

.. _GNU Emacs Lisp Reference Manual: http://www.gnu.org/software/emacs/emacs-lisp-intro/elisp/Numbers.html#Numbers
