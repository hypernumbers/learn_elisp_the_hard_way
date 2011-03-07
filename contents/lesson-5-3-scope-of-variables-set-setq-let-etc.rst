==========================================================
Lesson 5-3 - Scope Of Variables (set, setq, let, let* etc)
==========================================================

Introduction
------------

Scope is an important concept in programming. When is the variable 'X' this 'X' and not that 'X', from where does 'X' gets its value, how is 'X' changed.

ELisp has 4 different types of scope:

* global scope
* local scope
* buffer-local scope
* terminal-local scope

The type of scope that Elisp implements is *dynamic* scope. The majority of Lisp dialects implement dynamic scope, but they predominately use a different type of scope called *lexical* scope.

A version of lexical scope is available in Elisp by using a package called 'cl'. This will not be discussed in this book.

TODO - add a section on dynamic scope in Elisp versus lexical scope in other Lisps

------------
Global Scope
------------

Let's create a variable with *global scope*. Edit the file ``omar-menu.el`` in ``./emacs.d/omars-dir/``

Add the line:

::

 (setq omars-kills 123)

and then use the menu *Emacs-Lisp -> Evaluate Buffer* to execute that file again.

If you now go to *\*scratch\** and evaluate the variable ``omars-kills`` in it you will see ``123``.

The *global variable* ``omars-kills`` is available to any line of any function in the programme.

This is what we techies call **A Bad Thing**, or to put it another way **A Really Bad Thing (TM) (C) (R)**.

At least in ELisp you have to explicity make a symbol have global scope - unlike Javascript where you can make a global scope variable by accident.

------------------------------------
The Dastardly Nature Of Global Scope
------------------------------------



Buffer-Local Variables
----------------------

We have seen that Elisp has some variables that *appear* global in scope. We looked at the variable ``fill-column`` in lesson 2-4 and it appeared to be one such.

If we evaluate ``fill-column`` in *\*scratch\** we get the value:

::

 fill-column ;;its not in brackets because it is not a function!
 70

(remember to evaluate an expression in *\*scratch\** use *[Crtl]-j*)

But if we use ``describe-variable`` to see the definition of ``fill-column`` it tells a slightly different story:

::

 fill-column is a variable defined in `C source code'.
 Its value is 70

  Automatically becomes buffer-local when set in any fashion.
  This variable is safe as a file local variable if its value
  satisfies the predicate `integerp'.

 Documentation:
 *Column beyond which automatic line-wrapping should happen.
 Interactively, you can set the buffer local value using C-x f.

 You can customize this variable.

The thing that should get your eyebrows raised is the phrase *buffer-local*. What this means is that ``fill-column`` isn't actually a *global-variable* there is a ``fill-column`` variable for each buffer.

This chapter will look at how that sort of local scope is implemented in Elisp.

---------------------
What You Have Learned
---------------------

------------------
Additional Reading
------------------

Richard Stallman laid out the rationale for dynamic binding in a `paper`_ he wrote for the ACM Conference on Text Processing.

----------------
Extra Activities
----------------


.. _paper: http://www.gnu.org/software/emacs/emacs-paper.html#SEC15
