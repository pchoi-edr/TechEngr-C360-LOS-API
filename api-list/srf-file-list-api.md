# SRF File List API

This API provides a list of downloadable files associated
with a given service request. The available files can be
downloaded using the [SRF Download API](srf-file-download-api.md).

## Available Endpoints

The following endpoints are made available by this API: 

### <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span> **Service Request Details**

```text
/api/v1/serviceRequest/files/list/:serviceRequestID
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
    "files": [
      {
        "uploadID": 1234567,
        "locationID": 1234567,
        "filename": "instructions-for-appraisal.txt",
        "type": "text/plain",
        "size": 657284,
        "uploadedAt": "2015-05-23T15:23:06Z",
        "uploadedBy": "user@example.com",
        "status": "Final Report",
        "documentType": "Instruction Letter",
        "serviceGroups": [
          "Valuation"
        ],
        "serviceTypes": [
          {
            "serviceType": "Appraisal",
            "name": "External Appraisal Report",
            "serviceGroup": "Valuation"
          }
        ],
        "attributes": [
          {
            "name": "Prepared By",
            "value": "Mr. Example"
          },
          {
            "name": "Report Date",
            "value": "2018-09-05"
          },
          {
            "name": "Report Title",
            "value": "Special Instructions for Appraisal"
          }
        ]
      }
    ]
  }
}
```

#### Response Structure

Each entry in the _files_ array represents a file that has been
uploaded to a service request and associated with one of its
locations. Most fields follow the naming conventions and data
structure used by Collateral360's File Manager screen, but the
following fields require special explication:

  * The **filename** field represents the original filename of
    the uploaded document.

  * The **type** field represents the MIME type of the file. This
    should conform to section 3.1.1.1 of RFC 7231.
    
  * The **size** field represents the size of the file, in eight-bit
    bytes (_i.e._ in octets). Client applications may wish to convert
    this into a more readily human-readable form for display, typically
    one of the following:
    
      * Kilobytes or kibibytes.
      * Megabytes or mebibytes.
    