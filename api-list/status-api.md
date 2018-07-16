# SRF Status API

This API provides basic identifying information about
service requests, their component collateral properties,
and the services to be performed on those collateral
properties.

## Available Endpoints

The following API endpoints are available as part of this
subsystem:

### <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span> **Service Request Details**

```text
/api/v1/status/:serviceRequestID
```

This API endpoint is accessible via the HTTP `GET` method.

#### Request

##### Path Parameters

The following URL path parameters are supported:

| Path Parameter | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| :serviceRequestID | Yes | Integer | The unique service request ID. |

##### Query String Parameters

The following URL query string parameters are supported:

| Parameter | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| locationID | No | Integer | A unique location ID. |
| serviceID | No | Integer | A unique service ID. |

The `locationID` parameter can be used by itself to retrieve
all service-related data for the specified location. If a
location ID is specified, then the location must belong to
the specified service request.

If a `serviceID` parameter is supplied, then only information
related to that individual service will be returned.

If a `locationID` and a `serviceID` parameter are both supplied
together, then the specified service must belong to the
specified location.

Example usages follow, where `123` represents a service request
ID, `456` represents a location ID, and `789` represents a
service ID:

```text
/api/v1/status/123
```

```text
/api/v1/status/123?locationID=456
```

```text
/api/v1/status/123?serviceID=789
```

```text
/api/v1/status/123?locationID=456&serviceID=789
```

#### Response

##### Example JSON Response

The following represents an example JSON response. In this
example, any value surrounded by angled brackets would be
replaced by an unique identifier in an actual response. Thus,
`<serviceRequestId>` would be an actual service request ID.

```javascript
{
  "meta": {
    "date": "2018-04-28T12:23:23Z",
    "function": "get",
    "responseCode": 200,
    "responseID": "da288fe6-7991-11e8-adc0-fa7ae01bbebc",
    "success": true
  },
  "data": {
    "<serviceRequestID>": [
        {
          "locationID": "<locationID>",
          "address": [
            {
              "street_address": "123 street",
              "optional_address": "Suite #1",
              "city": "city",
              "state": "state",
              "stateAbbreviated": "stateAbbreviated",
              "zip": "zip",
              "country": "country",
              "countryAbbreviated": "countryAbbreviated"
            }
          ],
          "status": "Pending",
          "services": [
            {
              "serviceID": "<serviceID>",
              "jobNumber": "11-1111111",
              "status": "Pending",
              "fee": null,
              "startDate": "12-13-2018 10:10:10",
              "dueDate": "12-13-2018T10:10:10Z",
              "completeDate": "12-13-2018T10:10:10Z",
              "createdAt": "2018-02-28T08:34:16Z",
              "updatedAt": ""
            }
          ]
        },
        {
          "locationID": "<locationID>",
          "address": [
            {
              "street_address": "123 street",
              "optional_address": "Suite #1",
              "city": "city",
              "state": "state",
              "stateAbbreviated": "stateAbbreviated",
              "zip": "zip",
              "country": "country",
              "countryAbbreviated": "countryAbbreviated"
            }
          ],
          "status": "Hold",
          "services": [
            {
              "serviceID": "<serviceID>",
              "jobNumber": "11-1111111",
              "status": "Hold",
              "fee": null,
              "startDate": "12-13-2018T10:10:10Z",
              "dueDate": "12-13-2018T10:10:10Z",
              "completeDate": "12-13-2018T10:10:10Z"
            }
          ]
      }
    ]
  }
}
```
