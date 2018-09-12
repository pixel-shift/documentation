============
Introduction
============

About
=====

Pixelshift.io is a cloud-based service for processing large numbers of images at scale. It has been written from the ground up with this sole objective, and it is the most efficient and lowest-cost service of its type. Whether you need to process hundreds, or hundreds of thousands of images, our Microservice architecture running on Kubernetes rapidly adapts to handle any size of workload.   

Supported operations include resizing, cropping, re-colouring and swapping file-types (for a full list refer to the :webroot:`API specification <swagger/index.html>`). The service is accessed via a :webroot:`REST API <swagger/index.html>` and will require some software development expertise and set-up in order to get started. Currently, images can only be fetched from and returned to Amazon S3 Storage Buckets, though support for Azure and Google Cloud Storage is under development.

Overview
========

The following list outlines the steps you will need to follow in order to start using the service. Click on any of the headings to be taken to a more detailed description.

**1. Generate API Keys** for signing your requests. This is done via your Dashboard.

**2. Grant access to your images** by setting up an IAM User and attaching an Inline Policy to it.

**3. Create a Batch Process Task**
Tasks consist of ____ and an array of *Image Urls* and *Image Transforms* to be performed.

A basic example is shown below:
