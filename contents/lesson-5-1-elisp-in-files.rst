===========================
Lesson 5-1 - Elisp In Files
===========================

------------
Introduction
------------

So far we have created emacs functions in the ``.emacs`` file and attached that to menu-bar and the like. This is a bit sub-optimal. To use Elisp properly we should package up functionality into files and make it easy for them to be added to emacs.

Emacs loads files from various libraries. It used a global variable called ``load-path`` to work out where to load them from.

You can look at the current value of that global variable in the \*scratch\* buffer by evaluating (type in the text and type *[Control][j]* at the end):

``load-path``

Your install of emacs will dump out loads of directories:

``("/usr/share/emacs23/site-lisp/thailatex" "/usr/share/emacs23/site-lisp/latex-cjk-thai" "/usr/share/emacs23/site-lisp/latex-cjk-common" "/usr/share/emacs23/site-lisp/dictionaries-common" "/etc/emacs23" "/etc/emacs" "/usr/local/share/emacs/23.1/site-lisp" "/usr/local/share/emacs/site-lisp" "/usr/share/emacs/23.1/site-lisp" "/usr/share/emacs/23.1/site-lisp/dictionaries-common" "/usr/share/emacs/23.1/site-lisp/latex-cjk-common" "/usr/share/emacs/23.1/site-lisp/latex-cjk-thai" ...)``

For a shared production package (ie one that everyone on a particular machine will need access to) the install directory would be somewhere in the shared path space (ie a directory like ``/usr/share/emacs23/site-lisp/``). The convention is that there are ``site-lisp`` directories for all versions of Emacs as well a for specific versions. Upgrades of the base Emacs operator can cause some packages to fail.

For this lesson we will store our Elisp files locally. Conventionally this is done in a directory called ``.emacs.d``. Best practice says that we don't not add ``.emacs.d`` to the ``load-path``, but we can create a sub-directory under that and add it.

Create a subdirectory called ``omars-dir`` in ``~/.emacs.d/`` and inside that create a file called ``myomar.el``.

Add versions of our old favourite functions to ``myomar.el``

| ``(defun omar-hip ()``
|   ``(interactive)``
|   ``(message "hip, hop, don't stop"))``

| ``(defun omar-hotel ()``
|  ``(interactive)``
|  ``(message "hotel, motel, holiday inn"))``

In order to make this available to us we need to add the path to ``load-path``. This is done in our ``.emacs`` file.

``(add-to-list 'load-path "~/.emacs.d/omars-dir")``

Re-evaluate the ``.emacs`` buffer and then switch to the scratch buffer and evaluate ``load-path`` - our directory should now be the first path in the list.

--------------
Using Our File
--------------

We have our new directory in the *load-path* we have our file in that directory. Is that enough?

Quit Emacs and restart (thus losing all our history and defined functions). Our new directory should still be in the *load-path*; but will the code be loaded?

Emacs has an interactive command for executing interactive functions called execute-extended-command. It is bound to the key combination *[M-x]* so simply type that and the focus will switch to the mini-buffer and wait for you to enter the name of the command you want to run. Stick in ``omar-hotel``. Your attempt to run it should fail.

Providing code in a searchable path isn't enough. You need to add a line to the ``.emacs`` file telling it to load our new file, and another line in the file itself to identify what it is that the file is providing.

To make life simpler we are going to call the features that our ``myomar.el`` file provides the same base name as the file, ie ``myomar``.

To get this to autoload we add the following line to our ``.emacs`` file after the line where we have added ``~/.emacs.d/omars-dir/`` to the ``load-path``:

``(require 'myomar)``

and we add this line at the top of ``myomar.el``:

``(provide 'myomar)``

Now if we quite Emacs and restart it and the use the *[M-x]* trick with ``omar-hip`` the function will execute.

-------------------
Our Execution Model
-------------------

This is the execution model we will use from now on:

* create a custom file or files in a standard directory
* edit ``.emacs`` to run an initialisation function

The initialisation function will do a number of things:

* set up the global environment
* change menus, tool-bars and key bindings
* load the code that is needed

Usually this is done conditionally via hooks. The classic route is a *major-mode* which is triggered by editing files with a certain file type. Later on we will create our own major mode for *omar*. When files whose names match ``*.omar`` are loaded a new mode with menus, tool-bar buttons and key bindings will *magically* appear.

On starting Emacs our ``.emacs`` file will bind a variety of functions such that Emacs runs them when a file that matches ``*.omar`` is edited. These functions will load our modules as needed and dynamically customise Emacs.

---------------------
What You Have Learned
---------------------

You have learned:

* the basics of including code
* how Emacs looks for modules
* how to load some custom code into Emacs at startup

------------------
Additional Reading
------------------

There is a slightly more to loading code in Elisp which is described in the `Loading Code`_ section of the Elisp Reference Manual.

.. _Loading Code: http://www.gnu.org/software/emacs/emacs-lisp-intro/elisp/How-Programs-Do-Loading.html#How-Programs-Do-Loading
