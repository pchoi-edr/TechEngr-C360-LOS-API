# Service Request Form API

The SRF API is used to create or replace a draft service request.
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

## Handling of Invalid Data

Each draft service request is considered to be a
work-in-progress, and most data validation rules are not
executed while a service request is in the draft status.

Accordingly, each invalid field value supplied to the draft
SRF API endpoints will cause one of the following results
to occur:

  * The invalid value will be recorded in the draft
    service request.
    
  * The invalid value will result in a blank field in
    the draft service request.
    
In either case, the system may generate a warning in the
API response.

Note that, due to internal implementation details of the API
system, an invalid user account email address should always
generate a warning if it is not used for determining access
according to permissions rules (in which case an error will
be generated instead).

## API Request Structure

API requests issued to create or modify a service request all have
the same high-level structure.

### Metadata Field Definitions

The following fields should be included in the API request's
top-level `meta` element:

| Metadata Field | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| cabinet | Yes | String | The name of the cabinet that will contain the draft SRF. |
| currency | Yes | String | A three-letter ISO 4217 currency code. This must be in uppercase. |
| requestedBy | Yes | String | The email address of the user who is issuing this request (for an HTTP `POST` operation, this will be the service request creator). This must be an email address associated with an appropriate user account in Collateral 360. |

### Data Field Definitions

The following elements will be expected within the API request's
top-level `data` element:

| Data Field | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| transaction | Yes | Object | General data fields that describe the service request. |
| collaterals | Yes | Array | An array where each element contains the data fields that describe a single real property used as collateral. |

Note that, depending on your configuration options in Collateral 
360, draft SRFs may only be visible to the user who created them.
In this case, the `requestedBy` field defines this user within
the original API call used to create a service request.

Unless otherwise noted, all monetary amounts in the request will be
denominated in the specified currency.

### Transaction Field Definitions

The values in the API request's `transaction` element will
vary by client. Each value represents a data field that describes
the overall service request independently of any collateral (such
as a loan principal amount).

The fields that can be included in this section are defined in the
JSON schema returned by the SRF Fields API.

### Collateral Field Definitions

The API request's `collaterals` element consists of an array where
each element represents an individual real property used to
collateralize a loan. As such, the fields in this section can
be repeated between each element.

Similarly to the `transaction` element's contents, the fields in
each element of the `collaterals` array are defined in the JSON 
schema returned by the SRF Fields API. However, one additional field
is present:

| Data Field | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| services |Yes| Array | An array of services to perform on the collateral property. |

Each element in the `services` array is an object that represents a
service to perform on a collateral property, such as the following
examples (your set of services may be different):

* Phase I Environmental Report

* Property Appraisal Inspection

Each service is associated with a _feature_, which represents the broad
category of services it belongs to. Typical features may include
environmental services, appraisal services, construction services, _etc._

You may wish to segregate or group services according to their
associated features within your application's user interface to
improve its intuitiveness.

Each element in the `services` array must be an object that has
the following values, which are defined in the JSON schema
returned by the SRF Fields API:

| Data Field | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| serviceType | Yes | String | The unique value used to identify each type of service. |

<div style="page-break-after: always;"></div>

## Available API Endpoints

The following endpoints are supported by the SRF API subsystem:


* [POST](api-list/srf-api/srf-api-post.md)
* [PUT](api-list/srf-api/srf-api-put.md)
* [PATCH](api-list/srf-api/srf-api-patch.md)

