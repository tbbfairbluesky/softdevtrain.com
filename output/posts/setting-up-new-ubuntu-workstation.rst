.. title: Setting up new Ubuntu Workstation
.. slug: setting-up-new-ubuntu-workstation
.. date: 2018-03-23 14:33:25 UTC-05:00
.. tags: ubuntu, setup, linux 
.. category: Ubuntu
.. link: 
.. description: Notes on setting up an Ubuntu Linux Workstation
.. type: text

.. contents:: **Table of Contents**
   :depth: 1

----

Who is this post for?
=====================
   
This post is really not likely to be useful to anybody but me. There are so many assumptions about things
like:
* how and where ``bash`` startup files are stored in Dropbox
* how Thunderbird is already configured and the configuration files are shared across systems via Dropbox
* how Zim Wiki files are shared via Dropbox
* how ``ssh`` and ssh keys are configured
* what tools (Emacs, Geany, etc.) you want to use
* how you want things to appear in the launcher
* your knowledge about using ``sudo``
* etc. 

It would take a week or more to check and list all these assumptions. 

This post is really just a place for me to document the steps that **I** have to take in order to get a new
Ubuntu 16.04 LTS workstation configured for use.

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

Install Insync (Optional)
=========================

#. Download the 64-bit deb

#. Open the deb (with the Ubuntu Software Center)

#. Start insync and configure to Google accounts

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

#. In running KeePass2, choose *Tools* --> *Options...* and select **Lock workspace after KeePass inactivity (seconds): 300**

----

Install Chrome Browser
======================

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
      $ rm .bash_logout
      $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.bash_logout
      $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.bash_profile
      $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.bashrc
      $ ln -s ${HOME}/Documents/Dropbox/ubuntu/bin
      $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.emacs
      $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.emacs.d
      $ ln -s ${HOME}/Documents/Dropbox/ubuntu/projects
      $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.ssh
      $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.thunderbird # This one should be already done.
      $ ln -s ${HOME}/Documents/Dropbox/ubuntu/tools
      $ ln -s ${HOME}/Documents/Dropbox/ubuntu/workspace
      $ ln -s ${HOME}/Documents/Dropbox/ubuntu/.gitconfig
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

#. Enable Geany Plugins

   * Tools --> Plugin Manager
   * Check the following Plugins
     * Auto-close
     * Debugger
     * Extra Selection
     * File Browser
     * GeanyPy
     * GeanyVC
     * Git Change Bar
     * Macros
     * Numbered Bookmarks
     * Overview
     * Split Window
     * Updatechecker

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

      $ sudo su - root
      # cd /mnt
      $ mkdir chpc2
      $ mkdir fs01

#. Test mount CHPC2 file system

   .. code-block::

      $ mount_chpc2
      $ cd /mnt/chpc2
      $ ls

#. Test mount fs01 file system

   .. code-block::

      $ mount_fs01
      $ cd /mnt/fs01
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

#. Remove the LibreOffice Icons from the Launcher

#. Issue the following commands:

   .. code-block::

      $ sudo add-apt-repository ppa:libreoffice/ppa
      $ sudo apt update
      $ sudo apt install libreoffice

----

Add Screenshot Application to Launcher
======================================

#. Search for the Screenshot application in the Dash

#. Run it and lock the icon to the launcher


Make Directories for Mount Points
=================================

#. Issue the following commands:

   .. code-block::

      $ sudo su - root
      # cd /mnt
      # mkdir chpc2
      # chmod 777 chpc2
      # mkdir fs01
      # chmod 777 fs01
      # mkdir ifs01
      # chmod 777 ifs01
      # exit

----

Set up Workspace Switcher
=========================

#. Open ``Appearance`` from Dash

#. Select ``Behavior`` tab

#. Check ``Enable workspaces`` checkbox

#. Run ``Unity Tweak Tool`` from Dash

#. Select ``Workspace Settings`` under ``Window Manager``

#. Selecte ``Horizontal workspaces: 4`` and ``Vertical workspaces: 1``

#. Install compiz

   .. code-block::

      $ sudo apt-get install compiz compizconfig-settings-manager compiz-plugins

#. Run CompizConfig Settings Manager

#. Select ``Window Management``

#. Check ``Workspace Naming`` and enable the necessar plugin

#. Select ``Workspace Naming`` and name the workspaces: ``Administrative``, ``Development``, ``Pipeline Running and Checking``, ``Misc``

----

Install/Set Up Anaconda Python Distribution
===========================================

.. note::

   This should not be necessary

   If you've got the Anaconda Python 3 files stored properly and linked to properly in Dropbox, then this configuration
   and setup should already be done.

#. Download from https://www.continuum.io/downloads

#. Find 64-Bit Pyton 3.x distribution

#. Download the Anaconda installer script, e.g. ``Anaconda3-4.1.1-Linux-x86_64.sh``

#. Run the installer script: $ bash Anaconda3-4.1.1-Linux-x86_64.sh

#. Create and activate a Python 3 environment

   .. code-block::

      $ conda create --name python3 python=3
      $ source activate python3
      $ conda install requests
      $ conda list

----

Install and Configure VLC Media Player
======================================

#. Visit: http://www.videolan.org/vlc/download-ubuntu.html 

#. Download and install

#. Set VLC as default Music and Video application

   * Select ``Settings`` icon in upper right hand corner of screen
   * ``About this computer``
   * ``Default Applications``
   * Music: ``VLC Media Player``
   * Video: ``VLC Media Player``

----

Configure Terminal Keep Alive
=============================

#. See http://askubuntu.com/questions/127369/how-to-prevent-write-failed-broken-pipe-on-ssh-connection

#. Edit /etc/ssh/ssh_config

#. Set ``ServerAliveInterval`` to 120

----

Install Miscellaneous Software Using Ubuntu Software Center
===========================================================

The following can all be install from the Ubuntu Software Center and then remove their icons from the launcher

#. Alternatives Configurator

#. Meld

#. Okular

#. pdfsam


----

Install Java JDK
================

See: https://thishosting.rocks/install-java-ubuntu/

#. Install the Default JDK

   .. code-block::

      $ sudo apt install default-jdk default-jdk-doc

   This should get you Java 8

#. Install Oracle's Java 9 JDK

   .. code-block::

      $ sudo apt-get update && sudo apt-get upgrade
      $ sudo apt-get install software-properties-common
      $ sudo add-apt-repository ppa:webupd8team/java
      $ sudo apt-get update
      $ sudo apt-get install oracle-java9-installer

#. Configure default

   .. code-block::

      $ sudo update-alternatives --config java

   Select the Java you want to be your default and check/set your JAVA_HOME environment
   variable in your ``.bashrc`` file as necessary.  The ``update-alternatives`` program sets
   up symbolic links such that:

   ``/usr/bin/java`` --> ``/etc/alternatives/java``
   ``/etc/alternatives/java`` --> wherever you set it (e.g. ``/usr/lib/jvm/java-9-oracle/bin/java``)

   But it doesn't seem to take care of setting the JAVA_HOME environment variable.

----

Install DragonDisk
==================

#. Visit http://www.s3-client.com/download-s3-compatible-cloud-client.html

#. Download ``.deb`` file for amd64

#. Open the ``.deb`` file in Ubuntu Software Center and install it.


.. S3 Browser - Windows Only

----

Installing R and R Studio
=========================

#. Install R itself

   .. code-block::

      $ sudo apt-get update
      $ sudo apt-get install r-base

#. Install RStudio

   * Visit https://www.rstudio.com/products/rstudio/
   * Click RStudio Desktop link
   * Make sure you are getting the Open Source Edition and click the ``Download RStudio Desktop`` link,
     followed by the appropriate ``Download Now`` button, followed by the link for the ``Ubuntu 16.04/Debian 9+ (64-bit)``
     installer
   * Open the ``.deb`` and install it with Ubuntu Software Center

.. HipChat - don't bother installing now. Will be replaced by Stride I think

----

Install Several Versions of MATLAB
==================================

#. Visit https://www.mathworks.com

#. Select the Login link

#. Login to account (see KeePass2)

#. In *My Software* list, by the Concurrent License for Academic Use, click the Download Link

#. Download versions R2013a, R2014a, R2016b, and R2018a

   For each one:

   * Choose Linux 64-bit for each (of course)
   * Every product that is available for the platform should already be checked/selected
   * Click the **Download ... Products** button
   * Follow the instructions to download all the products into a download directory
   * Follow the instructions to install the product
   * Log in to MATLAB account during installation
   * When prompted for license file, use ``${HOME}/Documents/Dropbox/MATLAB/network.lic`` as path to license file.

   * **Instructions and procedures may be different for each version**

----

Install/Enable SSH Server
=========================

References
----------

* See https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2

Steps
-----

#. Issue the following commands to install the ssh server:

   .. code-block::

      $ sudo apt-get install openssh-server

#. Issue the following command to copy your ssh key (id_rsa.pub) to the machines you want to 
   be able to easily ssh to.

   .. code-block:: bash

      $ # The following is so you can ssh right back to the current workstation (leopardws01.wucon.wustl.edu)
      $ # This is necessary for the Torque job scheduler
      $ ssh-copy-id <your-login-id>@leopardws01.wucon.wustl.edu

   You should then be able to:

   .. code-block::

      $ ssh leopardws01
      $ ssh <your-login-id>@leopardws01.wucon.wustl.edu 

----

Install Torque/PBS Job Scheduler on the Workstation
===================================================

References
----------

* `Installing Torque/PBS job scheduler on Ubuntu 14.04 LTS/16.04 LTS <https://jabriffa.wordpress.com/2015/02/11/installing-torquepbs-job-scheduler-on-ubuntu-14-04-lts/>`_

* `What is the difference between PBS and Torque <http://www.clusterresources.com/pipermail/torqueusers/2008-February/006827.html>`_

  * Torque is an open source implementation of PBS (Portable Batch System). It is a fork of OpenPBS (discontinued), but cannot use the PBS name due to trademark issues.

  * PBS and Torque consist of 3 pieces: ``pbs_server``, ``pbs_sched``, and ``pbs_mom``.

  * The ``pbs_sched`` part can be replaced with the *free* MAUI scheduler or with the *for pay* MOAB scheduler.

  * Torque even allows you to write your own replacement for ``pbs_sched``.

  * There is one ``pbs_server`` which interacts with the user.

  * There are many ``pbs_moms``, one per compute node.

  * There is one ``pbs_sched`` (scheduler) which talks to the ``pbs_server`` and to the ``pbs_moms``

  * I imagine that

    * The ``pbs_server`` gets requests for jobs to run from the user (via the ``qsub`` command). 

    * The ``pbs_sched`` communicates with the ``pbs_server`` to learn what jobs have been requested. The ``pbs_sched`` then implements the scheduling policy.

    * The ``pbs_sched`` communicates with the ``pbs_mom`` on execution/compute nodes to actually cause jobs to start running.

    * This is just a guess at the basic architecture.

Information
-----------

* FQDN: leopardws01.wucon.wustl.edu

* Steps need to be done as root: ``sudo su - root``

Steps
-----

Credit to Installing Torque/PBS blog entry linked above. Steps copied here so as not to be dependent upon a blog whose author might decide to no longer maintain.

#. Install the necessary software

   .. code-block::

      $ apt-get install torque-server torque-client torque-mom torque-pam

#. Stop all torque services and create a clean setup

   .. code-block::

      $ /etc/init.d/torque-mom stop
      $ /etc/init.d/torque-scheduler stop
      $ /etc/init.d/torque-server stop
      $ pbs_server -t create

#. Kill the just-started server

   .. code-block::

      $ killall pbs_server

#. Configure server process

   .. code-block::

      $ echo leopardws01.wucon.wustl.edu > /etc/torque/server_name
      $ echo leopardws01.wucon.wustl.edu > /var/spool/torque/server_priv/acl_svr/acl_hosts
      $ echo root@leopardws01.wucon.wustl.edu > /var/spool/torque/server_priv/acl_svr/operators
      $ echo root@leopardws01.wucon.wustl.edu > /var/spool/torque/server_priv/acl_svr/managers

#. Tell the server that this box itself is a compute node

   Specify 4 cores - which you can change

   .. code-block::

      $ echo leopardws01.wucon.wustl.edu np=4 > /var/spool/torque/server_priv/nodes 

#. Tell the MOM process which server to contact for work

   .. code-block::

      $ echo leopardws01.wucon.wustl.edu > /var/spool/torque/mom_priv/config

#. Restart all the processes

   .. code-block::

      $ /etc/init.d/torque-server start
      $ /etc/init.d/torque-scheduler start
      $ /etc/init.d/torque-mom start

#. Start the scheduler

   .. code-block:: bash

      # set scheduling properties
      $ qmgr -c 'set server scheduling = true'
      $ qmgr -c 'set server keep_completed = 300'
      $ qmgr -c 'set server mom_job_sync = true'

#. Create a default queue (named 'batch', but you can change this)

   .. code-block:: bash

      # create default queue
      $ qmgr -c 'create queue batch'
      $ qmgr -c 'set queue batch queue_type = execution'
      $ qmgr -c 'set queue batch started = true'
      $ qmgr -c 'set queue batch enabled = true'
      $ qmgr -c 'set queue batch resources_default.walltime = 1:00:00'
      $ qmgr -c 'set queue batch resources_default.nodes = 1'
      $ qmgr -c 'set server default_queue = batch'

#. Configure the server to allow submissions from itself

   .. code-block:: bash

      # configure submission pool
      $ qmgr -c 'set server submit_host = leopardws01'
      $ qmgr -c 'set server allow_node_submit = true'

#. Test by "submitting" an interactive job

   .. code-block:: bash

      $ qsub -I

   You should get into a shell on the same box as if you ssh'ed to the same node.

#. Check for running PBS processes

   .. code-block:: 

      $ pgrep -l pbs

   You should see 3 processes (something like)

   .. code-block::

      18030 pbs_server
      18074 pbs_sched
      18122 pbs_mon

   .. note::

      Sometimes on reboot, the ``pbs_sched`` process doesn't get started. Invoking 
      the ``~/bin/restart_torque`` script after a reboot should fix that problem 
      for now.  It needs to be investigated why started ``pbs_sched`` on boot-up
      doesn't seem to be working.

      Here's one possible place to start the investigation:

      https://stackoverflow.com/questions/36013057/all-jobs-in-q-queue-for-torque-pbs-scheduler

#. Modify/configure the ``qpeek`` script

   * ``qpeek`` is a local Perl script instead of an actual PBS/Torque command

   * Edit ``~/bin/qpeek`` and replace the like that looks like:

   .. code-block:: perl

      my $host    = "mgt2.cluster" # or whatever host is listed

   with

   .. code-block:: perl

      my $host    = "leopardws01.wucon.wustl.edu" # or what your FQDN is

