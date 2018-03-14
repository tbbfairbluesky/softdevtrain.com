.. title: Comparing versions of a file between 2 Git Branches
.. slug: comparing-versions-of-a-file-between-2-git-branches
.. date: 2018-03-14 14:52:34 UTC-05:00
.. tags: git
.. category: Git Standard Usage 
.. link: 
.. description: Simply command to compare version of a file between 2 different git branches
.. type: text

.. contents:: Table of Contents
   :depth: 1

----

Command
=======

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
