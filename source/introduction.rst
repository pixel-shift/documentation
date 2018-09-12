============
Introduction
============

About
=====

Pixelshift.io is a cloud-based service for processing large numbers of images at scale. It has been written from the ground up with this sole objective, and it is the most efficient and lowest-cost service of its type. Whether you need to process hundreds, or hundreds of thousands of images, our Microservice architecture running on Kubernetes rapidly adapts to handle any size of workload.   

The service is accessed via a :webroot:`REST API <swagger/index.html>` and will require some software development expertise and set-up in order to get started. Images can only be fetched from and returned to Amazon S3 Storage Buckets currently, though support for Azure and Google Cloud Storage is under development.

Overview
========

Getting up and runnn

**1. Set Up**
A one-time series of steps to generate your API keys and grant access to your storage locations.

**2. Authorize**
Processing requests must be authorized by OAUTH

**3. Create a Batch Process Task**
Tasks consist of ____ and an array of *Image Urls* and *Image Transforms* to be performed.

A basic example is shown below:



batch processing requests can be sent to our API and your images will be uploaded, processed and downloaded 
Currently, it can read from and write to Amazon Web Services storage buckets 
