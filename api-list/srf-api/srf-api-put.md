# Service Request Form API - PUT

### <span style="background-color: #5493dc; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">PUT</span> **Service Request Form**

```text
/api/v1/serviceRequest/form/:serviceRequestID
```

This API endpoint is used to replace an existing service
request, and is invoked via the HTTP `PUT` method.

Note that the entire contents of the service request are
replaced with the new values. As such, your application
should always supply every field you do not wish to be
converted into a blank value. This operation essentially
represents a complete replacement of all values, rather
than a partial update on a field-by-field basis.

#### Request

##### Path Parameters

This endpoint accepts the following parameters in its
URL path:

| Path Parameter | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| :serviceRequestID | Yes | Integer | The value that uniquely identifies the service request to update. |

##### Body Parameters

This endpoint accepts the same body parameters as the
corresponding SRF creation endpoint (accessible via
an HTTP `POST` operation).

##### Example JSON Request

API requests to this endpoint will be identical in
structure to those sent to the SRF creation endpoint
(accessible via an HTTP `POST` operation).

#### Response

##### Expected HTTP Response Code

When operating normally, this API endpoint will return
an HTTP response code of `200` ("OK").

##### Sample JSON Response

API responses returned by this endpoint will be identical
in structure to those sent to the SRF creation endpoint
(accessible via an HTTP `POST` operation).