Gitlab Setup
=========================

Check you have access to Mazars gitlab `code.mazars.global <https://code.mazars.global>`__

Important : you must authenticate yourself on the Mazars gitlab via TheGate connection 
platform and use your OTP from inWebo (illustrated below).

.. tab:: Use TheGate

  Login Gitlab throught TheGate (use the bottom button "Sign in with TheGate")

  |gitlab_auth_the_gate|

.. tab:: Mazars auth

  - Use your Mazars login/Password
  - |mz_login|
  - this will bring you to the In_Webo OTP auth

.. tab:: inWebo OTP

  Below the "inWebo" green links page, click on the second one (Log in with a one-time
  code OTP)

  |in_webo_links|

.. tab:: Enter OTP Code

  Below the "inWebo" Email Address / OTP form, email is your Mazars email, OTP is
  provide by the inWebo mobile app:

  |in_webo_otp|

.. tab:: You're IN

  Below, you're in, you can navigate through repositories you have access to.

  - |git_choose_kng|

.. |git_choose_kng| image:: /docs/setup_accounts/gitlab/gitlab_choose_kng.png
   :width: 430px
.. |in_webo_links| image:: /docs/setup_accounts/gitlab/in_webo_links.png
   :width: 430px
.. |in_webo_otp| image:: /docs/setup_accounts/gitlab/in_webo_otp.png
   :width: 430px
.. |mz_login| image:: /docs/setup_accounts/gitlab/the_gate_mazars_login.png
   :width: 430px
.. |gitlab_auth_the_gate| image:: /docs/setup_accounts/gitlab/gitlab_auth_the_gate.png
   :width: 430px

Now we want to  be able to retrieve code from and push our production to Gitlab. This
requires that Gitlab authorizes you to do so from your Linux terminal. Your SSH keys will
help.

Configure Gitlab with your ssh keys
-----------------------------------
Provide your ssh **public** key into your Gitlab account.


.. tab:: Gitlab SSH keys

   Go to this URL: https://code.mazars.global/-/profile/keys

   |gitlab_set_ssh_key|

   Step_1, Step_2, Step_3 are describe in the image above

.. tab:: cat ssh public key

  From your Linux get your SSH pub key

  For Step_4 please get the content of ~/.ssh/your_pub_key.pub with ``cat``::

     luis@12BANEHIYAT471:~$ cat ~/.ssh/luis.belmar-letelier@mazars.fr.pub
     ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCtEFiagtxuIcNkcm39ZB81 ... bPCX7JsYvSivK4hl
     cASQ== luis.belmar-letelier@mazars.fr
     luis@12BANEHIYAT470:~$

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

   hiya@12BANEHIYAT470:~$ ssh git@code.mazars.global
   The authenticity of host '52.169.52.102 (52.169.52.102)' can't be established.
   ED25519 key fingerprint is SHA256:JDEydp97Lz9ivsPmvJBu4wWa0gBa2dyh2+D8Bhf/JD0.
   This key is not known by any other names
   >> Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
   Warning: Permanently added '52.169.52.102' (ED25519) to the list of known hosts.
   PTY allocation request failed on channel 0
   Welcome to GitLab, @hiya!
   Connection to 52.169.52.102 closed.
   hiya@12BANEHIYAT470:~$

The very first time you SSH the host, a check is done, please answer **yes** lowercase
to the question:

   ``Are you sure you want to continue connecting (yes/no/[fingerprint])?`` **yes**

Next time, Gitlab will just say Welcome, your SSH keys are working fine:

.. code:: bash

   hiya@12BANEHIYAT470:~$ ssh git@code.mazars.global
   PTY allocation request failed on channel 0
   Welcome to GitLab, @hiya!
   Connection to 52.169.52.102 closed.
   hiya@12BANEHIYAT470:~$