# SRF Download Assets API

This API provides a list of downloadable assets associated
with a given service request. The available files can be
downloaded using the [SRF Download API](srf-download-api.md).

## Available Endpoints

The following endpoints are made available by this API: 

### <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span> **Service Request Details**

```text
/api/v1/download/assets/:serviceRequestId
```

#### Request

##### Path Parameters

| Path Parameter | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| :serviceRequestID | Integer | Yes | A service request ID. |

##### Body Parameters

This endpoint does not accept and HTTP body parameters.

#### Response

##### Expected HTTP Response Code

When operating normally, this API endpoint will return
an HTTP response code of `200` ("OK").

##### Example JSON Response

```json
{
  "meta": {
    "date": "2018-04-28 12:23:23",
    "function": "get",
    "responseCode": 200,
    "responseID": "e3733640-789c-11e8-9dfc-81c439846400",
    "success": true,
    "warnings": []
  },
  "data": {
    "assets": [
      {
        "uploadID": 1234567,
        "locationID": 1234567,
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
        "locationID": 1234567,
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
  }
}
```
