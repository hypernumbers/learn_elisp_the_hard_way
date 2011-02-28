======================================
Best Practice 1 - Writing Better Elisp
======================================

------------
Introduction
------------

So far we have knocked up quick'n'dirty Elisp. As we get deeper into writing Elisp it is important to start following best practices to try and make sure our code is clean, good and easy to maintain.

Best practices will be introduced in small chapters like this.

------------------------------
Avoiding Name Space Collisions
------------------------------

Emacs (and the Elisp it is written in) uses a lot of global state to manage itself. One of the problems with global state is that it can lead to developers accidentally overwriting other peoples function definitions and variables through name space collisions.

When writing custom code for Emacs you should choose a name that describes what you are doing and use that as a prefix on all your variable and function definitions.

For the rest of this book our chosen name is *omar*. Why omar? I like *The Wire* so why not.

-----------------------------
Which Keys Should You Bind To
-----------------------------

Emacs as an editor has an emphasis on keyboard shortcuts. There are lots of different add-ons and packages, major and minor modes, all of which use keyboard short cuts.

If you start binding functions to key combinations randomly you may well start breaking other parts of Emacs.

There are a complex set of conventions about which keys you should use - but we will conform to the most basic set of there here.

The following keys are reserved for the use of users:

* *[F5]* to *[F9]*
* *[C-c][a]* to *[C-c][z]*

We will follow these conventions.

------------------
Additional Reading
------------------

There are more `Coding Conventions`_ for writing Elisp additional and rules about `Key-Binding Conventions`_ in the *Emacs Lisp Reference Manual*.

.. _Coding Conventions: http://www.gnu.org/software/emacs/elisp/html_node/Coding-Conventions.html#Coding-Conventions

.. _Key-Binding Conventions: http://www.gnu.org/s/emacs/manual/html_node/elisp/Key-Binding-Conventions.html#Key-Binding-Conventions
