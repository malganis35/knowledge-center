Python Setup
=========================

Setup Python with ``pyenv``
------------------------------
Installing python 3 and utils:

.. code:: bash

    sudo apt-get update  # to update the local DB with the available remote ubuntu software
    sudo apt-get install python3-pip python-is-python3 make build-essential python3-venv
    sudo apt-get install unzip zip tree gdu git tig terminator htop

Download and Install Pyenv

.. code:: bash

    curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash

Add the following lines of code to your ``.bashrc`` this will change dynamically your
Python virtualenv just by moving to the right folder.

.. code:: bash

    $ tail -4 ~/.bashrc
    export PYENV_ROOT="$HOME/.pyenv"
    command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"
    eval "$(pyenv init -)"
    eval "$(pyenv virtualenv-init -)"
    $

source ``~/.bashrc`` to make it effective immediately. 

.. code:: bash

    $ source .bashrc

At this time the only Python available is the one provided by Ubuntu (called ``system`` by pyenv)

.. code:: bash

    caotrido@12BANEHIYAT470:~$ pyenv  versions
    * system (set by /home/caotrido/.pyenv/version)
    caotrido@12BANEHIYAT470:~$

Create a ``doc`` virtualenv based on the system Python.

.. code:: bash

    caotrido@12BANEHIYAT470:~$ pyenv virtualenv system doc

You can now temporary define your ``doc`` virtualenv with:

.. code:: bash

   caotrido@12BANEHIYAT470:~$ pyenv activate doc
   (doc) caotrido@12BANEHIYAT470:~$

.. _Automate venv activation:

Automate virtualenv activation
------------------------------

Now with ``pyenv local doc`` on a specific folder, just going to this folder will automaticaly activate the ``doc`` virtualenv :

.. code:: bash

   caotrido@12BANEHIYAT470:~$ pyenv local doc
   (doc) caotrido@12BANEHIYAT470:~$

.. note::
   This work creating a ``.python-version`` file on the folder with the virtualenv name
   in it.