
============
Introduction
============

About
-----

Pixelshift.io is a cloud-based service for processing large numbers of images at scale, and is the most efficient and lowest-cost service of its type. Whether you need to process hundreds, or hundreds of thousands of images, our Microservice architecture running on Kubernetes rapidly adapts to handle any size of workload.   

Supported operations include resizing, cropping, re-colouring and changing file-types (for a full list refer to the :webroot:`API specification <swagger/index.html>`). The service is accessed via a :webroot:`REST API <swagger/index.html>`.

Images can be fetched and returned to you via two methods:

**1. Raw URLs:** Any valid URL can be used to GET and PUT your images. Typically, URLs will be pre-signed for a particular storage provider such as Azure, Amazon S3 or Google Cloud.

**2. Amazon IAM User:** a special user created to grant access to specific Amazon S3 Storage Buckets.


How to Use Pixelshift
---------------------

Below is a brief summary of how to use the service. Click on any of the headings to be taken to a more detailed description.

**1.** :webroot:`Generate API Keys <documentation/api/introduction.html#authorization>` for signing your requests. This is done via your :webroot:`Dashboard <Dashboard/ApiAccess>`.

**2.** :webroot:`Create an API Client <documentation/api/introduction.html#creating-an-api-client>` by cloning one of `our repositories <https://github.com/pixel-shift>`_, generating one with `autorest <https://github.com/Azure/autorest>`_ against our :webroot:`Swagger/OpenAPI document <swagger/v1/swagger.json>` or writing your own.

**3.** If your images are in Amazon S3 Storage and wish to use an IAM User, create one and attach an Inline Policy to it to :webroot:`Grant access to your images in AWS Storage <documentation/setup/awsSetUp.html>`.  *(If you are using raw URLs you can skip this step.)*

**4.** :webroot:`Define your Processing Tasks <documentation/api/introduction.html#defining-processing-tasks>` as *Transform Graphs* or raw JSON objects.

**5.** :webroot:`Submit a Batch <documentation/api/introduction.html#submitting-a-batch>` of Processing Tasks via your API Client.
