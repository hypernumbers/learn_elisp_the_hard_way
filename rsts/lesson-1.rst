================================
Lesson 1 - First eLisp Programme
================================

This lesson will show you how to execute your first eLisp programme.

* start Emacs 
* go to the scratch buffer by using the menu `Buffers -> \*scratch\*`

--------------------
What You Should Type
--------------------
``(+ 1 2)``

Now put the cursor at the **end** of the expression - that is to say after the right bracket and type ``Control-j``

-------------------
What You Should See
-------------------
| ``(+ 1 2)``
| ``3``

---------------
What This Means
---------------

What you typed in consists of an expression ``(+ 1 2)`` and a command to Emacs to execute it ``[Control-j]``. Expressions are sometimes called *forms*.

eLisp is a dialect of Lisp - which stands for List Processing. A list is any thing between two brackets ``(`` and ``)``

The programme that was executed consisted of an operator ``+`` and two constants ``1`` and ``2``

The command to Emacs is applied at the point where the cursor is - it evaluates all the eLisp in the window up to that point and prints the output.

Lets look at executing the same expression in a different way. Delete the expression in the \*scracha\* buffer

--------------------
What You Should Type
--------------------
``(+ 1.0 2.0)``

Now put the cursor in the **middle** of the expression - that is to say between the brackets and type ``Control-Alt-x``

-------------------
What You Should See
-------------------

In the window nothing will change
``(+ 1.0 2.0)``

The result of the expression is now put in the *minibuffer*
``3.0``

---------------
What This Means
---------------

The way in which you evaluate the expression determines where the output goes. Alos notice that the previous examples used integers like ``1`` and ``2`` and returned an integer value. This expression uses floating point numbers like ``1.0`` and returns a float as the result.

--------------------
What You Should Type
--------------------
``(+ 1.0e+3 2.0e-2)``

Now put the cursor at the **end** of the expression  and type ``Control-x Control-e``

-------------------
What You Should See
-------------------

In the window nothing will change
``(+ 1.0e+3 2.0-2)``

The result of the expression is now put in the *minibuffer*
``1000.02``

---------------
What This Means
---------------

You can express floating point numbers is scientific notation

---------------------
What You Have Learned
---------------------

You have learned how to evaluate a basic eLisp expression (or form) in the scratch buffer. 

----------------
Extra Activities
----------------

Try some expressions that add integers to floats. What is the result?

What happens if you use scientific integers like ``1e+10``?

Can you add negative numbers?

| What do you think the following expressions will return?
| ``(- 3 4)``
| ``(* 4 5)``
| ``(/ 1.0 4.0)``

| Evaluate the following expression and try and work out why it returns why it does?
| ``(/ 1 4)``
