======================
Lesson 9 - Emacs Menus
======================

------------
Introduction
------------

This section will look at creating a new menu in Emacs and binding a custom function to it. Before doing that we need to create a couple of functions in our ``.emacs`` file to bind to the menu.

We will incorporate our best practice naming conventions in it.

| ``(defun omar-hip ()``
|   ``"a nonce menu function"``
|   ``(interactive)``
|   ``(message "hip, hop, don't stop"))``

| ``(defun omar-hotel ()``
|  ``"another nonce menu function"``
|  ``(interactive)``
|  ``(message "hotel, motel, holiday inn"))``

-------------------
The Basics Of Menus
-------------------

We are going to create a menu called ``Omar`` which calls these two functions.

''

------------------------------------
Adding New Items To An Existing Menu
------------------------------------

Lets bind the two nonce functions to an existing menu. Clear out the menu definition code from your ``.emacs`` file and replace it with this:

| ``(defvar menu-bar-omar-menu (make-sparse-keymap "Omar's Menu"))``
| ``(define-key menu-bar-omar-menu [omar-hip]``
|   ``'(menu-item "Hip" omar-hip``
| 	      ``:help "Hip, yeah!"))``
| ``(define-key menu-bar-omar-menu [separator-omar-1]``
|   ``'(menu-item "--"))``
| ``(define-key menu-bar-omar-menu [omar-hotel]``
|   ``'(menu-item "Hotel" omar-hotel``
|      	      ``:help "Hotel, yeah!"))``
| ``(define-key menu-bar-edit-menu [omar]``
|        ``(list 'menu-item "Omar Menu" menu-bar-omar-menu))``

Lets step through it line by line. The first line defines a new variable ``menu-bar-omar-menu``. Note that it has a conventional name. It is part of the *menu* system so it has the prefix ``menu-bar-``. The value of this variable is set to a *sparse keymap*. The entire input management system is built around datatypes called *keymaps*. A *sparse* keymap is just an empty unitialised one.

The next three lines add elements to the sparse keymap. The first and third items are normal menu items, the second is a separator.

The ``define-key`` operator defines a key:

* the first parameter it takes is the keymap to which the key is added
* the second is an array with the function name the menu item is bound to
* the third item is the value that the ``menu-item`` operator returns (which is why the third expression is quoted)

The ``menu-item`` expression takes 4 parameters:

* the string that appears in the menu
* the menu item **(again?)**
* some help thing **?**
* the help string

---------------------
What You Have Learned
---------------------

------------------
Additional Reading
------------------

----------------
Extra Activities
----------------


