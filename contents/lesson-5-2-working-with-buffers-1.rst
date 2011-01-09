=====================================
Lesson 5-2 - Working With Buffers (1)
=====================================

------------
Introduction
------------

We need to learn how to programme eLisp a bit better, and the best way to do that is to write some programmes that add functionality to Emacs itself.

In this lesson we are going to:
* add a menu to Emacs
* call functions from that menu which operate on the current buffer

To do that we will create a file of eLisp which will:

* define some functions
* add an Emacs menu bound to those functions

We will then edit the `.emacs` file to load our eLisp file at start up.

------------------------
Preparing Our eLisp File
------------------------

Create a new file called ``omarmenu.el`` in the directory ``~/.emacs.d/omars-dir/`` and type the following code in:

| ``(defun omar-count ()``
|   ``(interactive)``
|   ``(message "When we have finished this will count the number of words in the current buffer"))``
| ``(defvar menu-bar-omar-menu (make-sparse-keymap "Omar"))``
| ``(define-key-after global-map [menu-bar omar]``
|   ``(cons "Omar's Menu" (make-sparse-keymap "Omar")))``
| ``(define-key global-map [menu-bar omar omar-count]``
|   ``'(menu-item "Count" omar-count``
| 	      ``:help "Will eventually count words in the current buffer!"))``
| ``(global-set-key (kbd "C-c a") 'omar-count)``
| ``(provide 'omarmenu)``


Then open your ``.emacs`` file in your home directory add the following lines - You might want to delete everything that is in it first:

| ``(add-to-list 'load-path "~/.emacs.d/omars-dir")``
| ``(require 'omarmenu)``

All we have done is create an empty function (it prints *When we have finished this will count the number of words in the current buffer* into the modeline).

We have then created a menu called *Omar's Menu* with one item *Count*. We have then bound *Count* to the approved user key-shortcut *[C]-c a*.

Finally ``omarmenu.el`` announes to the world that it provied ``omarmenu``.

We have then edited the ``.emacs`` file telling it to look for eLisp programmes in the directory ``~/.emacs.d/omars-dir/`` and asking it to load the functionality of ``omarmenu``.

If you have been editing these files (or any files) in Emacs then close it and reopen it.

Emacs should load its ``.emacs`` file and add a menu item to the menubar.

Click on the menu-item *Count* and the message should print in the modeline.

What we will do in this and subsequent lessons is fill in the *empty function* *Count* until it can count the words in the current buffer.

----------------------
Examining Our Function
----------------------

We are going to use a lot of Emacs functions to write our function `omar-count` so we need to learn how to look up their documentation.

Let's start by examining our own function. We will use the built-in Emacs function `describe-function`. It can be called in the usual way:

*[M]-x* `describe-function` and then enter `omar-count` into the modeline. You should see something like this:

.. image :: /images/emacs-using-describe-function.png

Lets add a proper function definition for our function. Edit `omarmenu.el`:

| ``(defun omar-count ()``
|   ``(interactive)``
|   ``"This function will count the number of words in the current buffer"``
|   ``(message "When we have finished this will count the number of words in the current buffer"))``

To see this help string in action you will need to either select the menu item *Emacs-Lisp -> Evaluate Buffer* or close and re-open emacs.

---------------------
What You Have Learned
---------------------

------------------
Additional Reading
------------------

----------------
Extra Activities
----------------


