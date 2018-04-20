==========
AWS Set Up
==========

Overview
========

In order for us to process images stored in AWS we need programmatic access to your storage bucket(s). This access is granted to a special IAM (Identity Access Management) User that must be created via the AWS dashboard or CLI. A policy is then attached to this IAM User that grants it permission to read and write from your buckets.

All we then require are the access keys for the IAM user.


Creating a New IAM User
=======================

An IAM User can be easily created via the AWS Console (Services/IAM/Users), as shown in this section. It is also possible to set up an IAM User via the AWS CLI, but this is not covered here - please refer to the `official documentation <https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html>`_ for details. 

1. Sign in to your AWS Management Console
2. Navigate to `Security, Identity & Compliance -> IAM -> Users`
3. Click **Add User**
4. Enter a **User name** - e.g. 'iam_pixelshift'
5. Select 'Programmatic access' as the **Access type** 
6. Click **Next**
7. Continue past the 'Set permissions for <username>' screen without selecting anything(permissions will be set shortly).
8. On the 'Review' screen, ignore the permssions warning and click **Create User**
9. You should see the 'Success' page with your new IAM User, with access to the *Access Key Id* and *Secret Access Key* **Important:** This is the only time you can view both keys (though you can re-generate the secret if you need to). :webroot:`dashboard` Either copy and paste them directly into your :webroot:`dashboard here <dashboard/setup>` or store them somewhere safe until later.