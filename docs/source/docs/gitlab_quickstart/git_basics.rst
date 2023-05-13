Git Basics
============

Introduction
------------

If you are working on a project over time, you may want to keep track of which changes
were made, by whom, and when those changes were made. This becomes increasingly
important if you end up having a bug in your code! Git can help you with this.

Version control is a system that records changes to a file or set of files over time so
that you can recall specific versions later. See more here `Git -- getting started with
DVCS <https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control>`__

Basic ``git`` workflow
----------------------
Below the basic ``git`` workflow

If you create news files you have to explicitly add them e.g.

.. code:: bash

  $ git add new_file.rst image/image.png
  $ vim new_file.rst    # hack hack hack ...
  $ git status          # to check what files has been involved
  $ git diff            # to check if it's a good hack

  $ git commit -m 'very clear message, the team should have a clear understanding of what this patch is for'
  $ git push            # to send this to gitlab so coleges can get it

Anytime or when we start a new session, the morning, after lunch, colleges could have
pushed some new code on the remote gitlab repository. So we have to fetch the remote
code in case there is something new:

.. code:: bash

  $ git fetch    # you get stuff from gitlab, your last collegue work

In case ``fetch`` retrieve some new code you have to integrate it to your working copy

.. code:: bash

  $ git rebase   # you integrate this new work on your working copy

Now you can start again the above workflows:

.. code:: bash

  $ vim ...             # hack hack hack ...
  $ git diff            # to check if it's a good hack
  $ git commit -m 'clear commit message, ... '

You can use ``tig`` to have and overview on repository commits::

  $ tig

.. image:: /docs/gitlab_quickstart/git_basics/tig_view.png
   :width: 430px

.. admonition:: set name/email on first commit

   On your very first commit ``git`` will return this message::

     hiya@12BANEHIYAT470:~$ git commit -m 'commit msg'
     your gitconfig file is not configured, please check your name an email
     on ~/.gitconfig fix it and come back to your commit.
     hiya@12BANEHIYAT470:~$

   You have to correctly set you name and email in the ``~/.gitconfig`` file::

     hiya@12BANEHIYAT470:~$ vim ~/.gitconfig

.. fixme

Small Git training
------------------
- Create a folder with ``mkdir ~/testgit; cd ~/testgit``
- create a simple ``README.txt`` file in it, add some content with vim.
- ``git init`` will setup the folder as a git repository
- ``git add README.txt`` file and ``git commit -m 'initial commit'``
- iterate 10 times modifying the content of the ``README.txt`` file, creating new files (do
  not foget to ``git add new_files.txt``) adding a commit at each step.
- use ``tig`` to follow the construction.

.. note::

  The above training does not include ``git fetch`` nor ``git rebase``, your
  ``~/testgit`` repository is for now local, we will learn more on Git in a dedicated
  training, let's finish this one first.