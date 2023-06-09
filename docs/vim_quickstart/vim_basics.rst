Vim Basics
=========================

Learn minimal vim
-------------------------
We will have to write in files from the terminal, we need an editor, **Vim** is our main
editor, you will learn to use it like Code Ninjas.

In theses days of Virtualisation, DevOps, Cloud, tricky network, we cannot afford to
have to install an editor on the each of the dozens of Virtual Machines that are involved in our
daily work.

- Vim is *modal*: you get specialized modes each one has a full keyboard and a dedicated
  grammar for maximum effic

- Vim is *composable*: you get dozens of small, basic, commands that you combine into
  natural language-like "sentences".  There is very little difference between what you
  think and what you actually tell Vim to do.

- Vim is *always available*: any Linux/BSD/MacOS machine has it. Vim has a small
  footprint (can manipulate bigData files), low latency, fast startup, allows for more
  screen space, is customizable and most importantly, once the muscle-memory has been
  ingrained, it’s nearly impossible to switch to something else.

.. admonition:: vim 101

   The basic knowledge to close this part and start using vim would be to know how to:

   - open a file with vim:

     - ``$ vim my_file.txt``

   - close the file: ``:q``, save the file: ``:w``, save and close: ``:wq``
   - write some text: first you have to type ``i`` to enter in *insert* mode, then you
     can write ``some texte`` then you hit the escape key ``Esc`` to come back to the normal
     mode.


Let's take 30 minutes to learn how to use ``vim``, just practice the integrated training
``vimtutor``::

  caotrido@12BANEHIYAT470:~$ vimtutor
  ...

  ===============================================================================
  =    W e l c o m e   t o   t h e   V I M   T u t o r    -    Version 1.7      =
  ===============================================================================
  ...
                         Lesson 1.1:  MOVING THE CURSOR

     ** To move the cursor, press the h,j,k,l keys as indicated. **
               ^
               k              Hint:  The h key is at the left and moves left.
         < h       l >               The l key is at the right and moves right.
               j                     The j key looks like a down arrow.


This is more than enough to end this session.