.. title: Creating a Release from a Bugfix Branch
.. slug: creating-a-release-from-a-bugfix-branch
.. date: 2018-03-14 16:04:00 UTC-05:00
.. tags: git release, git
.. category: Git Standard Usage 
.. link: 
.. description: Step by step guide to creating a release from a git bugfix branch
.. type: text

.. contents:: Table of Contents
   :depth: 1

----

Assumptions
===========

* All changes to be included in the release have been made on the ``bugfix-branch``
* The ``bugfix-branch`` is a branch off of a ``release-branch`` (e.g. ``release/v3.25.0``) 

----

Steps
=====

#. Commit all your changes on the ``bugfix-branch``

#. Check out the ``release-branch`` (the branch that the ``bugfix-branch`` came off of in the first place).

   .. code-block::

	  $ git checkout release/v3.25.0

#. Create and checkout a *new* branch which will contain the bugfix changes and the release. We'll
   call this *new* branch the ``bugfix-release`` branch.

   .. code-block:: bash

	  $ git branch release/v3.25.1    # create the bugfix-release branch
	  $ git checkout release/v3.25.1  # checkout the bugfix-release branch

#. Merge the ``bugfix-branch`` changes into the ``bugfix-release`` branch and squash the changes into one big change set.

   .. code-block::

	  $ git merge --squash bugfix-branch

#. Fix up the ``version.txt`` file

   .. code-block::

	  $ git_current_branch > version.txt
	  $ git add version.txt

   Note: ``git_current_branch`` should be an alias defined as:

   .. code-block::

	  $ alias git_current_branch='git symbolic-ref -q HEAD --short'

#. Commit all changes to the ``bugfix-release`` branch

   .. code-block::

	  $ git commit -m "Big description of the bugfix changes"

   Now all the changes from the ``bugfix-branch`` are in the ``bugfix-release`` (e.g. release/v3.25.1) branch.

#. Push everything to the origin (GitHub)

   .. code-block::

	  $ git push origin --all

#. Remove the local ``bugfix-branch`` whose changes you've now merged and committed to the ``bugfix-release`` branch.

   .. code-block::

	  $ git branch -D bugfix-branch

#. Remove the remote ``bugfix-branch`` from the origin repository (GitHub)

   .. code-block::

	  $ git push origin --delete bugfix-branch

#. Create a tag in the ``bugfix-release`` branch 

   .. code-block::

	  $ git checkout *<bugfix-release>*
	  $ git checkout release/v3.25.1
	  $ git_current_branch > version.txt
	  $ git add version.txt
	  $ git commit -m "Created v3.25.1"
	  $ git tag -a v3.25.1 -m "Tagging v3.25.1"
	  $ git push --tags origin release/v3.25.1

#. Go to https://github.com, log in, and create a release from the tag

   Releases --> Draft a new release --> Select tag

   * Provide a Title and Description
   * Publish the release

#. Make sure you don't leave your local ``git`` repository with the release branch checked out.

   You do not want to make further changes to that branch.

   Also, you *most likely* (but not always) want your bug fix to go into the master branch so that it gets included
   in any future releases.

   .. code-block:: bash

	  $ git checkout master
	  $ git merge release/v3.25.1 # substitute your bugfix release
	  $ git_current_branch > version.txt
	  $ git add version.txt
	  $ git commit -m "Updated version.txt"
	  $ git push origin --all

#. As always, further feature changes should go in a feature branch (off of ``master``) and further bugfix changes should
   go in a bugfix branch (off of the release for which the bugs are being fixed).

