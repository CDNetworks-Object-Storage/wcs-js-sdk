## Introduction
1. [Source Code](https://github.com/CDNetworks-Object-Storage/wcs-js-sdk/tree/main/src)
2. [demo&example](https://github.com/CDNetworks-Object-Storage/wcs-js-sdk/tree/main/test/demo1)
3. [demo user guide](https://github.com/CDNetworks-Object-Storage/wcs-js-sdk/blob/main/demo-user%20guide.md)

## Prerequisites
- Cloud Storage is activated.
- The AccessKey and SecretKey are created
- System: Above H5

Notes:
Token  generation is not support in Wcs-JavaScript-SDK. We suggest you set up a server for token generation by yourself. 

## Install
#### 1. Include
```
<script type="text/javascript" src="/dist/wcs.min.js"></script>
```
Using the script tag to include an external JavaScript file, then a global object named wcs will be created.

#### 2. Install npm
```
npm install wcs-js-sdk
```

## Iniatialization
- Upload can be controlled by object named ```uploadObj```, which can help to upload, callback, stop, etc.
- SDK determines whether to use direct upload or multipart upload according to the file size and block size ```BLOCK_SIZE```.    1) If the file size is greater than ```BLOCK_SIZE```: multipart upload; 2) Otherwise: direct upload

### Import:
```
1. import * as wangsu from 'wcs-js-sdk'
2. import { wcsUpload } from 'wcs-js-sdk'         //call wcsUpload()  
3. import * as wangsu from 'wcs-js-sdk'           //call wangsu.wcsUpload()
```
### How to use
```
var uploadObj = wangsu.wcsUpload(file, token, uploadUrl, extraConfig);
```
### Parameters:
```
file                            // The file need to be uploaded
token                           // Token required by the backend server
uploadUrl                       // Upload URL of Ojbect Storage
extraConfig={
    timeout: 0,                 //Timeout, default value is 0, it will retry upload when timeout
    concurrentRequestLimit:3,   //Concurrency, default value is 3. Notes: The browsers have limitation in the request resources for the connection. For example, Chrome's request limitation is 6, so there will be a situation where if you write 10 concurrently, but only 6 are actually uploaded.
    retryCount:0                //Retry upload, default value is 0.
}

```

### Upload
```
uploadObj.putFile();

```

### Callback the uploading status
```
uploadObj.uploadProgress = function (progress) {}
- progress format
{
    total:{
        loaded: ?,      //Loaded size
        size: ?,        //Total file size 
        percent: ?      //ratio
    },
    chunks:[            //Block info, it is in array format 
        {loaded: ?, size: ?, percent: ?},
        {loaded: ?, size: ?, percent: ?}
    ]
}

```

### Callback Errors
```
uploadObj.onError = function (error) {}
- error format
{
    code: ?,  // Error code, please note that there isn't code in uploadObj.stop() and timeout retry
    message: "",  //Error info
    isRequestError: true //Is it a request error? That is, after normal upload, the server returns an error. This is a normal error, and there is no need to re-upload.
}

```

### Finish Callback
```
uploadObj.onComplete = function(res){}
- res format
{
    data: jsonObj/String   //The result returned by the server. Note: If the code string is returned directly, the JSON object is returned if the chunk size is exceeded and multipart uploads is used.
}

```

### Stop
```
uploadObj.stop();


```

[Demo](https://github.com/CDNetworks-Object-Storage/wcs-js-sdk/tree/main/test/demo1)
