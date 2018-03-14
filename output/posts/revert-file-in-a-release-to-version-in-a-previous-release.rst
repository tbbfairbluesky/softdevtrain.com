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






.. code-block::

   git diff branch1 branch2 path/to/myfile.ext

or 

.. code-block::

   git difftool branch1 branch2 path/to/myfile.ext

----

Notes
=====

#. If the files are identical, the command will silently return, show no output, and not
   start any external tool.
