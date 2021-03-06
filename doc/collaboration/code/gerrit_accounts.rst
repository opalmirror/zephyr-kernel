.. _gerrit_accounts:

Requesting a Linux Foundation Account
#####################################

Contributions to the Zephyr kernel code base require a Linux Foundation account.
Follow the steps below to create a Linux Foundation account.

Creating a Linux Foundation ID
******************************

#. Go to the `Linux Foundation ID website`_.

#. Select the option :guilabel:`I need to create a Linux Foundation ID`.

   .. figure:: figures/setting_up01.png
      :scale: 75 %
      :alt: linuxfoundation.org identity page

#. Fill out the form that appears:

   .. figure:: figures/setting_up02.png
      :scale: 75 %
      :alt: New account form

#. Open your email account and look for a message with the subject line:
   "Validate your Linux Foundation ID email".

#. Open the received URL to validate your email address.

#. Verify the browser displays the message :guilabel:`You have successfully
   validated your e-mail address`.

#. Access `Gerrit`_ by selecting :guilabel:`Sign In`:

   .. figure:: figures/setting_up03.png
      :scale: 75 %
      :alt: Gerrit without being signed in

#. Use your Linux Foundation ID to Sign In:

   .. figure:: figures/setting_up04.png
      :scale: 75 %
      :alt: Gerrit sign in screen

Configuring Gerrit to Use SSH
*****************************

Gerrit uses SSH to interact with your Git client. A SSH private key
needs to be generated on the development machine with a matching public
key on the Gerrit server.

If you already have a SSH key-pair, skip this section.

As an example, we provide the steps to generate the SSH key-pair on a Linux
environment. Follow the equivalent steps on your OS.

#. Create a key-pair, enter:

   .. code-block:: console

      $ ssh-keygen -t rsa -C "John Doe john.doe@example.com"

   .. note::
      This will ask you for a password to protect the private key as it
      generates a unique key. Please keep this password private, and DO NOT
      enter a blank password.

   The generated key-pair is found in:
   :file:`~/.ssh/id_rsa` and :file:`~/.ssh/id_rsa.pub`.

#. Add the private key in the :file:`id_rsa` file in your key ring:

   .. code-block:: console

      $ ssh-add ~/.ssh/id_rsa

Once the key-pair has been generated, the public key must be added to Gerrit.

Follow these steps to add your public key :file:`id_rsa.pub` to the Gerrit
account:

1. Go to `Gerrit`_.

2. Click on your account name in the upper right corner.

3. From the pop-up menu, select :guilabel:`Settings`.

4. On the left side menu, click on :guilabel:`SSH Public Keys`.

5. Paste the contents of your public key :file:`~/.ssh/id_rsa.pub` and click
   :guilabel:`Add key`.

.. note::
   The :file:`id_rsa.pub` file can be opened with any text editor. Ensure
   that all the contents of the file are selected, copied and pasted into the
   :guilabel:`Add SSH key` window in Gerrit.

.. warning::
   Potential Security Risk! Do not copy your private key
   :file:`~/.ssh/id_rsa` Use only the public :file:`~/.ssh/id_rsa.pub`.

.. _code_check_out:

Checking Out the Source Code
****************************

#. Ensure that SSH has been set up properly. See
   `Configuring Gerrit to Use SSH`_ for details.

#. Clone the repository:

   a. Use your Linux Foundation ID:

      .. code-block:: console

         $ git clone
         ssh://LFID@gerrit.zephyrproject.org:29418/zephyr zephyr-project

   .. note:: LFID should be replaced with your Linux Foundation ID.


You have successfully checked out a copy of the source code to your local
machine.

.. important::
   Linux users need to download the Zephyr SDK even after successfully
   cloning the source code. The SDK contains packages that are not part of
   the Zephyr Project. See :ref:`zephyr_sdk` for details.

Gerrit Commit Message Hook
**************************

.. include:: ../collaboration/code/gerrit_practices.rst
   :start-line: 42
   :end-line: 49


.. toctree::
   :maxdepth: 2

   installation_linux.rst
   installation_mac.rst

.. _Linux Foundation ID website: https://identity.linuxfoundation.org

.. _Gerrit: https://gerrit.zephyrproject.org/
