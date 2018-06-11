# SRF API

## Service Request Data Fields

##### Data Fields for Service Request Fields

| Data Field | Type | Description |
| :--- | :--- | :--- |
| projectName | string | Project Name |
| cabinet | string | Cabinet Name |
| loanNumber | string | Loan Number |
| accountOfficer | string | Account Officer |
| requestor | string | Requestor |
| loanAmount | number | Loan amount |
| currency | string | Currency type. Default is USD |
| borrower | string | Borrower |
| loanPurpose | string | Loan purpose (enum) |
| extended | object | Extended Custom Data Fields |
| collaterals | object | Array of Collaterals |

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

## <span style="background-color: #5493dc; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">PUT</span> **Service Request Details**

```text
/v1/api/srf/:serviceRequestID
```

### Request

#### Path Parameters

| Path Parameter | Type | Description |
| :--- | :--- | :--- |
| serviceRequestID | Int | Service Request ID |

#### Body Parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| meta | object | Metadata for the data being submitted |
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
        "projectName": "string",
        "cabinet": "string",
        "loanNumber": "string",
        "accountOfficer": "string",
        "requestor": "string",
        "loanAmount": "number",
        "currency": "string",
        "borrower": "string",
        "loanPurpose": "string",
        "extended": {
            "lotSize": "3 acres",
            "parking": "garage"
        },
        "collaterals": [
            {
                "addresses": [
                    {
                        "street_address": "string",
                        "optional_address": "string",
                        "city": "string",
                        "state": "string",
                        "stateAbbreviated": "string",
                        "zip": "string",
                        "country": "string",
                        "countryAbbreviated": "string",
                        "primary": "boolean"
                    }
                ],
                "propertyType": "string",
                "services": [],
                "extended": {
                    "lon": "",
                    "lat": "",
                    "tax": "abated"
                }
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
    "serviceRequestData": "<?xml version=\"1.0\" encoding=\"UTF-8\"?><serviceRequestForm><meta><dataType>json</dataType></meta><serviceRequestData><accountOfficer>string</accountOfficer><borrower>string</borrower><collaterals> <collateral><address1>string</address1><address2>string</address2><city>string</city><extended> <lat /> <lon /> <tax>abated</tax></extended><propertyType>string</propertyType><state>string</state><stateAbbreviated>string</stateAbbreviated><zip>string</zip> </collateral></collaterals><extended> <lotSize>3 acres</lotSize> <parking>garage</parking></extended><loanAmount>number</loanAmount><currency>USD</currency><loanNumber>string</loanNumber><loanPurpose>string</loanPurpose><projectName>string</projectName><requestor>string</requestor> </serviceRequestData></serviceRequestForm>"
}
```

#### Sample JSON Stringified Submission

```javascript
{
    "meta": {
        "dataType": "string"
    },
    "serviceRequestData": "{\"meta\": {\"dataType\": \"json\"},\"serviceRequestData\": {\"projectName\": \"string\",\"loanNumber\": \"string\",\"accountOfficer\": \"string\",\"requestor\": \"string\",\"loanAmount\": \"string\",\"currency\":\"USD\",\"borrower\": \"string\",\"loanPurpose\": \"string\",\"extended\": {\"lotSize\": \"3 acres\",\"parking\": \"garage\"},\"collaterals\": [{\"address1\": \"string\",\"address2\": \"string\",\"city\": \"string\",\"state\": \"string\",\"stateAbbreviated\": \"string\",\"zip\": \"string\",\"propertyType\": \"string\",\"extended\": {\"lon\": \"\",\"lat\": \"\",\"tax\": \"abated\"}}]}}"
}
```

### Response

```javascript
{
    "response": {
        "code": 201,
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

## <span style="background-color: #ebb747; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">POST</span> **Service Request Details**

```text
/v1/api/srf
```

### Request

#### Body Parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| meta | object | Metadata for the data being submitted |
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
    "projectName": "string",
    "cabinet": "string",
    "loanNumber": "string",
    "accountOfficer": "string",
    "requestor": "string",
    "loanAmount": "number",
    "currency": "string",
    "borrower": "string",
    "loanPurpose": "string",
    "extended": {
      "lotSize": "3 acres",
      "parking": "garage"
    },
    "collaterals": [
      {
        "addresses": [
          {
            "street_address": "string",
            "optional_address": "string",
            "city": "string",
            "state": "string",
            "stateAbbreviated": "string",
            "zip": "string",
            "country": "string",
            "countryAbbreviated": "string",
            "primary": "boolean"
          }
        ],
        "propertyType": "string",
        "services": [],
        "extended": {
          "lon": "",
          "lat": "",
          "tax": "abated"
        }
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
    "serviceRequestData": "<?xml version=\"1.0\" encoding=\"UTF-8\"?><serviceRequestForm><meta><dataType>json</dataType></meta><serviceRequestData><accountOfficer>string</accountOfficer><borrower>string</borrower><collaterals> <collateral><address1>string</address1><address2>string</address2><city>string</city><extended> <lat /> <lon /> <tax>abated</tax></extended><propertyType>string</propertyType><state>string</state><stateAbbreviated>string</stateAbbreviated><zip>string</zip> </collateral></collaterals><extended> <lotSize>3 acres</lotSize> <parking>garage</parking></extended><loanAmount>string</loanAmount><currency>USD</currency><loanNumber>string</loanNumber><loanPurpose>string</loanPurpose><projectName>string</projectName><requestor>string</requestor> </serviceRequestData></serviceRequestForm>"
}
```

#### Sample JSON Stringified Submission

```javascript
{
    "meta": {
        "dataType": "string"
    },
    "serviceRequestData": "{\"meta\": {\"dataType\": \"json\"},\"serviceRequestData\": {\"projectName\": \"string\",\"loanNumber\": \"string\",\"accountOfficer\": \"string\",\"requestor\": \"string\",\"loanAmount\": \"string\",\"currency\":\"USD\",\"borrower\": \"string\",\"loanPurpose\": \"string\",\"extended\": {\"lotSize\": \"3 acres\",\"parking\": \"garage\"},\"collaterals\": [{\"address1\": \"string\",\"address2\": \"string\",\"city\": \"string\",\"state\": \"string\",\"stateAbbreviated\": \"string\",\"zip\": \"string\",\"propertyType\": \"string\",\"extended\": {\"lon\": \"\",\"lat\": \"\",\"tax\": \"abated\"}}]}}"
}
```

### Response

```javascript
{
    "response": {
        "code": 201,
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

