# SRF Download API

Services performed on collateral properties typically result
in documentation (_e.g._ reports, legal paperwork, affidavits,
_etc._). These documents are ordinarily uploaded to--or
otherwise made available through--the Collateral 360 system.

This API is responsible for downloading the documents that
are associated with a service performed on a collateral
property.

## Available Endpoints

The following endpoints are available as part of this API:

### <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span> **Service Request Details**

```text
/api/v1/download/:serviceRequestId?uploadId=1234567
```

This endpoint is accessible via the HTTP `GET` method. A
successful invocation will return an HTTP redirection
response that points to the file to download.

The download will be performed automatically in compatible
user agents. Depending on the architecture of your client
application, this may occur automatically, or you may have
to examine the response and retrieve the downloadable file
in a separate HTTP `GET` operation.

#### Request

##### Path Parameters

| Path Parameter | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| :serviceRequestID | Integer | Yes | The ID of the service request. |

##### Body Parameters

This endpoint does not accept any HTTP body parameters.

##### Query String Parameters

| Parameter | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| uploadID | Integer | Yes | The ID of an uploaded file. |

Note that the upload ID must represent a file that was uploaded
for a service performed on one of the collateral properties
in the specified service request. If the upload ID exists
but does not match the specified service request, this will
be considered an error condition.

#### Response

##### Expected HTTP Response Code

Unlike most other responses from the LOS API, a successful
response will be sent with an HTTP response status code of
`303` (indicating a redirection where the new URL must be
retrieved using the HTTP `GET` method).

#### Example JSON Response

In the following example, the value `<PATH_TO_FILE>` will
be replaced in an actual response by a URL to the requested
file. If your client application does not honor the HTTP
redirection response status code returned by this endpoint,
then you can use this URL to download the file in a separate
HTTP `GET` request.

```json
{
  "meta": {
    "date": "2018-04-28T12:23:23Z",
    "function": "get",
    "responseCode": 303,
    "responseID": "a0345fe4-7a2d-11e8-adc0-fa7ae01bbebc",
    "success": true,
    "warnings": []
  },
  "data": {
    "download": "<PATH_TO_FILE>"
  }
}
```
