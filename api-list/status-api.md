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
/api/v1/serviceRequest/status/:serviceRequestID
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
/api/v1/serviceRequest/status/123
```

```text
/api/v1/serviceRequest/status/123?locationID=456
```

```text
/api/v1/serviceRequest/status/123?serviceID=789
```

```text
/api/v1/serviceRequest/status/123?locationID=456&serviceID=789
```

#### Response

##### Expected HTTP Response Code

When operating normally, this API endpoint will return
an HTTP response code of `200` ("OK").

##### Example JSON Response

The following represents an example JSON response for a
service request that is no longer in the draft status.
In this example, any value surrounded by angled brackets
would be replaced by a unique identifier in an actual
response. Thus, `<serviceRequestID>` would be an actual
service request ID.

Note that every service request will contain one or more
locations, and each location can contain zero or more
services. (If your company has custom workflow rules
implemented for its service request form, then your
data may conform to stricter requirements.)

```json
{
  "meta": {
    "date": "2018-04-28T12:23:23Z",
    "function": "get",
    "responseCode": 200,
    "responseID": "da288fe6-7991-11e8-adc0-fa7ae01bbebc",
    "success": true,
    "warnings": []
  },
  "data": {
    "serviceRequestID": <serviceRequestId>,
    "loanID": <loanID>,
    "draft": false,
    "locations": [
      {
        "locationID": <locationID>,
        "complete": false,
        "address": {
          "street1": "1600 Pennsylvania Avenue NW",
          "street2": "Oval Office",
          "city": "Washington",
          "state": "DC",
          "postalCode": "20500",
          "country": "US",
          "latitude": 38.879146,
          "longitude": -76.981882
        },
        "services": [
          {
            "serviceType": "PhaseI",
            "name": "Phase I Environmental Site Assessment",
            "serviceGroup": "Environmental",
            "jobNumber": "<jobNumber>",
            "status": "New",
            "fee": 0,
            "primaryAssignee": "user1@example.com",
            "secondaryAssignees": [
                "user2@example.com",
                "user3@example.com"
            ],
            "startDate": "2018-12-13T08:10:10Z",
            "dueDate": "2018T-12-1615:10:10Z",
            "completionDate": "2018-12-14T10:10:10Z",
            "created": "2018-12-10T08:34:16Z",
            "updated": null
          }
        ]
      }
    ],
    "created": "2018-12-10T08:34:16Z"
  }
}
```

For each location:

  * The `complete` field will be `true` if the location
    has been marked as complete, or `false` if it is
    marked as incomplete.
    
  * Most values in the `address` section will be strings;
    if a value is missing, it will be an empty string.
    However, the geographical coördinates will be floating
    point numbers, or `null` if no coördinates are present.
    
For each service:

  * The `serviceType` is the semi-human-readable code
    used to identify the yupe of service performed.
    
  * The `name` is the human-readable name of the service.
  
  * the `serviceGroup` is the broad category under which
    the service is organized:. Common values include the
    following (though this list may be appended to over
    time):
    
    * `Environmental`
    * `Valuation`
    * `Flood`
    * `Inspection`
    * `Construction`
    * `Additional Services`
    
  * If no `primaryAssignee` exists, it will be `null`.
   
  * If no `fee` value is present, it will be `null`.
    
  * If any date is missing, it will be `null`.
  
The data structure of an API response that represents
a draft service request will differ from the foregoing
example. Instead, it will look like the following:

```json
{
  "meta": {
    "date": "2018-04-28T12:23:23Z",
    "function": "get",
    "responseCode": 200,
    "responseID": "d65e6997-d73d-46e5-97f0-f12c989850f8",
    "success": true,
    "warnings": []
  },
  "data": {
    "serviceRequestID": <serviceRequestId>,
    "loanID": null,
    "draft": true,
    "locations": [
      {
        "address": {
          "street1": "1600 Pennsylvania Avenue NW",
          "street2": "Oval Office",
          "city": "Washington",
          "state": "DC",
          "postalCode": "20500",
          "country": "US",
          "latitude": 38.879146,
          "longitude": -76.981882
        },
        "services": [
          {
            "serviceType": "PhaseI",
            "name": "Phase I Environmental Site Assessment",
            "serviceGroup": "Environmental",
          }
        ]
      }
    ],
    "created": "2018-12-10T08:34:16Z"
  }
}
```

The major differences are as follow:

  * No loan ID will be assigned yet (`loanID` will be `null`).
  
  * The `draft` field will be `true`.
  
  * Locations will not have their location IDs assigned
    yet (`locationID` will be `null`).
  
  * Locations will not have any `complete` status.
  
  * Each service will only have its basic identifying
    information (indicating what type of service it is).
