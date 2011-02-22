=========================
Emacs And The .emacs File
=========================

------------
Introduction
------------

We will be using the `.emacs` file a lot to get our functionality into Emacs. Emacs itself also uses the `.emacs` file. Let's see how it uses it.

--------------
Saving Options
--------------

Emacs saves some of your options in the `.emacs` file. Let's change some options, save them and then see how they appear.

Start by clearing the `.emacs` file - open it in an editor, delete all the contents and save it. (You might want to copy it elsewhere if it has stuff in it you really care about).

If you edited it in Emacs you will need to close Emacs and reopen it to 'lose' all your old configuration - if you edited it in an other editor, simply open Emacs.

We are going to do some simple changes to our default fonts and then save them.

Use the menu item *Options -> Set Default Fonts...* and you will get the standard font dialog box:

.. image :: /images/emacs-font-dialog-box.png

Choose a different font, size, weight etc etc. Your open buffers will redraw with the new fonts.

Now save the options with the menu item *Options -> Save Options*.

Notice that the modeline now says something like `Wrote /home/gordonguthrie/.emacs` - obviously it will have your name in it and not mine.

Now open the `.emacs` file. Mine looks like:

::

 (custom-set-variables
   ;; custom-set-variables was added by Custom.
   ;; If you edit it by hand, you could mess it up, so be careful.
   ;; Your init file should contain only one such instance.
   ;; If there is more than one, they won't work right.
  )
 (custom-set-faces
   ;; custom-set-faces was added by Custom.
   ;; If you edit it by hand, you could mess it up, so be careful.
   ;; Your init file should contain only one such instance.
   ;; If there is more than one, they won't work right.
  '(default ((t (:inherit nil :stipple nil :background "white" :foreground "black" :inverse-video nil :box nil :strike-through nil :overline nil :underline nil :slant normal :weight normal :height 143 :width normal :foundry "bitstream" :family "Courier 10 Pitch")))))

Emacs has *saved options* into the `.emacs` file. Emacs marks the code that it adds with quotes as above. If you see big chunks of code like this in your `.emacs` file - that's what it is. Don't panic.

---------------------
What You Have Learned
---------------------

You have learned not to worry about finding strange code in your `.emacs` file.

----------------
Extra Activities
----------------

You can really customise Emacs with the menu item *Options -> Customise Emacs - > Browse Customization Groups*.

This should open up a page that looks like this:

.. image :: /images/emacs-customization-groups.png

Have a play with the various options and see what happens to your `.emacs` file when you save them.
