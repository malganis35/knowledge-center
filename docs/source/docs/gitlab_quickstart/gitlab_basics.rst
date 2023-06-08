Gitlab Basics
=========================

Clone your first gitlab repository
----------------------------------
The very first Git repository we will clone is the one of the knowledge center your are
reading (what a "Mise en abyme" !)

Let's duplicate the Gitlab group structure in your Linux VM (WSL)::

   >> cd; mkdir -p g/{knowledge,infra,2022,2023,mz}
   >> tree
   .
   └── g
       ├── 2022
       ├── infra
       ├── knowledge
       └── mz
   hiya@12BANEHIYAT470:~$

Go to https://gitlab.com/do-favier/knowledge and copy the *clone
ssh* URL:

.. image:: /docs/gitlab_quickstart/gitlab_basics/gitlab_clone_ssh_link.png
   :width: 430px

Back to your terminal use ``git`` to clone it.::

   >> cd g/knowledge
   >> git clone git@code.mazars.global:knowledge/knowledge_data_advisory.git
   >>ls
   knowledge_data_advisory

Compile Sphinx documentation
------------------------------------
.. note::

  The https://knowledge.dofavier.fr/index.html documentation is written in ``.rst`` files, a
  markup language. To compile the documentation means to use sphinx compiler to convert
  this ``.rst`` files in HTML pages you can then read from your own laptop with the Edge
  or Firefox Windows browser.

let's go to the ``knowledge`` repository::

   >> cd knowledge

.. tab:: manual (doc) venv activation

   In case you did not made the :ref:`Automate venv activation` you can have to activate
   manualy the ``(doc)`` virtualenv::

      >> cd knowledge
      >> pyenv activate doc
      >> (doc) user@machine:~/g/knowledge/knowledge$

.. tab:: auto (doc) venv activation

   In case you made the :ref:`Automate venv activation` you can notice that the ``(doc)``
   virtualenv has been automaticaly activated.

   .. code::

      >> cd knowledge
      >> (doc) user@machine:~/g/knowledge/knowledge_data_advisory$


---

Now that the ``(doc)`` virtualenv is activated we can install the Sphinx in it with
``pip install -r requirements.txt``::

   >> (doc) user@machine:~/g/knowledge/knowledge_data_advisory$ pip install -r requirements.txt
   
And build the HTML documentation with ``make html``::

   (doc) user@machine:~/g/knowledge/knowledge_data_advisory$ make html
   build succeeded.

   The HTML pages are in _build/html.

As the output said, the HTML has been done in the ``_build/html`` folder.

The good news is that we can access Linux files from the Windows host. For that let's
enter in the **Windows File Explorer** this ``\\wsl$`` this will provide Network connexion
inside the our Linux files.

So from Windows let's run the Windows File Explorer and navigate to
``/home/<>/g/knowledge/knowledge_data_advisory/_build/html/index.html``

To learn the restructuredtext aka **rst** syntax to document our projects is easy, you
will learn that in this dedicated training to `sphinx
<https://knowledge.dofavier.fr/docs/sphinx_quickstart/index.html>`__.

.. admonition:: Transition to Git

   Soon you will be able to improve/modify this documentation editing files with
   ``vim``, compiling with a ``make html`` and refreshing the WEB browser you will see
   the result.

   But before to do that you need to learn to use Git our Distributed Version Control
   Systems (DVCS).