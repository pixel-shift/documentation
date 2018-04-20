========
Overview
========

About
=====

Pixelshift.io is a service optimised for processing large numbers of images at scale. It has been written from the ground up with this sole objective, and it is the fastest and lowest-cost service of its type.


Overview
========

There are only a few parts to this process:

**1. Set Up**
A one-time series of steps to generate your API keys and grant access to your storage locations.

**2. Authorize**
Processing requests must be authorized by OAUTH

**3. Create a Batch Process Task**
Tasks consist of ____ and an array of *Image Urls* and *Image Transforms* to be performed.

A basic example is shown below:

.. jsonschema::

    {
        "title": "Example Batch Process Task",
        "id": "http://this.better.be.a.regular.domain",
        "type": "object",

        "properties":{
            "name": { "type": "string"}
        }
    }

batch processing requests can be sent to our API and your images will be uploaded, processed and downloaded 
Currently, it can read from and write to Amazon Web Services storage buckets 
