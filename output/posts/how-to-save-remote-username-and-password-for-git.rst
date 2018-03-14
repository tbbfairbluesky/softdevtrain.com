.. title: How to save remote username and password for Git
.. slug: how-to-save-remote-username-and-password-for-git
.. date: 2018-03-14 12:48:35 UTC-05:00
.. tags: git
.. category: Git Standard Usage 
.. link: 
.. description: Steps for storing Git credentials
.. type: text
.. updated: 2018-03-14 12:48:35 UTC-05:00

.. contents:: Table of Contents
   :depth: 1

----

Assumptions
===========

* You are using Git version 2.16.2 or greater

----

Useful Links
============

* `Stackoverflow question about saving credentials <https://stackoverflow.com/questions/35942754/how-to-save-username-and-password-in-git>`_
* `Git Credentials Documentation <https://git-scm.com/docs/gitcredentials>`_

----

Steps
=====

#. Configure the *credential helper* for the repository to be the *store* helper 

   The *store* helper stores the credentials in a user readable only file after the
   credentials are supplied once.

   .. code-block::

	  $ git config credential.helper 'store --file=/home/*my-account*/.git-credentials-WUSTL'

   or 

   .. code-block::

	  $ git config credential.helper 'store --file=/home/*my-account*/.git-credentials-PERSONAL'

#. Issue a command that requires the credentials

   .. code-block:: bash

	  $ git push origin --all # supply username and password as prompted

   If the credentials have already been stored in the specified file, then they will be used.

   If the credentials have *not* already been stored in the specified file, then the username 
   and password will then be stored in the specified file. Next time they are needed,
   they will be retrieved from the *store* (the file) and you will no longer need to supply them.

#. To reset them, you can delete the specified store file and issue a command that requires the 
   credentials.

