====================================================
Lesson 5-3 - Scope Of Variables (set, setq, let etc)
====================================================

We have seen that eLisp has some variables that *appear* global in scope. We looked at the variable ``fill-column`` in lesson 2-4 and it appeared to one such.

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

This chapter will look at how that sort of local scope is implemented in eLisp.

------------
Global Scope
------------

Lets create a variable with *global scope*. Edit the file ``omar-menu.el`` in ``./emacs.d/omars-dir/``

Add the line:

::
 (setq omars-kills 123)

and then use the menu *Emacs-Lisp -> Evaluate Buffer* to execute that file again.

If you now go to *\*scratch\** and evaluate the variable ``omars-kills`` in it you will see ``123``.

The *global variable* ``omars-kills`` is available to any line of any function in the programme.

This is what we techies call **A Bad Thing**, or to put it another way **A Really Bad Thing (TM) (C) (R)**. 

------------------------------------
The Dastardly Nature Of Global Scope
------------------------------------

---------------------
What You Have Learned
---------------------

------------------
Additional Reading
------------------

----------------
Extra Activities
----------------


