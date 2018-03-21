.. title: Setting up new Ubuntu Workstation
.. slug: setting-up-new-ubuntu-workstation
.. date: 2018-03-20 17:32:25 UTC-05:00
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

Remove Amazon Icon from Launcher
================================

#. Right click on Amazon Icon

#. Select Unlock from Launcer in context menu

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
	  $ cd ~/.config
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.config/zim
	  $ cd ~/.local/share/applications
	  $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.local/share/applications/gnome-terminal.desktop

#. Log out and log back in
	  
----

Set Up Terminal Preferences and Profiles
========================================

#. Start a Terminal window

#. Use the Terminal's menus to navigate to ``Terminal --> Preferences --> General``
	  
#. Make sure ``Show menubar by default in new terminals`` and ``Enable the menu accelerator key (F10 by default)`` are
   checked

#. Go to the ``Profiles`` tab

#. Rename the ``Unamed`` profile to SystemDefault.

#. Create CHPC1, CHPC2, hcpx-fs01, TimsPreferred profiles as follows

   * CHPC1 

	 * General: Columns: 132, Rows: 42
	 * Colors: Use colors from system theme

   * CHPC2

	 * General: Columns: 132, Rows: 42
	 * Colors: 
	   * **uncheck** Use colors from system theme
	   * Built-in schemes: Custom
	   * Text color: #000000
	   * Background color: #FCE9C0
	   * **uncheck** Use transparency from system theme

   * hcpx-fs01

	 * General: Columns: 132, Rows: 42
	 * Colors:
	   * **uncheck** Use colors from system theme
	   * Built-in schemes: Black on light yellow
	   * **uncheck** Use transparency from system theme

   * TimsPreferred

	 * General: Columns: 132, Rows: 42
	 * Colors:
	   * **uncheck** Use colors from system them
	   * Built-in schemes: Solarized light
	   * **uncheck** Use transparency from system theme

#. Set defaut to TimsPreferred

#. Test open terminals on all platforms

----

Change Desktop Background
=========================

#. System Settings --> Apperance

#. Change from Wallpapers to Colors & Gradients

#. Select Color Gradient with down indicator, "v"

#. Select Left color and set to pre-prepared light blue color

#. Right Color stays black

----

Install Emacs
=============

#. Issue the following command

   .. code-block::

	  $ sudo apt install emacs24-nox

----

Install Geany
=============

#. Issue the following commands

   .. code-block::

	  $ sudo apt install geany
	  $ sudo add-apt-repository ppa:geany-dev/ppa
	  $ sudo apt-get update
	  $ sudo apt-get install geany geany-plugins

#. Run Geany from the Dash

#. Lock the Geany icon in the Launcher

----

Install Filezilla
=================

#. Issue the following commands

   .. code-block::

	  $ sudo apt-get update
	  $ sudo apt-get install filezilla

#. Add the following sites to the FileZilla Site Manager

   * fastmail ftp
	 * Host: ftp.fastmail.com
	 * Protocol: FTP
	 * Logon Type: Normal
	 * User: Get from KeePass2
	 * Password: Get from KeePass2

   * hcpcourse machine as admin
	 * Host: 128.252.155.182
	 * Protocol: SFTP
	 * Logon Type: Normal
	 * User: Get from KeePass2
	 * Password: Get from KeePass2

   * hcpcourse machine as hcpcourse
	 * Host: 128.252.155.182
	 * Protocol: SFTP
	 * Logon Type: Normal
	 * User: Get from KeePass2
	 * Password: Get from KeePass2

#. Lock FileZilla to Launcher

----

Verify Anaconda Python 3 Environment
====================================

#. Issue the following commands:

   .. code-block::

	  $ source activate python3

#. Make sure this gets you the Anaconda Python 3 environment with Nikola version v7.8.12 or higher installed

   .. code-block::

	  $ nikola --version

----

Install Gnome2 Tools
====================

#. Issue the following commands

   .. code-block::

	  $ sudo apt install libgnome2-bin

   This will give you access to commands line ``gnome-open``

----

Install gitg
============

#. Use the Ubuntu Software Center and search for gitg

#. Install it

#. Run it and make sure the icon is locked to the launcher

----

Install Unity Tweak Tool
========================

#. Use the Ubuntu Software Center and search for Tweak

#. Install the ``Unity Tweak Tool`` instead of the ``Tweak Tool``

#. Unlock it from the launcher

----

Update Mouse Sensitivity
========================

#. See `Fix Mouse Sensitivity in Ubuntu 16.04 <http://www.pontikis.net/blog/fix-mouse-sensitivity-ubuntu>`_

#. Try ``xset m 1/2 4`` in the ``~/.config/autostart/mouse.desktop`` file
   

Update Git
==========

See the post `Update Git <link://slug/update-git>`_

----

Set Up to Save Remote Git Username and Passwords
================================================

See the post `How to save remote username and password for Git <link://slug/how-to-save-remote-username-and-password-for-git>`_

----

Set Up Git FTP
==============

See the section **Preparing to deploy your site using git-ftp** in the post
`Setting up Nikola, git, and git-ftp <link://slug/setting-up-nikola-git-and-git-ftp>`_

----

Install Tkinter for Python
==========================

.. code-block::

   $ sudo apt-get update
   $ sudo apt-get install python-tk
   $ sudo apt-get install python3-tk

----

Configure Nautilus
==================

#. See `How to Easily Add Custom Right-Click Options to Ubuntu's File Manager <https://www.howtogeek.com/116807/how-to-easily-add-custom-right-click-options-to-ubuntus-file-manager/>`_

#. Install nautilus-actions

   .. code-block::

	  $ sudo apt-get install nautilus-actions

#. Log out and log back in in order to restart the Nautilus file manager.

#. Run nautilus-actions from the Dash

#. Add PrependModDate action - replace ${HOME} with actual path to home directory

   * Action
	 * Check *Display item in selection context menu*
	 * Check *Display item in location context menu*
	 * Context Label: ``PrependModDate``

   * Command
	 * Path: ``${HOME}/bin/PrependModDate``
	 * Parameters: ``%B``
	 * Working Directory: ``%d``

   * Execution
	 * Execution Mode: Normal

#. Add RemoveNumbers action

   * Action
	 * Check *Display item in selection context menu*
	 * Check *Display item in location context menu*
	 * Context Label: ``RemoveNumbers``

   * Command
	 * Path: ``${HOME}/bin/remove_numbers``
	 * Parameters: *empty*
	 * Working Directory: ``%d``

   * Execution
	 * Execution Mode: Normal

#. Set up Nautilus Preferences

   * In Nautilus: Edit --> Preferences

	 * Views
	   * View new folders using: *List View*
	   * Arrange Items: *By Name*
	   * Check: *Sort folders before files*
	   * Check: *Show hidden and backup files*

	 * Behavior
	   * Double click to open items
	   * View executable text files when they are opened
	   * Ask before emptying the Trash or deleting files
		 
	 * List Columns
	   * Name, Size, Type, Modified

	 * Preview

	   * Files
		 * Show thumbnails: *Never*

	   * Folders
		 * Count number of items: *Local Files Only*

----

Configure Date and Time Options
===============================

#. Find the *Time & Date* settings in the System Settings App

#. Select the *Clock* tab

#. Check the following options
   
   * In the clock, show Weekday
   * In the clock, show Date and month
   * 24-hour time

----

Set Up for Mounting Remote File Systems
=======================================

#. Install sshfs

   .. code-block::

	  $ sudo apt update
	  $ sudo apt install sshfs

#. Create remote mount directory

   .. code-block::

	  $ cd ~
	  $ mkdir -p mnt/chpc2
	  $ mkdir -p mnt/fs01
	  
#. Test mount CHPC2 file system

   .. code-block::

	  $ mount_chpc2
	  $ cd ~/mnt/chpc2
	  $ ls
	  
#. Test mount fs01 file system

   .. code-block::

	  $ mount_fs01
	  $ cd ~/mnt/fs01
	  $ ls

----

Install Search for Files Tool
=============================

#. Install recoll
   
   .. code-block::

	  $ sudo apt-get install recoll

#. Install catfish

   .. code-block::

	  $ sudo apt-get install catfish

#. Run each to make sure recoll is indexing and to lock catfish icon to Launcher

----

Update to Latest Version of LibreOffice
=======================================

#. Issue the following commands:

   .. code-block::

	  $ sudo add-apt-repository ppa:libreoffice/ppa
	  $ sudo apt update
	  $ sudo apt install libreoffice

----

Install Torque/PBS Job Scheduler on the Workstation
===================================================

https://jabriffa.wordpress.com/2015/02/11/installing-torquepbs-job-scheduler-on-ubuntu-14-04-lts/

FQDN: leopardws01.wucon.wustl.edu
