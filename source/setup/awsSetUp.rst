==========
AWS Set Up
==========

Overview
========

In order for us to process images stored in AWS we need programmatic access to your storage bucket(s). You grant this access to a special IAM (Identiy Access Management) User that you create via the AWS dashboard or CLI. Then, you attach as policy to this IAM User that grants it permission to read and write from your buckets.

All we then require are the access keys for the IAM user.

Creating a New IAM User
=======================

An IAM User can be created via the AWS Console (Services/IAM/Users) or CLI, you can refer to the `official documentation <https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html>`_ for details. 