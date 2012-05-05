==========================
Why Did I Write This Book?
==========================

----------
Why Elisp?
----------

I am writing this book to learn Elisp myself. I use Emacs every day because it is the IDE of choice for Erlang and I am an Erlang programmer.

My relationship with Emacs is that of Simson Garfinkel, Daniel Weise and Steven Strassmann to `Unix`_ - I genuinely loathe it.

Emacs is the most prominent piece of software in the *apostolic* tradition. You are supposed to learn it by being instructed by someone who learnt it by being instructed by someone recursively all the way back to the original authors in a continuous apostolic succession.

I would fain be the John Knox, the Calvin, the Luther, and hell mend them.

By writing this book I hope to be able to write Elisp to configure and extend Emacs in my working environment.

-----------------------
Why Choose This Format?
-----------------------

I have chosen to use a format based on *Learn X The Hard Way*. That format is specifically aimed at writing books for non-programmers. My target audience is programmers with no functional programming experiences. Funtional Programming Languages in general (and Lisp in particular) are far enough from Object Orientated or Procedural languages that learning them is like starting to programme again - so the *beginners* format is quite appropriate.

I have not called the book *Learn Elisp The Hard Way* because this slightly hybrid formula would confuse that core brand.

I occasionally have to dip into Elisp in the form of .emacs files which are executed on startup and are how you configure Emacs to do specific stuff for your particular requirements.

One of the reasons why the *Learn X The Hard Way* books work is that the format of forcing people to type in code is a great way to teach them how to read the syntax. Elisp still looks like line noise to me and I have been programming since the late 70s in languages as diverse as Fortran, VB, C++, Java, Perl, Python, PHP, Ruby and Erlang. Writing this book has been a good way to learn how to *read* Elisp for me, and I hope it will work for the readers.

The transition from Fortran to the Obect Orientated paradigm of C++ was enormously painful. The shift from the OO paradigm (Ruby was my language *de jour* then) to functional programming in the form of Erlang was also horrendous.

I may be wrong, but I think that many experienced programmers who have no previous exposure to functional programming would benefit from a pretty brutal beginners style book about Elisp.

I have copies of `On Lisp`_ by Paul Graham and `Common Lisp A Gentle Introduction To Symbolic Computing`_ but have never been able to learn Lisp because of the very basic problem that Zed Shaw identified in `his article`_ on *How To Write A LxTHW* - I could never work out how to get to a basic working shell to type the code examples into. It's not that I didn't try, its just that after a summer of trying to start learning Lisp I had gotten nowhere. If you think that that's my fault, then it falls to you to explain how I managed to learn a bazillion other languages successfully.

The other appealing part of this format is that it isn't a reference book. To make clear just how unsuited I am to write a reference book about Lisp, let me enumerate ATTIDNK (All The Things I Do Not Know):

* the difference between Emacs and XEmacs
* the difference between Elisp and Lisp
* how Common Lisp is related to Clojure or any other Lisp
* how Lisp does package management
* pretty much everything else I would need to know to write a reference book

----------------------------------
On Learning Functional Programming
----------------------------------

If you just want to learn **a functional programming language** you really should learn Erlang and I recommend `Joe's book`_ or `Franceso and Simon's one`_.

-------------------
Big Up For Zed Shaw
-------------------

Zed Shaw? `Who?`_ `Why?`_

.. _Unix: http://www.amazon.com/UNIX-Haters-Handbook-Daniel-Weise/dp/1568842031/ref=sr_1_1?ie=UTF8&s=books&qid=1290297419&sr=1-1
.. _On Lisp: http://www.amazon.com/LISP-Advanced-Techniques-Common/dp/0130305529/ref=sr_1_1?ie=UTF8&qid=1290295941&sr=8-1
.. _Common Lisp A Gentle Introduction To Symbolic Computing: http://www.amazon.com/Common-Lisp-Introduction-Symbolic-Computation/dp/0805304924/ref=sr_1_8?s=books&ie=UTF8&qid=1290296197&sr=1-8
.. _his article: http://sheddingbikes.com/posts/1288945508.html
.. _Joe's book: http://www.amazon.com/Programming-Erlang-Software-Concurrent-World/dp/193435600X/ref=sr_1_2?s=books&ie=UTF8&qid=1290296292&sr=1-2
.. _Franceso and Simon's one: http://www.amazon.com/ERLANG-Programming-Francesco-Cesarini/dp/0596518188/ref=sr_1_1?s=books&ie=UTF8&qid=1290296292&sr=1-1
.. _Who? : http://www.zedshaw.com/
.. _Why? : http://sheddingbikes.com/posts/1288945508.html
