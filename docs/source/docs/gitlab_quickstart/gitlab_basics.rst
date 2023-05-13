Gitlab Basics
=========================

Clone your first gitlab repository
----------------------------------
The very first Git repository we will clone is the one of the knowledge center your are
reading (what a "Mise en abyme" !)

Let's duplicate the Gitlab group structure in your Linux VM::

   hiya@12BANEHIYAT470:~$ cd; mkdir -p g/{knowledge,infra,2022,2023,mz}
   hiya@12BANEHIYAT470:~$ tree
   .
   └── g
       ├── 2022
       ├── infra
       ├── knowledge
       └── mz
   hiya@12BANEHIYAT470:~$

Go to https://code.mazars.global/knowledge/knowledge_data_advisory and copy the *clone
ssh* URL:

.. image:: /docs/gitlab_quickstart/gitlab_basics/gitlab_clone_ssh_link.png
   :width: 430px

Back to your terminal use ``git`` to clone it.::

   hiya@12BANEHIYAT470:~$ cd g/knowledge
   hiya@12BANEHIYAT470:~/g/knowledge$ git clone git@code.mazars.global:knowledge/knowledge_data_advisory.git
   ...
   hiya@12BANEHIYAT470:~/g/knowledge$
   hiya@12BANEHIYAT470:~/g/knowledge$ ls
   knowledge_data_advisory
   hiya@12BANEHIYAT470:~/g/knowledge$

Compile Sphinx documentation
------------------------------------
.. note::

  The https://knowledge.mazars.global documentation is written in ``.rst`` files, a
  markup language. To compile the documentation means to use sphinx compiler to convert
  this ``.rst`` files in HTML pages you can then read from your own laptop with the Edge
  or Firefox Windows browser.

let's go to the ``knowledge_data_advisory`` repository::

   hiya@12BANEHIYAT470:~/g/knowledge$ cd knowledge_data_advisory

.. tab:: manual (doc) venv activation

   In case you did not made the :ref:`Automate venv activation` you can have to activate
   manualy the ``(doc)`` virtualenv::

      hiya@12BANEHIYAT470:~/g/knowledge$ cd knowledge_data_advisory
      hiya@12BANEHIYAT470:~/g/knowledge/knowledge_data_advisory$ pyenv activate doc
      (doc) hiya@12BANEHIYAT470:~/g/knowledge/knowledge_data_advisory$

.. tab:: auto (doc) venv activation

   In case you made the :ref:`Automate venv activation` you can notice that the ``(doc)``
   virtualenv has been automaticaly activated.

   .. code::

      hiya@12BANEHIYAT470:~/g/knowledge$ cd knowledge_data_advisory
      (doc) hiya@12BANEHIYAT470:~/g/knowledge/knowledge_data_advisory$


---

Now that the ``(doc)`` virtualenv is activated we can install the Sphinx in it with
``pip install -r requirements.txt``::

   (doc) hiya@12BANEHIYAT470:~/g/knowledge/knowledge_data_advisory$ pip install -r requirements.txt
   ...
   (doc) hiya@12BANEHIYAT470:~/g/knowledge/knowledge_data_advisory$

And build the HTML documentation with ``make html``::

   (doc) hiya@12BANEHIYAT470:~/g/knowledge/knowledge_data_advisory$ make html
   ...
   build succeeded.

   The HTML pages are in _build/html.
   (doc) hiya@12BANEHIYAT470:~/g/knowledge/knowledge_data_advisory$

As the output said, the HTML has been done in the ``_build/html`` folder.

The good news is that we can access Linux files from the Windows host. For that let's
enter in the **Windows File Explorer** this ``\\wsl$`` this will provide Network connexion
inside the our Linux files.

So from Windows let's run the Windows File Explorer and navigate to
``/home/<>/g/knowledge/knowledge_data_advisory/_build/html/index.html``

To learn the restructuredtext aka **rst** syntax to document our projects is easy, you
will learn that in this dedicated training to `sphinx
<https://knowledge.mazars.global/infra_mzskeleton/src/sphinx_tutorial/sphinx_syntax_tutorial.html>`__.

.. admonition:: transition to Git

   Soon you will be able to improve/modify this documentation editing files with
   ``vim``, compiling with a ``make html`` and refreshing the WEB browser you will see
   the result.

   But before to do that you need to learn to use Git our Distributed Version Control
   Systems (DVCS).