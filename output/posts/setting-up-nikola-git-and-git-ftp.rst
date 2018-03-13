.. title: Setting up Nikola, Git, and git-ftp
.. slug: setting-up-nikola-git-and-git-ftp
.. date: 2018-03-13 14:40:07 UTC-05:00
.. tags: nikola, git, setup
.. category: nikola
.. link: 
.. description: How to set up Nikola with a Git Repositor and Use git-ftp to deploy a static web-site
.. type: text
.. updated: 2018-03-13 14:55:00 UTC-05:00	  


Important Links
===============

* `Nikola Getting Started Guide <https://getnikola.com/getting-started.html>`_
* `The Nikola Handbook <https://getnikola.com/handbook.html>`_

Assumptions
===========

The following assumes:

* You already have a Python 3 environment set up using Anaconda.
* You have git version 2.16.2 or later installed
* You are working with your Python 3 and git tools at a ``bash`` shell

Links to Sub-Tasks covered within this page
===========================================  

#. `Installation of Nikola`_
#. `Associating your site source code with a GitHub Repository`_
#. `Building and viewing your site locally`_
#. `Preparing to deploy your site using git-ftp`_
  
Substitutions in commands
=========================

Make the following substitutions in the commands below:

* Substitute your Python 3 environment name for ``python3``
* Substitute the name of the directory in which you keep your
  source code projects for ``~/projects``
* Substitute the sub-directory of ``~/projects`` you want to
  use for the source code for your site for ``softdevtrain.com``.

----
  
Installation of Nikola
======================
  
#. Start your Python 3 environment

   .. code-block:: 

	  $ source activate python3

#. Install prerequisite Python "Asset management application for Python web development"

   .. code-block:: 
				
	  (python3) $ pip install webassets

#. Ensure that pip and setuptools are up-to-date
					  
   .. code-block::
				
	  (python3) $ pip install --upgrade setuptools pip --ignore-installed

#. Install Nikola

   .. code-block::

	  (python3) $ pip install --upgrade "Nikola[extras]" --ignore-installed

----
   
Associating your site source code with a GitHub Repository
==========================================================

If you are starting a completely new site
-----------------------------------------

#. Create a GitHub repository for your site
   
   * Visit <https://github.com> and login to your GitHub account.
   * Select the *New repository* button
   * Name the repository ``softdevtrain.com`` (your site name)

   You should see the GitHub URL for your new (empty) repository. (e.g. https://github.com/your-user-id/softdevtrain.com.git)

#. Clone your new (empty) GitHub repository

   .. code-block:: 
					 
	  (python3) $ cd ~/projects
	  (python3) $ git clone https://github.com/your-user-id/softdevtrain.com.git

#. Verify that the ~/projects/softdevtrain.com directory has been created

#. Initialize your site

   .. code-block:: 

	  (python3) $ cd ~/projects
	  (python3) $ nikola init softdevtrain.com
				   
   This should create the first version of your site in the ``softdevtrain.com`` sub-directory.
   
If you are working with a site for which a GitHub repository has already been created
-------------------------------------------------------------------------------------

#. Clone the existing GitHub repository

   .. code-block:: 
					 
	  (python3) $ cd ~/projects
	  (python3) $ git clone https://github.com/your-user-id/softdevtrain.com.git
   
----

Building and viewing your site locally
======================================

#. Build your site

   .. code-block:: 

	  (python3) $ cd ~/projects/softdevtrain.com
	  (python3) $ nikola build

#. View your site

   .. code-block::
		 
	  (python3) $ gnome-open output/index.html

   or

   .. code-block::
		 
      (python3) $ nikola serve -b
	  Ctrl-C when done

----
   
Preparing to deploy your site using git-ftp
===========================================

Install git-ftp
---------------

.. code-block::
		 
   (python3) $ sudo apt-get install git-ftp

Configure git-ftp
-----------------

.. code-block::
		 
   (python3) $ git config git-ftp.url "ftp://your-ftp-site/your-directory" (e.g. ftp://ftp.fastmail.com/*user-id*/files/*site-folder*)




ipsum loram dotaa

	  
