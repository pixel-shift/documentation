
============
Introduction
============

About
-----

Pixelshift.io is a cloud-based service for processing large numbers of images at scale. It has been created from the ground up with this sole objective, and it is the most efficient and lowest-cost service of its type. Whether you need to process hundreds, or hundreds of thousands of images, our Microservice architecture running on Kubernetes rapidly adapts to handle any size of workload.   

Supported operations include resizing, cropping, re-colouring and changing file-types (for a full list refer to the :webroot:`API specification <swagger/index.html>`). The service is accessed via a :webroot:`REST API <swagger/index.html>` and will require some software development expertise and set-up in order to get started. Currently, images can only be fetched from and returned to Amazon S3 Storage Buckets, although support for other storage providers and `signed-urls <https://docs.aws.amazon.com/AmazonS3/latest/dev//ShareObjectPreSignedURL.html>`_ is under development.


How to Use Pixelshift
---------------------

Below is a summary of steps required in order to start using the service. Click on any of the headings to be taken to a more detailed description.

**1.** :webroot:`Generate API Keys <documentation/api/introduction.html#authorization>` for signing your requests. This is done via your :webroot:`Dashboard <Dashboard/ApiAccess>`.

**2.** :webroot:`Grant access to your images in AWS Storage <documentation/setup/awsSetUp.html>` by setting up an IAM User and attaching an Inline Policy to it.

**3.** :webroot:`Create an API Client <documentation/api/introduction.html#creating-an-api-client>` by cloning one of `our repositories <https://github.com/pixel-shift>`_, generating one with `autorest <https://github.com/Azure/autorest>`_ against our :webroot:`Swagger/OpenAPI document <swagger/v1/swagger.json>` or writing your own.

**4.** :webroot:`Define your Processing Tasks <documentation/api/introduction.html#defining-processing-tasks>` as *Transform Graphs*

**5.** :webroot:`Submit a Batch <documentation/api/introduction.html#submitting-a-batch>` of Processing Tasks via your API Client.
