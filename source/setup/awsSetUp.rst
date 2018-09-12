==========
AWS Set Up
==========

Overview
========

Pixeshift needs programmatic access to the AWS Storage Bucket(s) where your images are stored. Firstly, you must create an IAM (Identity Access Management) User via the AWS dashboard (or CLI) and copy the access keys in to the :webroot:`Storage section of your Pixelshift Dashboard <Dashboard/Storage#iam-user>`. Then you grant access to this IAM user by attaching a Policy which gives it permission to read from and write to your buckets.

The process is described in more detail below.


Creating a New IAM User
=======================

An IAM User can be easily created via the AWS Console (Services/IAM/Users), as shown in this section. It is also possible to set up an IAM User via the AWS CLI, but this is not covered here - please refer to the `official documentation <https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html>`_ for details. 

1. Sign in to your AWS Management Console.
2. Navigate to `Security, Identity & Compliance -> IAM -> Users`.
3. Click **Add User**.
4. Enter a **User name** - e.g. 'iam_pixelshift'.
5. Select 'Programmatic access' as the **Access type**.
6. Click **Next**.
7. Continue past the 'Set permissions for <username>' screen without selecting anything (permissions will be set shortly).
8. On the 'Review' screen, ignore the permssions warning and click **Create User**.
9. You should now see the 'Success' page showing your new IAM User, along with their *Access Key Id* and *Secret Access Key*.
10. Copy and paste these new IAM keys in to your :webroot:`dashboard here <DashBoard/Storage#iam-user>` or store them somewhere safe for later. **Important:** This is the only time you can view both keys (though you can re-generate the secret if you need to).
11. After you have copied your keys, you can click **Close**. 

Granting Access with an Inline Policy
=====================================

Once you have created an IAM User, you must attach an Inline Policy to it that grants access to your Storage Bucket(s). You can choose to either grant access to individual Buckets or all of them (though this isn't recommended). 

1. First use your :webroot:`Pixelshift Dashboard <DashBoard/Storage#permissions>` to create a policy. Select the type of access and provide Bucket names if necessary.
2. Sign in to your AWS Management Console and navigate to `Security, Identity & Compliance -> IAM -> Users`.
3. Select the IAM User you want to attach the policy to.
4. On the 'Permissions' tab, select **Add inline policy** (bottom right)
5. On the 'Create policy' screen, select the **JSON** tab.
6. Copy the entire policy created in Step 1 into the editor.
7. Click **Review Policy**
8. Provide a name (e.g. pixelshift_access)
9. Click **Create Policy** to finish.

That's it!
