# SRF Download API

## <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span> **Service Request Details**

```text
/api/v1/download/:serviceRequestId?locationID=1234567&serviceID=1234567
```

```text
/api/v1/download/:serviceRequestId?uploadId=1234567
```

### Request

#### Path Parameters

| Path Parameter | Type | Description |
| :--- | :--- | :--- |
| serivceRequestID | Int | Service Request ID |

#### GET Parameters

Query parameters can be either a combination of locationID & serviceID or uploadID only.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| locationID | Int | Location ID |
| serviceID | Int | Service ID |

OR

| Parameter | Type | Description |
| :--- | :--- | :--- |
| uploadID | Int | Upload ID |

### Response

> Browser will be redirected and download will automatically commence.

```javascript
{
    "meta": {
        "responseCode": 200,
        "responseID": "e3733640-789c-11e8-9dfc-81c439846400",
        "success": true,
        "date": "2018-04-28 12:23:23",
        "function": "get"
    },
    "data": {
        "download": "{URI path of download file}"
    }
}
```
