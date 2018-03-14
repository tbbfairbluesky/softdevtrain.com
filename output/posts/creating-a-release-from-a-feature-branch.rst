.. title: Creating a Release from a Feature Branch
.. slug: creating-a-release-from-a-feature-branch
.. date: 2018-03-14 10:13:36 UTC-05:00
.. tags: git release, git
.. category: Git Standard Usage 
.. link: 
.. description: Step by step guide to creating a release from a git feature branch
.. type: text


Assumptions
===========

* All changes to be included in the release have been made on the ``feature-branch``
* We release from the ``master`` branch by merging ``feature-branch`` into the ``master`` branch
* A **feature release** (e.g. X.Y.0) gets a branch of its own off of the ``master``	

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

   Note: ``git_current_branch`` is an alias defined as:

   .. code-block::

	  alias git_current_branch='git symbolic-ref -q HEAD --short'

#. Commit all changes to the ``master`` branch. This is the one commit for all of the 
   feature-related changes

   .. code-block::

	  $ git commit -m "Big description of feature branch changes"

   Now all the changes you made in ``feature-branch`` are in the ``master`` branch.

#. Push everything to the origin (GitHub)

   
