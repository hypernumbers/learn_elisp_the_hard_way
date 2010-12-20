============================
Lesson 5 - Writing Functions
============================

----------------
Batch Mode eLisp
----------------

In order to write functions it is necessary to change the way in which eLisp expressions will be evaluated. Instead of invoking expressions in the \*scratch\* buffer it is time to switch to running eLisp in batch mode. 

In batch mode an eLisp file is invoked from the command line. In order to run a batch file called *first_programme.el* the following command would be run from the command line ``emacs --no-site-file --batch first_programme.el``

The option ``--no-site-file`` means that emacs doesn't load any eLisp from the site libraries. By default the ``--batch`` option also includes option ``--no-init-file``. Normally emacs starts and executes a init file. In Ubuntu this file is ``.emacs`` in the users home directory.

Start by creating a new directory, and in that create a file called *message.el*. The contents of that file is a single eLisp expression:

``(message "Bonjour Tout Le Monde")``

The file should be executed by running this batch command in the directory in which you have created *message.el*

``emacs --no-site-file --batch message.el``

The output should be ``Bonjour Tout Le Monde``

--------------------------
Defining A Simple Function
--------------------------

We will start by defining a function. Create a file with the following code in it:

| ``(defun bonjour () (message "Bonjour Tout Le Monde"))``
| ``(bonjour)``

On executing this file the output will be:

``Bonjour Tout Le Monde``

Lets understand what we are seeing. Consider the first line - the operator ``defun`` indicates that we are defining a function. Here it is taking 3 paramaters:

| **1** ``bonjour`` which is the name of the function
| **2** ``()`` which is a list of the parameters that the function will take
| **3** ``(message "Bonjour Tout Le Monde")`` is the body of code that will executed when the function is run

The second line simply executes the fuction ``bonjour``. The function definition states that ``bonjour`` takes no parameters (the list of parameters is empty).

--------------------------------
Defining A More Complex Function
--------------------------------

Lets create a function that takes multiple arguments:

| ``(defun tough_maths (i j k)``
|   ``"jeepers maths is tough!"`` 
|   ``(message (number-to-string (+ i j k))))``
| ``(tough_maths 3 4 5)``

When executed this will return:

``12``

In this case (unlike the simple case) ``defun`` takes 4 parameters and not three. The second paramater ```(i j k)`` is a list of parameters that the function takes. The third parameter is the documentation - it can be a string broken over many lines. The fourth parameter is the body of the function as in the previous example. Notice that in order to write the output the value of the expression ``(+ i j k)`` must be cast to a string with the operator ``number-to-string``.

---------------------
What You Have Learned
---------------------

You have learned how to run eLisp programmes in batch mode, and also how to define simple functions and invoke them.

------------------
Additional Reading
------------------

There is a section of the eLisp Reference Manual entitled `Functions`_.

----------------
Extra Activities
----------------

Write a function with multiple line documentation.


.. _Functions: http://www.gnu.org/software/emacs/elisp/html_node/Functions.html#Functions

