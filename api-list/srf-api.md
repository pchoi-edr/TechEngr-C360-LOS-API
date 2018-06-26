# SRF API

The SRF API is used to create or modify a draft service request.
Within Collateral 360, draft service requests are considered
works-in-progress, and therefore can be saved with incomplete
information. They are designed to record the user's work during
the time period when data about a loan or its collateral properties
are still being acquired, or when decisions are still being made
regarding the services to perform for each collateral property.

The fields accepted by this API are defined by the JSON schema
returned by the [SRF Fields API](srf-fields-api.md).

The API request format is largely identical for both the creation
of new service requests and the modification of existing ones.
The general format is described in the following sections. Any
differences in syntax or usage between these two use cases will
be noted.

## API Request Structure

API requests issued to create or modify a service request all have
the same high-level structure. The following elements will be
expected within the API request's top-level `data` element:

| Data Field | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| meta | Yes | object | Metadata related to the service request. |
| transactional | Yes | object | General data fields that describe the service request. |
| collaterals | Yes | array | An array where each element contains the data fields that describe a single real property used as collateral. |

### Metadata Field Definitions

The following fields should be included in the API request
data's top-level `meta` element:

| Data Field | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| cabinet | Yes | string | The name of the cabinet that will contain the draft SRF. |
| currency | Yes | string | A three-letter ISO 4217 currency code. |
| createdBy | Yes | email | The email address of the SRF creator. |

Note that, depending on your configuration options in Collateral 
360, draft SRFs may only be visible to the user who created them.
In this case, the `createdBy` field defines this user.

Unless otherwise noted, all monetary amounts in the request will be
denominated in the specified currency.

### Transactional Field Definitions

The values in the API request's `transactional` element will
vary by client. Each value represents a data field that describes
the overall service request independently of any collateral (such
as a loan principal amount).

The fields that can be included in this section are defined in the
JSON schema returned by the SRf Fields API.

### Collateral Field Definitions

The API request's `collaterals` element consists of an array where
each element represents an individual real property used to
collateralize a loan. As such, the fields in this section can
be repeated between each element.

Similarly to the `transactional` element's contents, the fields in
each element of the `collaterals` array are defined in the JSON 
schema returned by the SRF Fields API. However, one additional field
is present:

| Data Field | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| services |yes| array | An array of services to perform on the collateral property. |

Each element in the `services` array represents a service to perform on
a collateral property, such as the following examples (your set of services
may be different):

* Phase I Environmental Report

* Property Appraisal Inspection

Each service is associated with a _feature_, which represents the broad
category of services it belongs to. Typical features may include
environmental services, appraisal services, construction services, _etc._
In the event that two services share the same human-readable name, their
associated feature can be used to tell them apart. As such, your
application may wish to segregate or group services according to their
associated feature.

Each element in the `services` array should have the following values,
which are defined in the JSON schema returned by the SRF Fields API:

| Data Field | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| siteType | Yes | string | The service's site type (used as its unique identifier). |
| displayName | Yes | string | The displayed name of the service. |
| featureID | Yes | array | The service's feature ID. |
| featureName | Yes | array | The displayed name associated with the service's feature ID. |

<div style="page-break-after: always;"></div>

## SRF API Endpoints

The following endpoints are supported by the SRf API:

## <span style="background-color: #ebb747; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">POST</span> **Service Request Form**

```text
/api/v1/serviceRequestForm
```

### Request

#### Body Parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| meta | object | Meta Data for the data being submitted |
| serviceRequestData | object | Data package |

##### Parameters for `meta` object

|  Parameter | Type | Description |
| :--- | :--- | :--- |
| dataType | string | Options: json or xml |

##### Parameters for `serviceRequestData` object

|  Parameter | Type | Description |
| :--- | :--- | :--- |
| fields | string | Accepts: JSON, Stringified JSON or XML |

#### Sample JSON Submission

```javascript
{
  "meta": {
    "dataType": "json"
  },
  "serviceRequestData": {
    "meta": {
      "cabinet": "string",
      "currency": "USD",
      "createdBy": "email"
    },
    "transactional": {
      "Transactional Fields as Objects"
    },
    "collaterals": [
      {
        "Collaterals as Array of Objects",
        "services": [
          "Array of Services..."
        ]
      }
    ]
  }
}
```

#### Sample XML Submission

```javascript
{
    "meta": {
        "dataType": "xml"
    },
    "serviceRequestData": "<?xml version=\"1.0\" encoding=\"UTF-8\"?>
      <serviceRequestForm>
        <meta>
          <cabinet />
          <currency />
          <createdBy />
        </meta>
        <transactional />
        <collaterals>
          <collateral />
        </collaterals>
      </serviceRequestForm>"
}
```

### Response

```javascript
{
    "meta": {
        "responseCode": 201,
        "date": "2018-04-28 12:23:23",
        "function": "create"
    },
    "data": {
        "serviceRequestID": 1234567,
        "loanID": null,
        "locations": []
    }
}
```

### <span style="background-color: #5493dc; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">PUT</span> **Service Request Form**

```text
/api/v1/serviceRequestForm/:serviceRequestID
```

### Request

#### Path Parameters

| Path Parameter | Type | Description |
| :--- | :--- | :--- |
| serviceRequestID | Int | Service Request ID |

#### Body Parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| meta | object | Meta Data for the data being submitted |
| serviceRequestData | object | Data package |

##### Parameters for `meta` object

|  Parameter | Type | Description |
| :--- | :--- | :--- |
| dataType | string | Options: json or xml |

##### Parameters for `serviceRequestData` object

|  Parameter | Type | Description |
| :--- | :--- | :--- |
| fields | string | Accepts: JSON, Stringified JSON or XML |

#### Sample JSON Submission

```javascript
{
    "meta": {
        "dataType": "json"
    },
    "serviceRequestData": {
      "meta": {
        "cabinet": "string",
        "currency": "USD",
        "createdBy": "email"
      },
      "transactional": {
        "Transactional Fields as Objects"
      },
      "collaterals": [
        {
          "Collaterals as Array of Objects"
        }
      ]
    }
}
```

#### Sample XML Submission

```javascript
{
    "meta": {
        "dataType": "xml"
    },
    "serviceRequestData": "<?xml version=\"1.0\" encoding=\"UTF-8\"?>
      <serviceRequestForm>
        <meta>
          <cabinet />
          <currency />
          <createdBy />
        </meta>
        <transactional />
        <collaterals>
          <collateral />
        </collaterals>
      </serviceRequestForm>"
}
```

### Response

```javascript
{
    "meta": {
        "responseCode": 201,
        "date": "2018-04-28 12:23:23",
        "function": "update"
    },
    "data": {
        "serviceRequestID": 1234567,
        "loanID": null,
        "locations": []
    }
}
```

<div style="page-break-after: always;"></div>
