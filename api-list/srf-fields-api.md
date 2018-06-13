# SRF Fields API

The SRF Fields API will return a template of JSON or XML data schema. It will be up to the developer to make sure they provide proper data according to the JSON Schema in order to properly create a SRF within C360.

### JSON Schema Model

This JSON Schema represents the minimal data requirements and the required fields

```javascript
{
  "$id": "service-request-form",
  "type": "object",
  "$schema": "http://json-schema.org/draft-07/schema#",
  "properties": {
    "meta": {
      "$id": "/properties/meta",
      "type": "object",
      "properties": {
        "cabinet": {
          "$id": "/properties/meta/items/properties/cabinet",
          "type": "string",
          "title": "The Cabinet Schema ",
          "$ref": "#/definitions/cabinets"
        },
        "currency": {
          "$id": "/properties/meta/items/properties/currency",
          "type": "string",
          "title": "The Currency Schema ",
          "$ref": "#/definitions/currency"
        }
      }
    },
    "transactional": {
      "$id": "/properties/transactional",
      "type": "object",
      "properties": {
        "Transactional Properties as Objects..."
      },
      "required": [
        "Required Transactional Fields..."
      ]
    },
    "collaterals": {
      "$id": "/properties/collaterals",
      "type": "array",
      "items": {
        "$id": "/properties/collaterals/items",
        "type": "object",
        "properties": {
          "Collateral Properties as Objects..."
        },
        "dependencies": {
          "propertyType": ["propertySubType"],
          "propertySubType": ["propertyType"]
        },
        "definitions": {
          "propertyTypes": {
            "$id": "/properties/collaterals/items/definitions/propertyTypes",
            "type": "object",
            "items": {
              "$id": "/properties/collaterals/items/definitions/propertyTypes/items",
              "type": "object",
              "properties": {

              }
            }
          }
        }
        "required": [
          "Required Collateral Fields..."
        ]
      }
    }
  },
  "definitions": {
    "services": {
      "$id": "/definitions/services",
      "type": "object",
      "default": "",
      "enum": [
        "Services as Objects..."
      ]
    },
  }
}
```

<div style="page-break-after: always;"></div>

## <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span> **Service Request Details**

```text
/v1/api/serviceRequestFields
```

The following are examples of XML and JSON data format. These are default data fields which are required. Custom data fields can be added to "extended" for main data and collateral data. So you can submit custom fields for the Service Request and custom fields for the collateral data as well.

```xml
<?xml version="1.0" encoding="UTF-8"?>
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
</serviceRequestForm>
```

```javascript
{
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
```

### Response

#### Abbreviated

```javascript
{
    "response": {
        "code": 200,
        "date": "2018-04-28 12:23:23",
        "function": "get"
    },
    "data": {
        "model": {
            "jsonSchema": {"JSON Object Format using JSON Schema Draft-7..."},
        },
        "dataTemplates": {
            "json": {"JSON Object Format..."},
            "xml": "XML in String Format..."
        }

    }
}
```

#### Full

```javascript
{
    "response": {
        "code": 200,
        "date": "2018-04-28 12:23:23",
        "function": "get"
    },
    "data": {
      "model": {
        "jsonSchema": {
          "$id": "service-request-form",
          "type": "object",
          "$schema": "http://json-schema.org/draft-07/schema#",
          "properties": {
            "meta": {
              "$id": "/properties/meta",
              "type": "object",
              "properties": {
                "cabinet": {
                  "$id": "/properties/meta/items/properties/cabinet",
                  "type": "string",
                  "title": "The Cabinet Schema ",
                  "$ref": "#/definitions/cabinets"
                },
                "currency": {
                  "$id": "/properties/meta/items/properties/currency",
                  "type": "string",
                  "title": "The Currency Schema ",
                  "$ref": "#/definitions/currency"
                },
                "createdBy": {
                  "$id": "/properties/meta/items/properties/createdBy",
                  "type": "string",
                  "title": "The Created By Schema ",
                  "format": "email"
                }
              },
              "required": [
                "cabinet",
                "currency",
                "createdBy"
              ]
            },
            "transactional": {
              "$id": "/properties/transactional",
              "type": "object",
              "properties": {
                "Transactional Properties as Objects..."
              },
              "required": [
                "Required Transactional Fields..."
              ]
            },
            "collaterals": {
              "$id": "/properties/collaterals",
              "type": "array",
              "items": {
                "$id": "/properties/collaterals/items",
                "type": "object",
                "properties": {
                  "Collateral Properties as Objects..."
                },
                "required": [
                  "Required Collateral Fields..."
                ]
              }
            }
          },
          "definitions": {
            "services": {
              "$id": "/definitions/services",
              "type": "object",
              "default": "",
              "enum": [
                "Services as Objects..."
              ]
            },
          },
          "required": [
            "Required Main Fields..."
          ]
        },
      }
      "dataTemplates": {
        "JSON": {
          "meta": {
            "cabinet": "string",
            "currency": "USD"
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
        },
        "XML": "<?xml version=\"1.0\" encoding=\"UTF-8\"?>
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
    }
  }
}
```

## C360 Cabinets

C360 organizes loan information as Cabinets, much like a filing cabinet. Even if you have one loan, your form data is organized by Cabinet Name.

{need more info}

## Custom Fields

Within C360, there is provisions to provide for custom fields. Custom Fields can to added to the data schema by adding to the "extended" object either as objects or xml tags when submitting new data.

However, custom fields must exits within the JSON Schema to be processed. The JSON Schema will be generated based on the clients C360 Forms model and validation rules.

Any extraneous data fields not matching the Schema will be silently ignored. No warnings or information will be provided.
