# SRF Download Assets API

## <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span> **Service Request Details**

```text
/v1/api/download/assets/:serviceRequestId
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
```
