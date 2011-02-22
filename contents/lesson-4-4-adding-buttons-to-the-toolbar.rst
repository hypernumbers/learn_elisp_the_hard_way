===========================================
Lesson 4-4 - Adding Buttons To The Tool-bar
===========================================

**Prerequisite:** this lesson presumes you know how to use the ``.emacs`` file as outlined in Lessons 4-1 and 4-2.

------------
Introduction
------------

Adding buttons to the tool-bar is conceptually similar to adding menu items - binding in a 'non-key' keymap to the ``global=map``.

Before you do it you will need to create a new button image. Emacs buttons are stored in the directory ``usr/share/emacs/23.1/etc/images/``. Copy one out to a directory under your home directory. Fire up the Gimp, edit the image and resave it as ``omar.xmp``. Sudo to root and copy the new icon back to ``usr/share/emacs/23.1/etc/images/``.

We will use the functions ``omar-hip`` and ``omar-hotel`` which we defined for the previous lesson.

-------------------------
The Basics Of The Toolbar
-------------------------

Add the following line to your ``.emacs`` file and re-evaluate the buffer:

::

 (define-key global-map [tool-bar omar-button]
 '(menu-item "Hotel" omar-hotel
    :help "OMG Omar!"
    :image (image :type xpm :file "omar.xpm")))

We are binding in a ``menu-item`` onto the tool-bar - the ``menu-item`` has a paired-list with an image description.

---------------------
What You Have Learned
---------------------

You have learned:

* where tool-bar icons are
* how to edit them
* how to bind them in

----------------
Extra Activities
----------------

The tool-bar button we created was added at the start of the tool-bar. How would you add it to the end of the toolbar?
