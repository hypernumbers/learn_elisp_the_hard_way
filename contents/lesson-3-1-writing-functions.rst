==============================
Lesson 3-1 - Writing Functions
==============================

-----------------
Script Mode Elisp
-----------------

In order to write functions it is necessary to change the way in which Elisp expressions will be evaluated. Instead of invoking expressions in the \*scratch\* buffer it is time to switch to running Elisp as a script. 

To do this an Elisp file has to be invoked from the command line. If you had some Elisp expressions in a file called *first_programme.el* the following command would be run it as a script ``emacs --no-site-file --script first_programme.el``

The option ``--no-site-file`` means that emacs doesn't load any Elisp from the site libraries. By default the ``--script`` option also includes option ``--no-init-file``. Normally emacs starts and executes a init file. In Ubuntu this file is ``.emacs`` in the users home directory.

Start by creating a new directory, and in that create a file called *message.el*. The contents of that file is a single Elisp expression:

::

 (message "Bonjour Tout Le Monde")

The file should be executed by running this batch command in the directory in which you have created *message.el*

::

 emacs --no-site-file --script message.el

The output should be ``Bonjour Tout Le Monde``

--------------------------
Defining A Simple Function
--------------------------

We will start by defining a function. Create a file with the following code in it:

::

 (defun bonjour () (message "Bonjour Tout Le Monde"))
 (bonjour)

On executing this file the output will be:

::

 Bonjour Tout Le Monde

Let's understand what we are seeing. Consider the first line - the operator ``defun`` indicates that we are defining a function. Here it is taking 3 parameters:

| *1* ``bonjour`` which is the name of the function
| *2* ``()`` which is a list of the parameters that the function will take
| *3* ``(message "Bonjour Tout Le Monde")`` is the body of code that will executed when the function is run

The second line simply executes the fuction ``bonjour``. The function definition states that ``bonjour`` takes no parameters (the list of parameters is empty).

--------------------------------
Defining A More Complex Function
--------------------------------

Let's create a function that takes multiple arguments:

::

 (defun tough_maths (i j k)
   "jeepers maths is tough!" 
   (message (number-to-string (+ i j k))))
 (tough_maths 3 4 5)

When executed this will return:

::
 
 12

In this case (unlike the simple case) ``defun`` takes 4 parameters and not three. The second paramater ```(i j k)`` is a list of parameters that the function takes. The third parameter is the documentation - it can be a string broken over many lines. The fourth parameter is the body of the function as in the previous example. Notice that in order to write the output the value of the expression ``(+ i j k)`` must be cast to a string with the operator ``number-to-string``.

--------------------------------------------
Functions With Variable Numbers Of Arguments
--------------------------------------------

We have seen that the function ``defun`` has variable arity - that is to say it can take 3 or 4 arguments - we will see later that it can actually take 5 parameters.

Let's write a variable arity function:

::

 (defun variable_arity (a &optional b &rest c)
    "This is a function which has variable arity"
    (message (concat "variable a is " a))
    (message (concat "variable b is " b))
    (if c (message "c is not an empty list") (message "c is an empty list")))
 (message "run the fn with 1 variable")
 (variable_arity "eh")
 (message "run the fn with 2 variables")
 (variable_arity "eh" "bee")
 (message "run the fn with 3 variables")
 (variable_arity "eh" "bee" "see")
 (message "run the fn with 4 variables")
 (variable_arity "eh" "bee" "see" "dee")
 (message "run the fn with 5 variables")
 (variable_arity "eh" "bee" "see" "dee" "eee")


The result is:

::

 run the fn with 1 variable
 variable a is eh
 variable b is
 c is an empty list
 run the fn with 2 variables
 variable a is eh
 variable b is bee
 c is an empty list
 run the fn with 3 variables
 variable a is eh
 variable b is bee
 c is not an empty list
 run the fn with 4 variables
 variable a is eh
 variable b is bee
 c is not an empty list
 run the fn with 5 variables
 variable a is eh
 variable b is bee
 c is not an empty list

The important part of this is the first part of the function definition ``(defun variable_arity (a &optional b &rest c)...``. ``a`` is a required option - calling ``variable_arity`` with zero parameters will result in an error. The marker ``&optional b`` indicates that the subsequent parameter ``b`` is optional. In this function there is only one optional function but a clause like ``(i j &optional k l m)`` would have three optional arguments. The final clause ``&rest c`` indicates that all parameters from 3 onwards will be collected into the variable ``c`` as a list. You can have either ``&optional`` or ``&rest`` or both together as in this function.

---------------------
What You Have Learned
---------------------

You have learned how to run Elisp programmes in batch mode, and also how to define simple, more complex and variable arity functions and invoke them.

------------------
Additional Reading
------------------

There is a section of the Elisp Reference Manual entitled `Functions`_.

----------------
Extra Activities
----------------

Write a function with multiple line documentation.

The *required*, *optional* and *rest* clauses must be specified in that order. Can you work out why? 


.. _Functions: http://www.gnu.org/software/emacs/elisp/html_node/Functions.html#Functions

