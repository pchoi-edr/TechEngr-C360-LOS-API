# SRF Download API

## <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span> **Service Request Details**

```text
/v1/api/download/assets/:serviceRequestId?locationID=1234567&serviceID=1234567
```

```text
/v1/api/download/assets/:serviceRequestId?uploadId=1234567
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
    "download": "{URI path of download file}"
}
```
