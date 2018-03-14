.. title: Setting up Nikola, Git, and git-ftp
.. slug: setting-up-nikola-git-and-git-ftp
.. date: 2018-03-13 14:40:07 UTC-05:00
.. tags: nikola, git, setup
.. category: nikola
.. link: 
.. description: How to set up Nikola with a Git Repositor and Use git-ftp to deploy a static web-site
.. type: text
.. updated: 2018-03-13 14:55:00 UTC-05:00	  


.. contents:: Table of Contents
   :depth: 1

----

Useful Links
============

* `Nikola Getting Started Guide <https://getnikola.com/getting-started.html>`_
* `The Nikola Handbook <https://getnikola.com/handbook.html>`_
* `git-ftp <https://github.com/git-ftp/git-ftp>`_

----

Assumptions
===========

The following assumes:

* You already have a Python 3 environment set up using Anaconda.
* You have git version 2.16.2 or later installed
* You are working with your Python 3 and git tools at a ``bash`` shell

----

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

.. code-block:: bash
		 
   (python3) $ git config git-ftp.url "ftp://your-ftp-site/your-files-directory" 
   (python3) $ git config git-ftp.user "your-ftp-site-user-id"
   (python3) $ git config git-ftp.password "your-ftp-site-password"
   (python3) $ git config git-ftp.syncroot output/ # the output directory of a Nikola repository contains the built site to be deployed

----

Make a change to your content and build your site locally
=========================================================

For example:

.. code-block:: 
   
   (python3) $ nikola new_post

or 

.. code-block:: bash 
   
   (python3) $ nikola new_post -e # make a new post and open up the editor specified in the EDITOR environment variable

Edit your post or content.

Then build the site with the following command:

.. code-block:: 

   (python3) $ nikola build

----

Deploy your site
================

If you have not uploaded any files to the ftp site and you want to completely upload all files to your site.
------------------------------------------------------------------------------------------------------------

.. code-block:: 

   (python3) $ git ftp init

If you have previously uploaded files to your ftp site.
-------------------------------------------------------

.. code-block::

   (python3) $ git ftp push

----

Notes
=====

#. Pushing to the ftp site does *not* cause the changes to be committed to your local repository or
   pushed to the origin remote repository.

   You will need to do ``git commit -m "comment"`` to commit changes locally before they can be 
   pushed to the ftp site.

   You will need to do ``git push origin --all`` (or a similar command) to push your changes to the
   git repository.

#. Your standard operating procedure after setup will usually be:

   *Make or edit a post or page*

   .. code-block::

	  (python3) $ nikola new_post

   *Build the site locally to see how your changes look*

   .. code-block::

	  (python3) $ nikola build

   *See if it looks like what you like*

   .. code-block::

	  (python3) $ gnome-open output/index.html

   or

   .. code-block::
	  
	  (python3) $ nikola serve -b
	  Ctrl-C when done
	  
   *Commit changes to local repository and push them to remote (GitHub) repository*

   .. code-block::
		 
	  (python3) $ git add *files*
	  (python3) $ git commit -m "commit comment"
	  (python3) $ git push origin --all
   
   *Push the changes to the ftp site so they actually show up on your web site*
   
   .. code-block::

	  (python3) $ git ftp push
