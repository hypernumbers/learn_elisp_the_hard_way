========================
Lesson 4-3 - Emacs Menus
========================

**Prerequisite:** this lesson presumes you know how to use the ``.emacs`` file as outlined in Lessons 4-1 and 4-2.

------------
Introduction
------------

This section will look at creating a new menu in Emacs and binding a custom function to it. Before doing that we need to create a couple of functions in our ``.emacs`` file to bind to the menu.

We will incorporate our best practice naming conventions in it.

::

 (defun omar-hip ()
   "a nonce menu function"
   (interactive)
   (message "hip, hop, don't stop"))

 (defun omar-hotel ()
  "another nonce menu function"
  (interactive)
  (message "hotel, motel, holiday inn"))

-------------------
The Basics Of Menus
-------------------

We are going to create a menu called ``Omar`` which calls these two functions.

Type the following into your ``.emacs`` file and re-evaluate the buffer.

::

 (define-key global-map [menu-bar omar]
   (cons "Omar's Menu" (make-sparse-keymap "Omar")))

You will see that this has created a new top-level menu at the left of the menu bar. It consists of the words *Omar's Menu*. There are no items below it.

Lets look at that expression - it is defining a new key in the ``global-map``. The global map is a data structure which holds details of all key inputs:

* menu items
* toolbar items
* key shortcuts
* etc, etc

You can look at the value of the global keymap by evaluating the expression ``(current-global-map)`` in the \*scratch\* buffer.

The next parameter is the array ``[menu-bar omar]`` which tells the global keymap that this new key is under the menu. The final item is a parameter list - in this cause just jusing a normal string as the key. The function ``make-sparse-keymap`` creates an empty keymap - we will fill this keymap with the menu items later.

You should be quite confused by the terminology now. We are creating *menus* and all the functions refer to *keys*. Emacs has a mechanism for handling keyboard events. All the other user input mechanisms (mouse events, menus, toolbar buttons, etc, etc) are all extensions of key-handling mechanisms. Hence the fact that all these things are configured by *key* related functions.

The menu we have just created is in the wrong place really. The standard Emacs menus are:

* *File*
* *Edit*
* *Options*
* *Buffers*
* *Tools*

These constitute the *global* menu bar. In addition there is the *Help* menu - this is the *final items* menu. The Emacs convention is that user or mode-specific menus appear in the middle - that is to say to the right of the global menus and to the
left of the final items menu.

We can make our menu do that by changing the definition from ``define-key`` to ``define-key-after``.

Now lets make a proper menu. Type the following into your ``.emacs`` file and re-evaluate the buffer:

::

 (define-key-after global-map [menu-bar omar]
   (cons "Omar's Menu" (make-sparse-keymap "Omar")))
 (define-key global-map [menu-bar omar omar-hip]
   '(menu-item "Hip" omar-hip
 	      :help "Hip, yeah!"))
 (define-key global-map [menu-bar omar separator-replace-tags]
   '(menu-item "--"))
 (define-key global-map [menu-bar omar omar-hotel]
   '(menu-item "Hotel" omar-hotel
      	      :help "Hotel, yeah!"))

Notice how we are adding menu-items down the array ``[menu-bar omar omar-hip]`` and so on and so forth.

------------------------------------
Adding New Items To An Existing Menu
------------------------------------

Lets bind the two nonce functions to an existing menu. Clear out the menu definition code from your ``.emacs`` file and replace it with this:

::

 (defvar menu-bar-omar-menu (make-sparse-keymap "Omar's Menu"))
 (define-key menu-bar-omar-menu [omar-hip]
   '(menu-item "Hip" omar-hip
 	      :help "Hip, yeah!"))
 (define-key menu-bar-omar-menu [separator-omar-1]
   '(menu-item "--"))
 (define-key menu-bar-omar-menu [omar-hotel]
   '(menu-item "Hotel" omar-hotel
      	      :help "Hotel, yeah!"))
 (define-key menu-bar-edit-menu [omar]
        (list 'menu-item "Omar Menu" menu-bar-omar-menu))

Lets step through it line by line. The first line defines a new variable ``menu-bar-omar-menu``. Note that it has a conventional name. It is part of the *menu* system so it has the prefix ``menu-bar-``. The value of this variable is set to a *sparse keymap*. The entire input management system is built around datatypes called *keymaps*. A *sparse* keymap is just an empty uninitialised one.

The next three lines add elements to the sparse keymap. The first and third items are normal menu items, the second is a separator.

The ``define-key`` operator defines a key:

* the first parameter it takes is the keymap to which the key is added
* the second is an array with the function name the menu item is bound to
* the third item is the value that the ``menu-item`` operator returns (which is why the third expression is quoted)

The ``menu-item`` expression takes 3 parameters:

* the string that appears in the menu
* the function that is associated with the menu
* the final parameter is a property list (ie 2 elements) containing the constant variable ``:help`` and the help string which appears as the tooltip on the menu

Notice how we built this menu in a different way - creating a new keymap, adding elements into it, and finally sticking the new keymap into a keymap ``menu-bar-edit-menu`` which is already bound into the global-map.

------------------
Keyboard Shortcuts
------------------

Keyboard shortcuts are automatically added to menus if they exist. To try this out bind one of the functions to a key combination. Add a key binding to ``.emacs`` and reevaluate the buffer.

::

 (global-set-key [f5] 'omar-hip)

When you look at the menu now you should see the keyboard shortcut ``<f5>`` alongside the menu item *Hip*.

---------------------
What You Have Learned
---------------------

You have seen how to add basic menu items which bind to functions.

------------------
Additional Reading
------------------

There is a section on `Keymaps`_ in the *Introduction To Emacs Lisp* Manual - it includes a section on menu manipulation.

----------------
Extra Activities
----------------

You can alter the layout of your menus with a variety of `Menu Separators`_ create a new menu with some swanky separators.

We have build menus with single items - can you build sub-menus and sub-sub-menus?

.. _Keymaps: http://www.gnu.org/software/emacs/emacs-lisp-intro/elisp/Keymaps.html#Keymaps

.. _Menu Separators: http://www.gnu.org/software/emacs/elisp/html_node/Menu-Separators.html#Menu-Separators
