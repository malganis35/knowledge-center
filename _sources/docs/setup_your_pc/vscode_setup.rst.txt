=============
VS Code setup
=============


Install VScode for WSL
=============================

Presentation
----------------

.. image:: vscode_setup/vscode.PNG
   :width: 700px
   :align: center

VS Code is a software that can be installed without admin rights.
It offers a large range of useful functionalities to work within Data Services:

- Have an IDE to edit files
- Install extensions to easy you life within the team. For example, writing of Sphinx documentation (RST)
- Execute Jupyter Notebook

.. warning::
   Do not install VS Code within Windows. Everything will be done from your WSL command line



Installing VScode
---------------------

You'll have to install VScode from your WSL command line. 
The command you'll have to execute is the following :

.. code-block:: bash

    sudo snap install --classic code

You can try to open it by using this command to launch VScode.

.. code-block:: bash

   code

Alternatively, you can add this alias to your `.bashrc` file. 
It will allow to open VS Code using the current folder:

.. code-block:: bash

   alias code='code --remote wsl+ubuntu "$(pwd)"'


Installing a plug-in to simplify the writing in sphinx
======================================================

You'll need to go to the plug-in section in VScode, you can open it with CTRL+Maj+X, and then you type "reStructuredText" in the search bar and you install it. 

Procedure to install an extension (example with reStructuredText)

.. tab:: Access to Extension

  Click on the left to the extension (CTRL+Maj+X)

  .. image:: vscode_setup/vscode_extension.PNG
      :width: 600px
      :align: center

.. tab:: Install Extension

  Find the extension in the market place: **reStructuredText** by TatsuyaNakamori

  .. image:: vscode_setup/vscode_restructuredtext.PNG
      :width: 800px
      :align: center


Connect WSL to a remote linux machine
=====================================

If you use a Linux server (for example Oracle Cloud), to setup your WSL:

1. Go into your windows explorer to: ``C:\Users\cao-tri.do\.ssh``
2. Copy your ssh key here
3. Go into the ``config`` file and add this line to your file (change the host, IdentityFile, HostName, User)

.. code-block:: bash

   Host srv002.astraviz.fr
      IdentityFile C:/Users/cao-tri.do/.ssh/ssh-key-2023-08-02.key
      HostName srv002.astraviz.fr
      User ubuntu

4. Go into VS Code 
5. Select: "Connect to Host"
6. Select: "Add new ssh host". Enter the ssh
7. Alternatively, you will be able to open the remote explorer file from VS Code