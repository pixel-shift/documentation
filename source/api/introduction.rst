==========
API Access
==========

Overview
========

The first step is to obtain a valid *Bearer Token* using your API Keys as described below. The token that you receive is then used by one of our API Clients (or your own) in order to send *Batches* of image processing tasks to the API. Each *Batch* consists of a collection of *Transform Graphs*, and each  *Transform Graph* describes the source, operations and destination(s) for an image processing task. 

Getting Authorized
==================

Access to the Pixelshift API is secured via Oauth Bearer Tokens, and all requests require a valid Token to be attached. The steps to accquire a Bearer Token are outlined below.

**1. Generate API Public/Private Key Pair**

Visit your :webroot:`Pixelshift Dashboard <Dashboard/ApiAccess>` and hit 'Generate New Api Key'. Store both keys somewhere safe (please note that the Private Key is only available when a new key is generated though a new Private Key can be generated at any time).

----

**2. Accquire an OAuth Bearer Token**

Using your technology of choice, make a POST to http://www.pixelshift.io/connect/token with a POST body of `{ grant_type : "client_credentials"}` and your API Keys Base64 Encoded in the Authorization Header. For example, using Node.js this would look like:

.. code-block:: javascript
    :linenos:

    const https = require('https');
    const querystring = require('querystring');
    const postData = querystring.stringify({ grant_type: "client_credentials" });
    const clientId = "XXXXXXXXX";
    const clientSecret = "XXXXXXXXXXX";;
    const credentials = Buffer.from(clientId + ':' + clientSecret).toString('base64');
    
    var options = {
        hostname: 'www.pixelshift.io',
        path: '/connect/token',
        method: 'POST',
        headers: {
            'Content-Type': 'application/x-www-form-urlencoded',
            'Content-Length': postData.length,
            'Authorization' : 'Basic ' + credentials
        }
    };
    
    const req = https.request(options, (res) => {
        let data = '';
        res.on('data', d => {
            data += d;
        });
        res.on('end', () => {
            const response = JSON.parse(data);
            console.log(response.access_token);
        });
    });
    req.write(postData);
    req.end();



Initializing an API Client
==========================

The details of this step depend on your chosen language and implementation. As an example, the Pixelshift node.js client is intiazlied as follows (using the token obtained from the previous step):

.. code-block:: javascript
    :linenos:

    const creds = new TokenCredentials(token);
    const api = new PixelshiftApi(creds, "https://www.pixelshift.io");


Creating Transform Graphs
=========================

Each processing task within a *Batch* is described as a *Transform Graph*. To be valid, each *Transform Graph* must consist of the following components:

**1. A single StorageSource**, giving the location of the original image to be processed

**2. One or more Transforms**, describing the processing tasks to be performed

**3. One or more StorageSinks** giving the location(s) where the results of the processing tasks should be stored

Other requirements are as follows:

* Every *StorageSink* must be preceeded by a single *ImageFormat* node that defines the file format for the final result (e.g. jpeg or png)
* The number of *StorageSinks* per *Transform Graph* is limited to 5 

The sample below shows how to use the the Pixelshift Node.js API Client to build a simple *Transform Graph* to resize an image:

.. code-block:: javascript
    :linenos:

    //create StorageSource
    const storageSource = new PixelshiftApiModels.StorageSourceS3();
    storageSource.sourceBucket = "mysourcebucket";
    storageSource.sourceKey = "source-image.jpg";

    //create an ImageResizeMax transform node
    const resize = new PixelshiftApiModels.ImageResizeMax();
    resize.width = 500;
    resize.height = 500;
    
    //define output file format
    const jpeg = new PixelshiftApiModels.ImageFormatJpeg();
    jpeg.quality = 60;

    //define destination
    const storageSink = new PixelshiftApiModels.StorageSinkS3();
    storageSink.allowOverwrite = true;
    storageSink.destinationBucket = "destbucket";
    storageSink.destinationKey = "processed-image.jpg";

    //build transform graph
    const graph = new PixelshiftApiModels.TransformGraph();
    graph.transforms = [storageSource, resize, jpeg, storageSink];


Submitting a Batch
==================

*Transform Graphs* are attached to a *Batch*, which is then submitted for processing. Using Node.js again as an example, this is achieved as follows:

.. code-block:: javascript
    :linenos:
    :emphasize-lines: 4,5

    const batch = new PixelshiftApiModels.Batch();
    batch.items = [graph];

    //Note: this is only required for Node.js clients
    addTypeDiscriminatorsToBatch(batch);
    
    const apiResponsePromise = api.processImageBatch({ batch });
    let apiResponse;
    try{
        apiResponse = await apiResponsePromise;
    }catch(err){
        console.log(err);
    }
    
    console.log(JSON.stringify(apiResponse, null, 2));


**Please Note:** Line 5 in the above code is only required for Node.js clients.

The response will indicate success or, if unsuccessful, the reason that the submission has failed.