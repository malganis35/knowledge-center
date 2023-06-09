GIT & SSH Setup
=========================

Install Git
-------------------------
If you want to install the basic Git tools on Linux via a binary installer, you can generally do so through the package management tool that comes with your distribution. 

As usual, first start with an update of your package

.. code:: bash

  $ sudo apt get update

Then, install git from the command line

.. code:: bash

  $ sudo apt install git-all



Install Gitui
-------------------------
Based on the article: https://korben.info/gitui.html

In general, the inconvenient of graphical interface are: 

1/ they are not in the terminal ; 

2/ they slow down your user experience.

If you start with git and do not know all the good git command, you can test and use GitUI.

.. image:: /docs/setup_your_pc/git_setup/gitui_demo.gif
   :width: 600px

It is an interface for Git that you can pilot with your keyboard and that works with the terminal.
It is portable, fast, free and open source.
Compared to other packages, it is faster and takes less memory.

.. image:: /docs/setup_your_pc/git_setup/gitui_benchmark.png
   :width: 600px

To install GitUI

.. code:: bash

  curl -s curl -s https://api.github.com/repos/extrawurst/gitui/releases/latest | grep -wo "https.*linux.*gz" | wget -qi -
  tar xzvf gitui-linux-musl.tar.gz
  rm gitui-linux-musl.tar.gz
  sudo chmod +x gitui
  sudo mv gitui /usr/local/bin
  gitui

Setup your SSH keys
-------------------------
Configure ``ssh`` and your keys:

.. warning::

    - Use as SSH keys the one provided by the DevOps team (ask Kajan).
    - They will provide you with a zip file e.g. ``hiya.banerjee@mazars.fr.zip`` with
      both your public and private key, copy them in your Windows Documents folder.

      Please save the zip file in your Windows Documents folder. 

.. note::

  We can access the Windows filesystem from the Linux VM::

    hiya@12BANEHIYAT470:~$ df -h /mnt/c
    Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
    C:\                376G     62G  315G  17% /mnt/c
    hiya@12BANEHIYAT470:~$

Unzip the zip file in an ``.ssh`` folder directly from the ``.ssh`` folder, (example
below with Hiya's account):

.. code:: bash

    hiya@12BANEHIYAT470:~$ cd
    hiya@12BANEHIYAT470:~$ mkdir .ssh
    hiya@12BANEHIYAT470:~$ cd .ssh
    hiya@12BANEHIYAT470:~/.ssh$ unzip /mnt/c/Users/hiya.banerjee/Documents/hiya.banerjee@mazars.fr.zip
    Archive:  /mnt/c/Users/hiya.banerjee/Documents/hiya.banerjee@mazars.fr.zip
      inflating: hiya.banerjee@mazars.fr
      inflating: hiya.banerjee@mazars.fr.pub
    hiya@12BANEHIYAT470:~/.ssh$ rm
    /mnt/c/Users/hiya.banerjee/Documents/hiya.banerjee@mazars.fr.zip
    hiya@12BANEHIYAT470:~/.ssh$

Now both public and private keys are on your ``~/.ssh`` folder.

Add a symlink to the default ssh filename ``id_rsa`` to inform SSH about your default
account:

.. code:: bash

    hiya@12BANEHIYAT470:~$ ln -s ~/.ssh/hiya.banerjee@mazars.fr ~/.ssh/id_rsa
    hiya@12BANEHIYAT470:~$

To inform ``ssh`` about the Mazars gitlab, create an ``ssh/config`` file with the following:

.. code:: bash

  hiya@12BANEHIYAT470:~$ cat .ssh/config
    AddKeysToAgent yes

    host *
      ForwardAgent yes
      GSSAPIAuthentication no
      ServerAliveInterval 15

    host code.mazars.global
      Hostname 52.169.52.102
  hiya@12BANEHIYAT470:~$

Tips & Tricks on SSH Agent
------------------------------

Based on: https://kb.iu.edu/d/aeww

To avoid typing each time you push or fetch from Gitlab, you can use a SSH Agent.

In Unix, **ssh-agent** is a background program that handles passwords for SSH private keys. 
The **ssh-add** command prompts the user for a private key password and adds it to the list maintained by **ssh-agent**.
Once you add a password to **ssh-agent**, you will not be prompted for it when using SSH or 
scp to connect to hosts with your public key.

The public part of the key loaded into the agent must be put on the target system in ``~/.ssh/authorized_keys``; 
see Set up SSH public key authentication to connect to a remote system.

To use **ssh-agent** and **ssh-add**, follow the steps below:

1. At the Unix prompt, enter: 

.. code:: bash

  caotrido@12BANEHIYAT470:~$ eval `ssh-agent`

Make sure you use the backquote (`), located under the tilde (~), rather than the single quote (')

2. Enter the command: 

.. code:: bash

  caotrido@12BANEHIYAT470:~$ ssh-add .ssh/cao-tri.do@mazars.fr

Solving SSH issues
------------------------------

Based on: https://stackoverflow.com/questions/9270734/ssh-permissions-are-too-open

If you get an error like:

.. code:: bash

  Permissions 0777 for '/Users/username/.ssh/id_rsa' are too open.
  It is recommended that your private key files are NOT accessible by others.
  This private key will be ignored.

Then you need to change the permission of your private SSH key

.. code:: bash

  chmod 600 ~/.ssh/id_rsa

and also for your public SSH key

.. code:: bash

  chmod 600 ~/.ssh/id_rsa.pub