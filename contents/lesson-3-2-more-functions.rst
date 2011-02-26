===========================
Lesson 3-2 - More Functions
===========================

**Prerequisite:** This lesson presumes you know how to invoke Elisp expression as scripts as shown in Lesson 3-1.

------------
Introduction
------------

The functions we built in the previous lesson were a bit useless. This lesson will look at some more sophisticated functions:

* ones which can use local variables
* recursive functions

------------------------------
Functions With Local Variables
------------------------------

We have seen how to use ``set`` and ``setq`` to set *global* variables. Global variables are very ugly to use as they can be changed from anywhere and at anytime. This makes them very hard to reason about, and hence to use safely and debug.

It is important to be able to define *local* variables - variables which can only be set and changed locally from a small number of defined and known places.

The function used to do this is ``let``. It works like ``set``.

Type the following expressions in a file:

| ``(let ((first "hey")``
|  ``(second "ho"))``
|  ``(message first)``
|  ``(message second))``

The output should be:

| ``hey``
| ``ho``

If you carefully count the brackets you will see that ``(first "hey")`` and ``(second "ho")`` are both within a list that is the first parameter of ``let``. The scope of those variables is then the list that makes up the rest of the expression that has ``let`` as its operator.

We can see that this is the case by adding another message line:

| ``(let ((first "hey")``
|  ``(second "ho"))``
|  ``(message first)``
|  ``(message second))``
| ``(message first)``

When we try and run this we get an error message printed out:

| ``hey``
| ``ho``
| ``Symbol's value as variable is void: first``

This can now be used to make functions which are safe to use. Type in the following function:

| ``(defun myfun (a b c d)``
|   ``"This is a nonce function designed to show how to``
|   ``use local variables safely"``
|     ``(let ((e (+ a b))``
|          ``(f (* c d)))``
|     ``(- e f)))``
| ``(message (number-to-string (myfun 7 5 3 1)))``

The result should be:

``9``

Check that result yourself by working through the arithmetic.

-------------------
Recursive Functions
-------------------

Recursive functions are an important part of functional programming. A recursive function is simply one that calls itself

Create the following file:

| ``(defun print_int (n)``
|   ``"This function prints a list of integers in reverse order"``
|    ``(message (number-to-string n))``
|    ``(if (= n 0) (message "That's all folks!") (print_int (- n 1))))``
| ``(print_int 5)``

Your output should be:

| ``5``
| ``4``
| ``3``
| ``2``
| ``1``
| ``0``
| ``That's all folks!``

The key is the ``if`` expression. The first expression is *the terminal test*. If it is true the function prints "*That's all folks!*". If the terminal test is not met (ie it is false) the function calls itself with a value of the current value of ``n - 1``.

---------------------
What You Have Learned
---------------------

You have learned how to build basic functions with local variables and then how to build functions that call themselves.

------------------
Additional Reading
------------------

There is a section on `Recursive Functions`_ in the Gnu Emacs Lisp Intro.

----------------
Extra Activities
----------------

Write a recursive function to calculate the factorial of an integer.

.. _Recursive Functions: http://www.gnu.org/software/emacs/emacs-lisp-intro/html_node/Recursive-Definition-Parts.html#Recursive-Definition-Parts
