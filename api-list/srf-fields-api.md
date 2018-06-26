# SRF Fields API

The SRF Fields API will return a schema that dedcribes the
fields available for entry on service request forms. The
response will be formatted according to the JSON Schema
specification, which is documented here:

    http://json-schema.org/

Client applications should use the returned JSON schema to
format API requests for the creation and modification of
service requests.

> During the initial testing phase of the LOS API, the field
> list returned by this endpoint will be substantially complete,
> but some fields may not be present. These fields will be
> added to the schema as integration with client customizations
> to EDR's SRF functionality continues.
> 
> Any SRF fields not included in the JSON schema must be entered
> manually via the Collateral 360 web applicaton.

The schema returned by this endpoint will contain basic data
type validation rules. More specific validation rules (e.g.
data formatting for complex data types) will be added over time
in order to assist client application developers in providing
improved user experiences in their applications. Client
applications should be tolerant of additions to the schema.

## The JSON Schema Model

The following example JSON Schema represents the minimal data
requirements and the required fields. String values ending with
ellipses ("`...`") represent metasyntactic descriptions of the
contents of their containing elements, and should not be
considered literal examples of the data in these elements.

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
          "title": "The Cabinet Schema",
          "$ref": "#/definitions/cabinets"
        },
        "currency": {
          "$id": "/properties/meta/items/properties/currency",
          "type": "string",
          "title": "The Currency Schema",
          "$ref": "#/definitions/currency"
        },
        "createdBy": {
          "$id": "/properties/meta/items/properties/createdBy",
          "type": "string",
          "title": "The Created By Schema ",
          "format": "email"
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

## API Endpoints

The following endpoints are defined by this API subsystem:

### <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span> **Service Request Details**

```text
/api/v1/serviceRequestFields
```

Accessing this endpoint via an HTTP GET method will return a
representation of the fields available as part of your SRF.

The fields will broadly be delineated into three groups, each under their
own data element:

* The `meta` group contains descriptions of fields that describe the SRF,
  but which are not actually visible SRF fields within Collateral 360.
  These may represent data that are normally handled behind-the-scenes
  or automatically within Collateral 360, and that therefore may require
  special consideration by your application.
  
  For example, if your organization uses cabinets in Collateral 360 to
  organize your service requests, cabinet selection is ordinarily performed
  in the user interface prior to entering data into the service request form
  screen. When creating a service request via the API, the schema for the
  cabinet selection field will accordingly appear in the `meta` section.
  
* The `transactional` section contains schemata for fields that are only
  entered once, regardless of how many collateral properties are part of
  the service request.
  
  For example, a loan principal amount would typically appear here, since
  each loan only has one principal amount irrespective of how many real
  properties are used to collateralize it. 
  
* The `collaterals` section contains schemata for fields that are entered
  for each collateral property associated with the service request.
  
  For example, a property street address would appear here, since each
  real property used to collateralize a loan has its own address. 
  
The following are examples of XML and JSON data format. These are
default data fields which are required. Custom data fields can be
added to "extended" for main data and collateral data. So you can
submit custom fields for the Service Request and custom fields for
the collateral data as well.

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
    "meta": {
        "responseCode": 200,
        "responseID": "e3733640-789c-11e8-9dfc-81c439846400",
        "success": true,
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
    "meta": {
        "responseCode": 200,
        "responseID": "e3733640-789c-11e8-9dfc-81c439846400",
        "success": true,
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
