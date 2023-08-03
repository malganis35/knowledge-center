============================
R Server Installation
============================
:Authors:
    Cao Tri DO <cao-tri.do@mazars.fr>
:Version: 2023 08


Install R
============

Source: https://linuxize.com/post/how-to-install-r-on-ubuntu-20-04/

1. Install the dependencies necessary to add a new repository over HTTPS:

.. code-block:: bash

  sudo apt install dirmngr gnupg apt-transport-https ca-certificates software-properties-common

2. Add the CRAN repository to your system sources list:

.. code-block:: bash

  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
  sudo add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu focal-cran40/'

3. Install R by typing

.. code-block:: bash

  sudo apt install r-base-core

4. The installation may take a few minutes to complete. Once completed, verify it by printing the R version

.. code-block:: bash
  
  R --version

5. To be able to compile R packages, you need to install the build-essential package:

.. code-block:: bash
  
  sudo apt install build-essential


Install R Server
================

source: https://linux.how2shout.com/install-rstudio-server-open-source-on-ubuntu-20-04-lts/

1. Run update

.. code-block:: bash

  sudo apt update

2. Install Gdebi: To easily install Rstudio Desktop or Server, we will use the Gdebi Package manager that will automatically fetch and install the required dependencies needed by the tool.

.. code-block:: bash

  sudo apt-get install gdebi-core

3. Download RStudio Server package

.. code-block:: bash

  wget https://s3.amazonaws.com/rstudio-ide-build/server/bionic/arm64/rstudio-server-2022.12.1-366-arm64.deb

4. Installation command: ``sudo gdebi package-name`` Note: Replace package-name in the above command with the downloaded Rstudio file. For example, here we have downloaded rstudio-server-2022.12.1-366-arm64.deb thus the command will be:

.. code-block:: bash

  sudo gdebi rstudio-server-2022.12.1-366-arm64.deb

5. Create Users to Access Rstudio: Yes, of course, we can use our current root or non-root user to access the Rstudio web interface, however, if you have multiple members or developers in the team and all of them need access to Web Rstudio IDE, then create different users one by one.

The command to create a new user is:

.. code-block:: bash

  sudo adduser h2s

*Note: Replace the h2s with the username that you want to create and use with Rstudio.*

6. Open and Access Rstudio

To access this R web-based development platform simply note down the server-ip-address and use that with port number 8787. For instance, if our server where we have installed the Rstudio is 192.168.0.15 then in the browser it will be like this:

192.168.0.05:8787

Once you have the login screen, use the username and password you have created.