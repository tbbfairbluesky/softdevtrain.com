.. title: Creating a Release from a Feature Branch
.. slug: creating-a-release-from-a-feature-branch
.. date: 2018-03-14 11:35:00 UTC-05:00
.. tags: git release, git
.. category: Git Standard Usage 
.. link: 
.. description: Step by step guide to creating a release from a git feature branch
.. type: text
.. updated: 2018-03-14 11:35:00 UTC-05:00

Assumptions
===========

* All changes to be included in the release have been made on the ``feature-branch``
* We release from the ``master`` branch by merging ``feature-branch`` into the ``master`` branch
* A **feature release** (e.g. X.Y.0) gets a branch of its own off of the ``master``	

Steps
=====

#. Commit all your changes on the ``feature-branch``

#. Merge the ``master`` branch into the ``feature-branch`` and get all conflicts resolved.

   This is in case any changes were made in the ``master`` branch since the point at which
   the ``feature-branch`` was branched off from the ``master`` 

   .. code-block::

	  $ git checkout feature-branch
	  $ git merge master

#. Merge the ``feature-branch`` into the ``master`` branch and squash the changes into one big change set.
   
   This is to get the ``feature-branch`` changes into the ``master`` for use in the release and
   to ensure that these changes are included in any subsequent feature change branches. (Since
   feature change branches should be branches off of the ``master``.) The squashing means that all the
   changes for the current feature will be under one commit comment.

   .. code-block::

	  $ git checkout master
	  $ git merge --squash feature-branch

#. Fix up the ``version.txt`` file -- make it say ``master``

   .. code-block::

	  $ git_current_branch > version.txt
	  $ get add version.txt

   Note: ``git_current_branch`` should be an alias defined as:

   .. code-block::

	  alias git_current_branch='git symbolic-ref -q HEAD --short'

#. Commit all changes to the ``master`` branch. This is the one commit for all of the 
   feature-related changes

   .. code-block::

	  $ git commit -m "Big description of feature branch changes"

   Now all the changes you made in ``feature-branch`` are in the ``master`` branch.

#. Push everything to the origin (GitHub)

   .. code-block::

	  $ git push origin --all

#. Remove the local ``feature-branch`` whose changes you've now merged and committed to the ``master`` branch.

   .. code-block::

	  $ git branch -D feature-branch

#. Remove the remote ``feature-branch`` from the origin repository (GitHub)

   .. code-block::

	  $ git push origin --delete feature-branch

#. Create a release version in a release branch

   .. code-block:: bash

	  $ git checkout master
	  $ git branch release/v1.7.0  # substitute your intended release number
	  $ git checkout release/v1.7.0
	  $ git_current_branch > version.txt
	  $ git add version.txt
	  $ git commit -m "Created v1.7.0"
	  $ git tag -a v1.7.0 -m "Tagging v1.7.0"
	  $ git push --tags origin release/v1.7.0

#. Go to https://github.com, login in, and create a release from the tag

   Releases --> Draft a new release --> Select tag

   * Provide a Title: e.g. "Multirun ICA+fIX on 7T Retinotopy Data"
   * Provide a Description: e.g. "This release is intended to be used for running Multirun ICA+FIX processing on 7T Retinotopy data"
   * Publish the release

#. Make sure you don't leave your local ``git`` repository with the release branch checked out.

   You do not want to make further changes to that branch. If you are making a bugfix release (a final point release,
   e.g. v1.7.1 or v1.7.2), you will create a feature/bugfix branch off o the release branch. 

   .. code-block::

	  $ git checkout master

#. Make sure all the changes in the release branch are merged into the ``master`` branch and the ``master``
   branch is ready to use as a starting point for future changes.

   .. code-block:: bash

	  $ git merge release/v1.7.0 # substitute your release number
	  $ git_current_branch > version.txt
	  $ git add version.txt
	  $ git commit -m "Updated version.txt"
	  $ git push origin --all

#. Further changes should be done in a new feature branch, not on the ``master`` branch.
   


