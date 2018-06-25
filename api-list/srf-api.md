# SRF API

## Service Request Data Fields

##### Data Fields for Service Request Fields

| Data Field | Type | Description |
| :--- | :--- | :--- |
| meta | object | Project Meta Data |
| transactional | object | Project Fields |
| collaterals | object | Array of Collaterals |

##### Data Fields for Service Request Fields META

| Data Field | Type | Description |
| :--- | :--- | :--- |
| cabinet | string | Cabinet Name |
| currency | string | Currency 3 Code |
| createdBy | email | Email of SRF Creator |

##### Data Fields for `Collaterals`

| Data Field | Type | Description |
| :--- | :--- | :--- |
| street_address | array | Array of addresses |
| optional_address | string | Suite #; Apt #; etc... |
| city | string | City name |
| state | string | Full state name (enum) |
| stateAbbreviated | string | State 2 letter abbreviation (enum) |
| zip | string | Zip code |
| country | string | Country location (enum) |
| countryAbbreviated | string | Country Abbreviated location (enum) |
| propertyType | string | Property Type (enum) |
| services | array | Array of Services |
| extended | object | Extended Custom Data Fields for Collateral |

##### Data Fields for `Services`

| Data Field | Type | Description |
| :--- | :--- | :--- |
| siteType | string | Site Type |
| displayName | string | Display Name |
| featureID | array | Feature ID |
| featureName | array | Feature Name |

<div style="page-break-after: always;"></div>

## <span style="background-color: #5493dc; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">PUT</span> **Service Request Form**

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

