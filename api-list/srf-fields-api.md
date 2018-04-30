# SRF Fields API

## <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span> **Service Request Details**

```text
/v1/api/serviceRequestFields
```

### JSON Schema Model

This JSON Schema represents the minimal data requirements and the required fields

```javascript
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "propertyName": {
      "type": "string"
    },
    "loanNumber": {
      "type": "string"
    },
    "accountOfficer": {
      "type": "string"
    },
    "requestor": {
      "type": "string"
    },
    "loanAmount": {
      "type": "string"
    },
    "borrower": {
      "type": "string"
    },
    "loanPurpose": {
      "type": "string"
    },
    "extended": {
      "type": "object"
    },
    "collaterals": {
      "type": "array",
      "items": [
        {
          "type": "object",
          "properties": {
            "address1": {
              "type": "string"
            },
            "address2": {
              "type": "string"
            },
            "city": {
              "type": "string"
            },
            "state": {
              "type": "string"
            },
            "zip": {
              "type": "string"
            },
            "propertyType": {
              "type": "string"
            },
            "extended": {
              "type": "object"
            }
          },
          "required": [
            "address1",
            "address2",
            "city",
            "state",
            "zip",
            "propertyType",
            "extended"
          ]
        }
      ]
    }
  },
  "required": [
    "propertyName",
    "loanNumber",
    "accountOfficer",
    "requestor",
    "loanAmount",
    "borrower",
    "loanPurpose",
    "collaterals"
  ]
}
```

#### Collateral Model

This JSON Schema represents the Collateral Data Model.

```javascript
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "address1": {
      "type": "string"
    },
    "address2": {
      "type": "string"
    },
    "city": {
      "type": "string"
    },
    "state": {
      "type": "string"
    },
    "zip": {
      "type": "string"
    },
    "propertyType": {
      "type": "string"
    },
    "extended": {
      "type": "object"
    }
  },
  "required": [
    "address1",
    "address2",
    "city",
    "state",
    "zip",
    "propertyType"
  ]
}
```



```xml
<?xml version="1.0" encoding="UTF-8"?>
<serviceRequestForm>
   <propertyName />
   <loanNumber />
   <accountOfficer />
   <requestor />
   <loanAmount />
   <borrower />
   <extended />
   <loanPurpose />
   <collaterals>
      <collateral>
         <address1 />
         <address2 />
         <city />
         <state />
         <stateAbbreviated />
         <zip />
         <propertyType />
         <extended />
      </collateral>
   </collaterals>
</serviceRequestForm>
```

```javascript
{
  "propertyName": "string",
  "loanNumber": "string",
  "accountOfficer": "string",
  "requestor": "string",
  "loanAmount": "string",
  "borrower": "string",
  "loanPurpose": "string",
  "extended": {},
  "collaterals": [
    {
      "address1": "string",
      "address2": "string",
      "city": "string",
      "state": "string",
      "stateAbbreviated": "string",
      "zip": "string",
      "propertyType": "string",
      "extended": {}
    }
  ]
}
```

### Response

```javascript
{
    "response": {
        "code": 200,
        "date": "2018-04-28 12:23:23",
        "function": "get"
    },
    "data": {
        "JSON": {
            "meta": {
                "dataType": "json"
            },
            "serviceRequestData": {
                "propertyName": "string",
                "loanNumber": "string",
                "accountOfficer": "string",
                "requestor": "string",
                "loanAmount": "string",
                "borrower": "string",
                "loanPurpose": "string",
                "extended": {
                    "lotSize": "3 acres",
                    "parking": "garage"
                },
                "collaterals": [
                    {
                        "address1": "string",
                        "address2": "string",
                        "city": "string",
                        "state": "string",
                        "stateAbbreviated": "string",
                        "zip": "string",
                        "propertyType": "string",
                        "extended": {
                            "lon": "",
                            "lat": "",
                            "tax": "abated"
                        }
                    }
                ]
            }
        },
        "XML": "
            <?xml version="1.0" encoding="UTF-8"?>
            <serviceRequestForm>
            <meta>
                <dataType>json</dataType>
            </meta>
            <serviceRequestData>
                <accountOfficer>string</accountOfficer>
                <borrower>string</borrower>
                <collaterals>
                    <collateral>
                        <address1>string</address1>
                        <address2>string</address2>
                        <city>string</city>
                        <extended>
                        <lat />
                        <lon />
                        <tax>abated</tax>
                        </extended>
                        <propertyType>string</propertyType>
                        <state>string</state>
                        <stateAbbreviated>string</stateAbbreviated>
                        <zip>string</zip>
                    </collateral>
                </collaterals>
                <extended>
                    <lotSize>3 acres</lotSize>
                    <parking>garage</parking>
                </extended>
                <loanAmount>string</loanAmount>
                <loanNumber>string</loanNumber>
                <loanPurpose>string</loanPurpose>
                <propertyName>string</propertyName>
                <requestor>string</requestor>
            </serviceRequestData>
            </serviceRequestForm>
        "
    }
}
```


