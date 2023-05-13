GIT Setup
=========================

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
