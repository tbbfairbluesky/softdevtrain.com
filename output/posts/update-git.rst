.. title: Update Git
.. slug: update-git
.. date: 2018-03-14 13:03:35 UTC-05:00
.. tags: git
.. category: Git Standard Usage 
.. link: 
.. description: Steps for updating to the latest version of Git
.. type: text
.. updated: 2018-03-14 13:03:35 UTC-05:00

.. contents:: Table of Contents
   :depth: 1

----

Assumptions
===========

* You are using Git from Ubuntu/Debian Linux

----

Useful Links
============

* `Stackoverflow question about saving credentials <https://stackoverflow.com/questions/35942754/how-to-save-username-and-password-in-git>`_
* `Git Credentials Documentation <https://git-scm.com/docs/gitcredentials>`_

----

Steps
=====

#. Add the git-core Personal Package Archive (PPA) repository

   .. code-block::

	  $ sudo add-apt-repository ppa:git-core/ppa

#. Download package lists for repositories and update them to get newest versions of packages

   .. code-block::

	  $ sudo apt-get update

#. Install the latest version of git

   .. code-block::

	  $ sudo apt-get install git
