# SRF Download Assets API

## <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span> **Service Request Details**

```text
/api/v1/download/assets/:serviceRequestId
```

### Request

#### Path Parameters

| Path Parameter | Type | Description |
| :--- | :--- | :--- |
| serivceRequestID | Int | Service Request ID |

### Response

> Browser will be redirected and download will automatically commence.

```javascript
[
    "meta": {
        "responseCode": 200,
        "responseID": "e3733640-789c-11e8-9dfc-81c439846400",
        "success": true,
        "date": "2018-04-28 12:23:23",
        "function": "get"
    },
    "data": [
        {
            "uploadID": 1234567,
            "LocationID": 1234567,
            "fileName": "example-filename.txt",
            "fileType": "text/plain",
            "fileLocation": "/path/to/file",
            "fileSize": "1.2mb",
            "token": "example",
            "typeID": 1234567,
            "createdAt": "2015-05-23",
            "updatedAt": "2015-05-23"
        },
        {
            "uploadID": 1234567,
            "LocationID": 1234567,
            "fileName": "example-filename.txt",
            "fileType": "text/plain",
            "fileLocation": "/path/to/file",
            "fileSize": "1.2mb",
            "token": "example",
            "typeID": 1234567,
            "createdAt": "2015-05-23",
            "updatedAt": "2015-05-23"
        }
    ]
]
```
