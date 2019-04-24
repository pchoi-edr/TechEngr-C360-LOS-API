# Service Request Form API - POST

### <span style="background-color: #ebb747; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">POST</span> **Service Request Form**

```text
/api/v1/serviceRequest/form
```

This endpoint is used to create a new draft service request, and
is invoked via the HTTP `POST` method.

#### Request

##### Path Parameters

This endpoint does not accept any path parameters in its URL.

##### Body Parameters

The API request body conforms to the standard API request
format (_i.e._ a `meta` and a `data` element), per the
[API Data Structures](../request-response-structure.md)
section of this document.

The request's top-level `data` element should contain the
following elements, each of which must conform to the
requirements described above.

* `transaction`

* `collaterals`

The contents of these elements collectively define the contents of
the service request created by a successful invocation of this
endpoint.

If the specified service request is successfully created by this
endpoint, then the API response's `data` element will contain
a `serviceRequestID` element, which will be an integer that
uniquely identifies the newly created service request. 

##### Example JSON Request

A request to create a service request might look like the following
in general structure (replacing example values with values appropriate
to your specific application, per the JSON schema returned by the
SRF Fields API):

```json
{
  "meta": {
    "cabinet": "Example Cabinet Name",
    "currency": "USD",
    "requestedBy": "creator@example.com"
  },
  "data": {
    "transaction": {
      "exampleTransactionField": "Example Value"
    },
    "collaterals": [
      {
        "exampleCollateralField": "Example Value",
        "services": [
          {
            "siteType": "Appraisal"
          },
          {
            "siteType": "Environmental"
          }
        ]
      }
    ]
  }
}
```

#### Response

##### Expected HTTP Response Code

When operating normally, this API endpoint will return
an HTTP response code of `201` ("Created").

##### Example JSON Response

A successful API request to create a new service request will
yield an API response similar to the following:

```json
{
    "meta": {
        "date": "2018-04-28T12:23:23Z",
        "function": "create",
        "responseCode": 201,
        "responseID": "3b811014-7984-11e8-adc0-fa7ae01bbebc",
        "success": true,
        "warnings": []
    },
    "data": {
        "serviceRequestID": 1234567
    }
}
```

The `serviceRequestID` element contains a value that uniquely
identifies the newly created service request. Your application
should record this value, since any subsequent API requests you
may issue to modify the new service request must use this
value to identify which service request to update.