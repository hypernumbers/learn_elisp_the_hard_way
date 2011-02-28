=============================================
Lesson 4-2 - Adding Custom Functions To Emacs
=============================================

------------
Introduction
------------

In order to run custom Elisp functions it is necessary to have them loaded into Emacs at run time.

On load time emacs executes a startup file. In Emacs-23 on Ubuntu 10.10 this is a file called ``.emacs`` in your home directory.

This file may or may not exist. Emacs is quite happy for it not to exist. If you change any settings using the *Options* menu and then save them, the results will be written to the ``.emacs`` file.

------------------------
A Simple Custom Function
------------------------

Open the ``.emacs`` file (or create it if it doesn't exist) and add the following function:

::

 (defun doodlebug ()
  "Nonce function"
  (interactive)
  (message "Howdie-doodie fella"))

The first time you do this, edit the ``.emacs`` file and then open Emacs. If you edit it in Emacs you will need to quit and restart.

On starting Emacs all the code in ``.emacs`` is reloaded and evaluated.

This function can be run simply. The command *[Alt][x]* is used to a run a function interactively. Typing *[Alt][x]* switches the focus in Emacs to the minibuffer - if you then type in a function name it will be executed. To run ``doodlebug`` simply type *[Alt][x]* and then *doodlebug*.

You should then see the output in the minibuffer:

::

 Howdie-doodie fella

Look carefully at the function definition. The third parameter of the list is the expression ``(interactive)`` - this is necessary if we are to invoke the function from either a key-binding or the minibuffer.

---------------------------------
A Custom Function With User Input
---------------------------------

Let's edit the function to take some parameters:

::

 (defun doodlebug (a b c)
   "Nonce function"
   (interactive "sAdjective: \nsNoun: \nsExclamation: \n")
   (message "Its a %s thing, this %s, so it is, %s" a b c))

You can't reload the ``.emacs`` file, but you can manually re-evaluated by using the command *Emacs-Lisp -> Evaluate Buffer* in the ``.emacs`` buffer.

When you run this version of the function with *[Alt][x]doodlebug* it will offer up three prompts, to wit:

::

 Adjective:
 Noun:
 Exclamation:

As you type in a string at each prompt (ending with *[Return]*) each of the strings wll be bound to the variables ``a``, ``b`` and ``c`` in turn.

This behaviour in enabled by the new form of the *interactive* expression. The string which has been added to that expression consists of 6 separate components:

::

 s
 Adjective: \n
 s
 Noun: \n
 s
 Exclamation: \n

The 2nd, 4th and 6th parts are the prompts which will be shown in the minibuffer. The three ``s``'s are Interactive Codes  which refer to strings (ie key sequences terminated with *[Return]* which are entered at the prompt. There are a range of other Interative Codes, some of which are:


| ``a`` - a function name
| ``b`` - the name of an existing buffer
| ``B`` - the name of a buffer which may or may not exist
| ``c`` - a character
| ``C`` - a command
| etc, etc

You can read the full list of `Interactive Codes`_ in the reference manual

---------------------------------------------
Binding The Custom Function To A Key Sequence
---------------------------------------------

To bind the custom function to a key sequence add the following line to the ``.emacs`` file.

::

 (global-set-key [f5] 'doodlebug)

This expression will bind the function ``doodlebug`` to the *F5* function key. Once you have re-evaluated the ``.emacs`` buffer you will be able to fire the function with the *F5* key.

We can identify which function is bound to which key with the command:

::

 (lookup-key (current-global-map) [f5])

The rules for binding keys are a bit complex. We can use the operator ``kbd`` to generate the appropriate input to ``global-set-key`` and ``lookup-key``, for instance:

::

 (global-set-key (kbd "C-c a") 'doodlebug)
 (lookup-key (current-global-map) (kbd "C-c a"))

The expression ``(kbd "C-c a")`` generates the appropriate keymap for the key sequence *[C-c][a]*.

---------------------
What You Have Learned
---------------------

You have learned:

* a way to load a new function into emacs
* how to make the function take interactive paramaters
* how to invoke that command - via the command line and via a custom key

------------------
Additional Reading
------------------

There is a good discussion of keybindings in your ``.emacs`` file in the Emacs Lisp Introduction.

The whole process of binding keys to functions in emacs is quite complex and is covered in the `Keymaps`_ section of the manual

----------------
Extra Activities
----------------

What happens if you try and run a function which doesn't include the expression ``(interactive)``?

Experiment with other Interactive Codes in your functions.

Bind and unbind some keys to functions in your ``.emacs`` file.

.. _Interactive Codes: http://www.gnu.org/software/emacs/elisp/html_node/Interactive-Codes.html#Interactive-Codes

.. _Key Bindings: http://www.gnu.org/software/emacs/emacs-lisp-intro/html_node/Keybindings.html#Keybindings

.. _Keymaps: http://www.gnu.org/s/emacs/manual/html_node/elisp/Keymaps.html#Keymaps
