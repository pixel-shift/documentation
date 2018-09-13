============
Making Requests
============

Overview
========

Access to the Pixelshift API is secured via Oauth Bearer Tokens, and all requests require that a valid Token is attached. The general steps to accquire a Bearer Token and use it are outline below.

**1. Generate API Public/Private Key Pair**

To do this, visit your :webroot:`Pixelshift Dashboard <Dashboard/ApiAccess>` and hit 'Gneerate New Api Key'. Store both keys somewhere safe. **Note**: the Private Key is only available when a new key is generated (though a new Private Key can be generated at any time).

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
    ​
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
    ​
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
