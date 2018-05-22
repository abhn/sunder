Install Sunder
==============

We provide builds for macOS and Linux on our `GitHub Releases page`_.
For platform-specifc installation instructions, see below.

macOS
-----

#. Download the ``.dmg`` from our `GitHub Releases page`_.
#. Open the ``.dmg`` and drag Sunder to your Applications folder.

Linux (Debian or derivative)
----------------------------

#. Download the .deb from our `GitHub Releases page`_.
#. Open a Terminal and run:

   .. code:: sh

      sudo dpkg -i /path/to/sunder.deb
      sudo apt-get update && sudo apt-get install -yf

#. Type ``sunder`` at your Terminal to launch Sunder.

Tails (Tested on Tails 3.7)
---------------------------

.. warning:: Internet access is required for the initial install.

#. Set up a Tails VM with persistence (see `Tails User Guide`_).
#. Boot into Tails with Persistence and Admin password enabled.
#. Download the .deb from our `GitHub Releases page`_ to the Tor (Persistent) folder.
#. Download the signature (.asc) from our `GitHub Releases page`_ to the Tor (Persistent) folder.
#. Open a terminal and run:

  .. code:: sh

     # Copy sunder to the persistent volume and verify the signature
     cd ~/Persistent
     mkdir sunder && cd sunder
     cp ~/Tor\ Browser/sunder_0.1.1_amd64.deb* .
     gpg --verify sunder_0.1.1_amd64.deb.asc
     mkdir /tmp/sunder && cd /tmp/sunder
     # Download the dependencies:
     sudo apt download gconf2 gconfservice libappindicator1 libgconf-2-4 gconf2-common libdbusmenu-glib4 libdbusmenu-gtk4 libindicator7
     # Copy the dependencies to the persistent volume:
     cp * .deb ~/Persistent/sunder
     sudo dpkg -i *.deb
     # If prompted, run:
     sudo apt --fix-broken-install
     # start sunder
     sunder

Note that you will need reinstall Sunder each time you boot into Tails (with persistence and Admin enabled) by opening a terminal and running:

   .. code:: sh

      cd ~/Persistent/sunder
      sudo dpkg -i *.deb
      # If prompted, run:
      sudo apt --fix-broken-install

.. warning:: Updates to Tails may break functionality.

.. _`GitHub Releases page`: https://github.com/freedomofpress/sunder/releases
.. _`Tails User Guide`: https://tails.boum.org/doc/first_steps/index.en.html
