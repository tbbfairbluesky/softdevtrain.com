.. title: Revert file in a release to version in a previous release
.. slug: revert-file-in-a-release-to-version-in-a-previous-release
.. date: 2018-03-14 15:28:00 UTC-05:00
.. tags: git
.. category: Git Standard Usage 
.. link: 
.. description: Steps to revert a file in a release to the version of that file that was in a previous release
.. type: text

.. contents:: Table of Contents
   :depth: 1

----

Example Situation
=================

We have a file, ``FreeSurfer/FreeSurferPipeline.sh``, that was released with version v3.25.0 (from branch
``release/v3.25.0`` that needs to be reverted to the state it was in in version v3.24.0 (branch 
``release/v3.25.0``. We need to use this reverted file as part of a bugfix release, v3.25.1, that
is from a branch off of ``release/v3.25.0``.

----

Steps
=====

#. Checkout the release on which you are going to base the bugfix release (``release/v3.25.0``)

   .. code-block::

	  $ git checkout release/v3.25.0

#. Create and checkout a new branch that is based upon the currently checked out branch

   .. code-block::

	  $ git branch revert-freesurfer-6-changes
	  $ git checkout revert-freesurfer-6-changes

#. Make changes in the new branch and commit them

   In this case, the change is to overwrite a file in the branch with the same file from another branch.
   The other branch in this case is the previous release branch (``release/v3.24.0``).

   .. code-block::

	  $ git checkout *<other-branch>* *<file>*
	  $ git checkout release/v3.24.0 FreeSurfer/FreeSurferPipeline.sh
	  $ git commit -m "Reverted FreeSurfer/FreeSurferPipeline.sh to the code released with version v3.24.0"

#. Verify changes

   See `Comparing versions of a file between 2 Git Branches <link://slug/comparing-versions-of-a-file-between-2-git-branches>`_

   .. code-block::

	  $ git difftool revert-freesurfer-6-changes release/v3.25.0 FreeSurfer/FreeSurferPipeline.sh

   Should show changes because file has been overwritten.

   .. code-block::

	  $ git difftool release/v3.24.0 revert-freesurfer-6-changes FreeSurfer/FreeSurferPipelinesh

   Should show *no* changes because the version in branch ``revert-freesurfer-6-changes`` should now be the
   same as that in branch ``release/v3.24.0``.

#. Create a bugfix release

   See `Creating a Release from a Bugfix Branch <link::/slug/creating-a-release-from-a-bugfix-branch>`_
