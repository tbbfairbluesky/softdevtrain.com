.. title: Setting up new Ubuntu Workstation
.. slug: setting-up-new-ubuntu-workstation
.. date: 2018-03-20 11:32:25 UTC-05:00
.. tags: ubuntu, setup, linux 
.. category: Ubuntu
.. link: 
.. description: Notes on setting up an Ubuntu Linux Workstation
.. type: text

.. contents:: Table of Contents
   :depth: 1

----

Update and Upgrade After Initial Boot-up
========================================

#. Start a terminal window (Ctrl - Alt - T)

#. Enter the following commands

   .. code-block::

	  $ sudo apt-get update
	  $ sudo apt-get upgrade
	  $ sudo apt-get install -f

----

Install Dropbox
===============

#. Visit `Install Dropbox <https://www.dropbox.com/install-linux>`_

#. Download Ubuntu (.deb) 64-bit

#. Open the .deb with Ubuntu Software Center

#. Once Dropbox is installed, run Dropbox and configure it

   Select the Dropbox icon in the upper right and choose Preferences...

   Set the following preferences

General
-------

* Check the ``Start Dropbox on system startup`` box

Account
-------

* Link the computer to your Dropbox account

Bandwidth
---------

* No changes from defaults

Proxies
-------

* No changes from defaults

Notifications
-------------

* Uncheck Notify me about
  * New files synced
  * Edits to files

Sync
----

* Move Dropbox folder to ``${HOME}/Documents``

  This should end up placing the files in ``${HOME}/Documents/Dropbox``

* Choose *Selective Sync...* and only sync 

  * Apps
  * KeePass2
  * MATLAB
  * Notebooks
  * ubuntu
  * WUSTL

**It may take a couple days before Dropbox folders and files are fully synced.**

----

Install Zimwiki
===============

#. In a terminal window, issue the following commands:

#. Enter the following commands

   .. code-block::

	  $ sudo apt-get update && sudo apt-get upgrade
	  $ sudo add-apt-repository ppa:jaap.karssenberg/zim
	  $ sudo apt-get install zim

#. Open Zim and Open the Following 3 Notebooks

   * ``WUSTL`` at ``${HOME}/Documents/Dropbox/Notebooks/WUSTL``
   * ``Personal`` at ``${HOME}/Documents/Dropbox/Notebooks/Personal``
   * ``Training`` at ``${HOME}/Documents/Dropbox/Notebooks/Training``

#. Set default notebook to WUSTL

#. Lock the Zim Desktop Icon to the Launcher and move it up to the top, just below the Dash
 
----

Change Ubuntu Application Menu Location
=======================================

#. From the *Dash* (Ubuntu icon in upper left) enter "settings" and launch the System Settings app.
   (or use the *System Settings* icon in the launcher (looks like a gear with a wrench in front of it)

#. Navigate to Appearance --> Behavior

#. Under **Show the menus for a window** choose *In the window's title bar*

----

Configure, Run, and Check Thunderbird
=====================================

#. Thunderbird should already be installed as it is a default application for Ubuntu

#. **Before** running Thunderbird for the first time

   .. code-block::

	  $ cd 
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.thunderbird

#. Run Thunderbird and check accounts, folders, sending mail, etc.

#. Lock the Thunderbird Mail icon to the Launcher and move it up to just below the Zim Desktop Wiki icon

----

Install and Configure KeePass2
==============================

#. Issue the following commands to install KeePass2

   .. code-block::

	  $ sudo add-apt-repository ppa:jtaylor/keepass
	  $ sudo apt-get update
	  $ sudo apt-get install keepass2

#. Run KeePass2 from the Dash

#. Open KeePass2 database file - in synced Dropbox

#. Lock the KeePass2 icon to the Launcher

----

Install Chrome
==============

#. Visit https:://www.google.com/chrome

#. Select the ``Download Chrome`` button

#. Select ``64 bit .deb (For Debian/Ubuntu)``

#. Select ``Accept and Install``


Set Up Symbolic Links in ${HOME}
================================

#. Issue the following commands

   .. code-block:: bash

	  $ cd
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/anaconda3
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/awstest
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.bash_aliases
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.bash_logout
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.bashrc
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/bin
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.emacs
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.emacs.d
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/projects
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.ssh
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.thunderbird # This one should be already done.
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/tools
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/workspace

----

Set Up Terminal Preferences and Profiles
========================================

ipsum

----


Install Emacs
=============

#. Issue the following commands

   .. code-block::

	  $ sudo apt install emacs24-nox

----

Install Geany
=============

ipsum

----

Install Filezilla
=================

ipsum

----

Install Anaconda Python 3 Environment
=====================================

ipsum

----

Install Gnome2 Tools
====================

#. Issue the following commands

   .. code-block::

	  $ sudo apt install libgnome2-bin

   This will give you access to commands line ``gnome-open``

----

Update Git
==========

Link to other post

----

Set Up to Save Remote Git Username and Passwords
================================================

Link to other post

----

Set Up Nikola
=============

Link to other post


