=========================
Gitlab Setup
=========================

Check you have access to the Public Gitlab `Gitlab <https://about.gitlab.com/>`__

Login Gitlab
=========================

Login Gitlab with your user and password

.. image:: /docs/setup_accounts/gitlab/gitlab_signin.png
   :width: 500

Below, you're in, you can navigate through repositories you have access to.

.. image:: /docs/setup_accounts/gitlab/gitlab_choose_kng.png
   :width: 500



Now we want to  be able to retrieve code from and push our production to Gitlab. This
requires that Gitlab authorizes you to do so from your Linux terminal. Your SSH keys will
help.

Configure Gitlab with your ssh keys
========================================
Provide your ssh **public** key into your Gitlab account.


.. tab:: Gitlab SSH keys

   Go to this URL: https://gitlab.com/-/profile/keys

   |gitlab_set_ssh_key|

   Step_1, Step_2, Step_3 are describe in the image above

.. tab:: cat ssh public key

  From your Linux get your SSH pub key

  For Step_4 please get the content of ~/.ssh/your_pub_key.pub with ``cat``::

     >> cat ~/.ssh/luis.belmar-letelier@mazars.fr.pub
     ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCtEFiagtxuIcNkcm39ZB81 ... bPCX7JsYvSivK4hl
     cASQ== luis.belmar-letelier@mazars.fr

  .. image:: /docs/empty.png
     :width: 200px

.. tab:: Add

   below, cut and past the SSH public key to the form and click to "Add"

   |gitlab_add_ssh_key|

.. tab:: Added

   Your key has been added in your Gitlab profile

   |gitlab_ssh_key_done|

.. |gitlab_set_ssh_key| image:: /docs/setup_accounts/gitlab/gitlab_config_ssh_pub_key.png
   :width: 430px
.. |gitlab_add_ssh_key| image:: /docs/setup_accounts/gitlab/gitlab_add_ssh_pub_key.png
   :width: 430px
.. |gitlab_ssh_key_done| image:: /docs/setup_accounts/gitlab/gitlab_ssh_key_done.png
   :width: 430px

---

Test it:

.. code::

   >> ssh git@gitlab.com

If it is the first time, you should obtain this message: Answer it with 'yes'

The very first time you SSH the host, a check is done, please answer **yes** lowercase
to the question:

   ``Are you sure you want to continue connecting (yes/no/[fingerprint])?`` **yes**

Next time, Gitlab will just say Welcome, your SSH keys are working fine:

.. code::

   The authenticity of host '52.169.52.102 (52.169.52.102)' can't be established.
   ED25519 key fingerprint is SHA256:JDEydp97Lz9ivsPmvJBu4wWa0gBa2dyh2+D8Bhf/JD0.
   This key is not known by any other names
   >> Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
   Warning: Permanently added '52.169.52.102' (ED25519) to the list of known hosts.

And then, you obtain:

.. code:: bash
   
   PTY allocation request failed on channel 0
   Welcome to GitLab, @malganis35!
   Connection to 172.65.251.78 closed.