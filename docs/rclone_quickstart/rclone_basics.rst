Rclone Basics
========================

Rclone is a basic utility that allows to mount a cloud storage

Useful links
============
- install Rclone from zip: https://rclone.org/install/
- Rclone tutorial: https://korben.info/rclone-rsync-cloud-dropbox-amazon-s3-google-drive-hubic-backblaze-etc.html

Installation
============

Update the package

.. code-block:: bash

   sudo apt-get update

Install fuse3:

.. code-block:: bash

   sudo apt-get install fuse3

Install Rclone

.. code-block:: bash

   sudo apt-get install rclone

Manual Installation
===================

Oracle Cloud Infrastructure has a linux that is an old package for rclone

Fetch and unpack

.. code-block:: bash
   
   curl -O https://downloads.rclone.org/rclone-current-linux-amd64.zip
   unzip rclone-current-linux-amd64.zip
   cd rclone-*-linux-amd64

Copy binary file

.. code-block:: bash

   sudo cp rclone /usr/bin/
   sudo chown root:root /usr/bin/rclone
   sudo chmod 755 /usr/bin/rclone

Install manpage

.. code-block:: bash
   
   sudo mkdir -p /usr/local/share/man/man1
   sudo cp rclone.1 /usr/local/share/man/man1/
   sudo mandb

Run rclone config to setup. See rclone config docs for more details.

.. code-block:: bash

   rclone config

Essential commands
==================
Config a new cloud remote:

.. code-block:: bash

   rclone config

List the remotes

.. code-block:: bash

   rclone listremotes

Mount a drive (Uptobox)
=======================

Start with:

.. code-block:: bash

   rclone config

This will guide you through an interactive setup process. 
First, Rclone will search for a list of available remotes (i.e. Cloud providers).

To create a new remote, simply type "n" and hit ENTER. Then type the name of the remote. Here, I am going to name it as "mygdrive".

.. code-block:: bash

   2022/01/19 16:13:42 NOTICE: Config file "/home/ostechnix/.config/rclone/rclone.conf" not found - using defaults
   No remotes found - make a new one
   n) New remote
   s) Set configuration password
   q) Quit config
   n/s/q> n
   name> mygdrive    

A list of supported cloud providers will be displayed. 
Choose the cloud provider of your choice. 
In our case. it is Uptobox, so I entered number 39.

.. code-block:: bash

   Option Storage.
   Type of storage to configure.
   Enter a string value. Press Enter for the default ("").
   Choose a number from below, or type in your own value.
   1 / 1Fichier
      \ "fichier"
   2 / Alias for an existing remote
      \ "alias"
   3 / Amazon Drive
      \ "amazon cloud drive"
   ...
   39 / Uptobox
   \ "uptobox"

   Storage> 39

Enter your Upbtobox client ID by going to your account: https://uptobox.fr/my_account


Finally, mount the drive using:

.. code-block:: bash

   rclone mount --vfs-cache-mode writes --allow-non-empty --vfs-read-ahead=32M --buffer-size=64M Uptobox: ~/uptobox

Useful links due to errors:

- https://github.com/rclone/rclone/issues/6844
- https://forum.rclone.org/t/fatal-error-failed-to-mount-fuse/22119
- https://forum.rclone.org/t/montage-uptobox-does-not-update-new-content/28829

Unmount Drive
=============

To unmount a drive, just type in your console:

.. code-block:: bash

   fusermount -u ~/uptobox