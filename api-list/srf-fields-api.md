# SRF Fields API

The SRF Fields API will return a template of JSON or XML data schema. It will be up to the developer to make sure they provide proper data according to the JSON Schema in order to properly create a SRF within C360.

### JSON Schema Model

This JSON Schema represents the minimal data requirements and the required fields

```javascript
{
  "$id": "http://example.com/example.json",
  "type": "object",
  "$schema": "http://json-schema.org/draft-07/schema#",
  "properties": {
    "projectName": {
      "$id": "/properties/projectName",
      "type": "string",
      "title": "The Projectname Schema ",
      "default": "",
      "examples": [
        "string"
      ]
    },
    "cabinet": {
      "$id": "/properties/cabinet",
      "type": "string",
      "title": "The Cabinet Schema ",
      "description": "C360 organized vendor information as Cabinets, much like a filing cabinet. Even if you have one vendor, you form data is organized by Cabinet Name.",
      "default": "",
      "$ref": "#/definitions/cabinets",
      "examples": [
        "string"
      ]
    },
    "loanNumber": {
      "$id": "/properties/loanNumber",
      "type": "string",
      "title": "The Loannumber Schema ",
      "default": "",
      "examples": [
        "string"
      ]
    },
    "accountOfficer": {
      "$id": "/properties/accountOfficer",
      "type": "string",
      "title": "The Accountofficer Schema ",
      "default": "",
      "examples": [
        "string"
      ]
    },
    "requestor": {
      "$id": "/properties/requestor",
      "type": "string",
      "title": "The Requestor Schema ",
      "default": "",
      "examples": [
        "string"
      ]
    },
    "loanAmount": {
      "$id": "/properties/loanAmount",
      "type": "number",
      "title": "The Loanamount Schema ",
      "default": 0.00,
      "examples": [
        1000.00
      ]
    },
    "currency": {
      "$id": "/properties/currency",
      "type": "string",
      "title": "The Currency Schema ",
      "default": "USD",
      "enum": [
        "USD"
      ],
      "examples": [
        "USD"
      ]
    },
    "borrower": {
      "$id": "/properties/borrower",
      "type": "string",
      "title": "The Borrower Schema ",
      "default": "",
      "examples": [
        "string"
      ]
    },
    "loanPurpose": {
      "$id": "/properties/loanPurpose",
      "type": "string",
      "title": "The Loanpurpose Schema ",
      "default": "",
      "$ref": "#/definitions/loanPurposes",
      "examples": [
        "SBA"
      ]
    },
    "extended": {
      "$id": "/properties/extended",
      "type": "object"
    },
    "collaterals": {
      "$id": "/properties/collaterals",
      "type": "array",
      "items": {
        "$id": "/properties/collaterals/items",
        "type": "object",
        "properties": {
          "addresses": {
            "$id": "/properties/collaterals/items/properties/addresses",
            "title": "The Addresses Schema ",
            "type": "array",
            "default": "",
            "items": {
              "$ref": "#/definitions/addresses"
            },
            "examples": [
              "string"
            ]
          },
          "propertyType": {
            "$id": "/properties/collaterals/items/properties/propertyType",
            "type": "string",
            "title": "The Propertytype Schema ",
            "default": "",
            "$ref": "#/definitions/propertyTypes",
            "examples": [
              "string"
            ]
          },
          "services": {
            "$id": "/properties/collaterals/items/properties/services",
            "title": "The Services Schema ",
            "type": "array",
            "default": "",
            "items": {
              "$ref": "#/definitions/services"
            },
            "examples": [
              "string"
            ]
          },
          "extended": {
            "$id": "/properties/collaterals/items/properties/extended",
            "type": "object"
          }
        },
        "required": [
          "addresses",
          "propertyType",
          "services",
          "extended"
        ]
      }
    }
  },
  "definitions": {
    "addresses": {
      "$id": "/definitions/addresses",
      "title": "Address",
      "type": "object",
      "properties": {
        "street_address": {
          "$id": "/definitions/address/properties/street_address",
          "type": "string",
          "title": "The Street Address Schema ",
          "default": "",
          "example": [
            "string"
          ]
        },
        "optional_address": {
          "$id": "/definitions/address/properties/extra_address",
          "type": "string",
          "title": "The Optional Address Schema ",
          "default": "",
          "example": [
            "string"
          ]
        },
        "city": {
          "$id": "/definitions/address/properties/city",
          "type": "string",
          "title": "The City Schema ",
          "default": "",
          "example": [
            "string"
          ]
        },
        "state": {
          "$id": "/definitions/address/properties/state",
          "type": "string",
          "title": "The State Schema ",
          "default": "",
          "enum": [
            "Aguascalientes", "Alabama", "Alaska", "Alberta", "Arizona", "Arkansas", "Baja California", "Baja California Sur", "British Columbia", "California", "Campeche", "Chiapas", "Chihuahua", "Coahuila", "Colima", "Colorado", "Connecticut", "Delaware", "District of Columbia", "Durango", "Federal District", "Florida", "Georgia", "Guanajuato", "Guerrero", "Hawaii", "Hidalgo", "Idaho", "Illinois", "Indiana", "Iowa", "Jalisco", "Kansas", "Kentucky", "Louisiana", "Maine", "Manitoba", "Maryland", "Massachusetts", "Mexico State", "Michigan", "Michoacán", "Minnesota", "Mississippi", "Missouri", "Montana", "Morelos", "Nayarit", "Nebraska", "Nevada", "New Brunswick", "New Hampshire", "New Jersey", "New Mexico", "New York", "Newfoundland", "North Carolina", "North Dakota", "Northwest Territories", "Nova Scotia", "Nuevo León", "Nunavut", "Oaxaca", "Ohio", "Oklahoma", "Ontario", "Oregon", "Pennsylvania", "Prince Edward Island", "Puebla", "Puerto Rico", "Quebec", "Querétaro", "Quintana Roo", "Rhode Island", "San Luis Potosí", "Saskatchewan", "Sinaloa", "Sonora", "South Carolina", "South Dakota", "Tabasco", "Tamaulipas", "Tennessee", "Texas", "Tlaxcala", "Utah", "Veracruz", "Vermont", "Virginia", "Washington", "West Virginia", "Wisconsin", "Wyoming", "Yucatán", "Yukon Territory", "Zacatecas"
          ],
          "example": [
            "string"
          ]
        },
        "state_abbreviated": {
          "$id": "/definitions/address/properties/state_abbreviated",
          "type": "string",
          "title": "The State Abbreviated Schema ",
          "default": "",
          "enum": [
            "AB", "AGU", "AK", "AL", "AR", "AZ", "BC", "BCN", "BCS", "CA", "CAM", "CHH", "CHP", "CO", "COA", "COL", "CT", "DC", "DE", "DIF", "DUR", "FL", "GA", "GRO", "GUA", "HI", "HID", "IA", "ID", "IL", "IN", "JAL", "KS", "KY", "LA", "MA", "MB", "MD", "ME", "MEX", "MI", "MIC", "MN", "MO", "MOR", "MS", "MT", "NAY", "NB", "NC", "ND", "NE", "NH", "NJ", "NL", "NLE", "NM", "NS", "NT", "NU", "NV", "NY", "OAX", "OH", "OK", "ON", "OR", "PA", "PE", "PR", "PUE", "QC", "QUE", "RI", "ROO", "SC", "SD", "SIN", "SK", "SLP", "SON", "TAB", "TAM", "TLA", "TN", "TX", "UT", "VA", "VER", "VT", "WA", "WI", "WV", "WY", "YT", "YUC", "ZAC"
          ],
          "example": [
            "string"
          ]
        },
        "zip": {
          "$id": "/definitions/address/properties/zip",
          "type": "string",
          "title": "The Zip Schema ",
          "default": "",
          "example": [
            "string"
          ]
        },
        "country": {
          "$id": "/definitions/address/properties/country",
          "type": "string",
          "title": "The country Schema ",
          "default": "United States",
          "enum": [
            "Afghanistan", "Albania", "Algeria", "American Samoa", "Andorra", "Angola", "Anguilla", "Antarctica", "Antigua and Barbuda", "Argentina", "Armenia", "Aruba", "Australia", "Austria", "Azerbaijan", "Bahamas, The", "Bahrain", "Bangladesh", "Barbados", "Belarus", "Belgium", "Belize", "Benin", "Bermuda", "Bhutan", "Bolivia", "Bosnia and Herzegovina", "Botswana", "Bouvet Island", "Brazil", "British Indian Ocean Territory", "British Virgin Islands", "Brunei", "Bulgaria", "Burkina Faso", "Burundi", "Cambodia", "Cameroon", "Canada", "Cape Verde", "Cayman Islands", "Central African Republic", "Chad", "Chile", "China", "Christmas Island", "Cocos (Keeling) Islands", "Colombia", "Comoros", "Congo", "Congo, Democratic Republic of the", "Cook Islands", "Costa Rica", "Croatia", "Cuba", "Cyprus", "Czech Republic", "Denmark", "Djibouti", "Dominica", "Dominican Republic", "East Timor", "Ecuador", "Egypt", "El Salvador", "Equatorial Guinea", "Eritrea", "Estonia", "Ethiopia", "Falkland Islands (Islas Malvinas)", "Faroe Islands", "Federated States of Micronesia", "Fiji", "Finland", "France", "French Guiana", "French Polynesia", "Gabon", "Gambia,The", "Georgia", "Germany", "Ghana", "Gibraltar", "Greece", "Greenland", "Grenada", "Guadeloupe", "Guam", "Guatemala", "Guernsey", "Guinea", "Guinea-Bissau", "Guyana", "Haiti", "Heard Island and McDonald Islands", "Honduras", "Hong Kong", "Hungary", "Iceland", "India", "Indonesia", "Iran", "Iraq", "Ireland", "Isle of Man", "Israel", "Italy", "Ivory Coast (Cote d'Ivoire)", "Jamaica", "Japan", "Jersey", "Jordan", "Kazakhstan", "Kenya", "Kiribati", "Kuwait", "Kyrgyzstan", "Laos", "Latvia", "Lebanon", "Lesotho", "Liberia", "Libya", "Liechtenstein", "Lithuania", "Luxembourg", "Macao", "Macedonia", "Madagascar", "Malawi", "Malaysia", "Maldives", "Mali", "Malta", "Marshall Islands", "Martinique", "Mauritania", "Mauritius", "Mayotte", "Mexico", "Moldova", "Monaco", "Mongolia", "Montenegro", "Montserrat", "Morocco", "Mozambique", "Myanmar (Burma)", "Namibia", "Nauru", "Nepal", "Netherlands", "Netherlands Antilles", "New Caledonia", "New Zealand", "Nicaragua", "Niger", "Nigeria", "Niue", "Norfolk Island", "North Korea", "Northern Mariana Islands", "Norway", "Oman", "Pakistan", "Palau", "Panama", "Papua New Guinea", "Paraguay", "Peru", "Philippines", "Pitcairn Islands", "Poland", "Portugal", "Puerto Rico", "Qatar", "Reunion", "Romania", "Russia", "Rwanda", "Samoa", "San Marino", "Sao Tome and Principe", "Saudi Arabia", "Senegal", "Serbia", "Seychelles", "Sierra Leone", "Singapore", "Slovakia", "Slovenia", "Solomon Islands", "Somalia", "South Africa", "South Georgia and the South Sandwich Islands", "South Korea", "Spain", "Sri Lanka", "St. Helena", "St. Kitts and Nevis", "St. Lucia", "St. Pierre and Miquelon", "St. Vincent and the Grenadines", "Sudan", "Suriname", "Swaziland", "Sweden", "Switzerland", "Syria", "Taiwan", "Tajikistan", "Tanzania, United Republic of", "Thailand", "Togo", "Tokelau", "Tonga", "Trinidad and Tobago", "Tunisia", "Turkey", "Turkmenistan", "Turks and Caicos Islands", "Tuvalu", "Uganda", "Ukraine", "United Arab Emirates", "United Kingdom", "United States", "Uruguay", "Uzbekistan", "Vanuatu", "Vatican City (Holy See)", "Venezuela", "Vietnam", "Virgin Islands (US)", "Wallis and Futuna", "Western Sahara", "Yemen", "Zambia", "Zimbabwe"
          ],
          "example": [
            "United States"
          ]
        },
        "primary": {
          "$id": "/definitions/address/properties/primary",
          "type": "boolean",
          "title": "The Primary Schema ",
          "default": false,
          "example": [
            false
          ]
        }
      },
      "required": [
        "street_address",
        "optional_address",
        "city",
        "state",
        "state_abbreviated",
        "zip",
        "country",
        "default"
      ]
    },
    "services": {
      "$id": "/definitions/services",
      "type": "object",
      "default": "",
      "enum": [{
        "siteType": "PhaseI",
        "displayName": "Phase I Environmental Site Assessment",
        "featureID": "81",
        "featureName": "Procure New Services"
      },
        {
          "siteType": "ASTMPCA",
          "displayName": "ASTM Property Condition Assessment",
          "featureID": "122",
          "featureName": "Procure New Services"
        },
        {
          "siteType": "Appraisal",
          "displayName": "Commercial Appraisal Report",
          "featureID": "87",
          "featureName": "Valuation Services"
        },
        {
          "siteType": "AppraisalRev",
          "displayName": "Commercial Appraisal Review",
          "featureID": "87",
          "featureName": "Valuation Services"
        },
        {
          "siteType": "Evaluation",
          "displayName": "Commercial Evaluation",
          "featureID": "87",
          "featureName": "Valuation Services"
        },
        {
          "siteType": "LoanChkPlus",
          "displayName": "Loan Check Plus",
          "featureID": "81",
          "featureName": "Procure New Services"
        },
        {
          "siteType": "PhaseII",
          "displayName": "Phase II Environmental Site Assessment",
          "featureName": "81",
          "": "Procure New Services"
        },
        {
          "siteType": "ASTM",
          "displayName": "ASTM Transaction Screen",
          "featureID": "81",
          "featureName": "Procure New Services"
        },
        {
          "siteType": "DBReview",
          "displayName": "Database Review",
          "featureID": "81",
          "featureName": "Procure New Services"
        },
        {
          "siteType": "ResAppraisal",
          "displayName": "Residential Appraisal",
          "featureID": "87",
          "featureName": "Valuation Services"
        }
      ],
      "examples": [{
        "siteType": "ResAppraisal",
        "displayName": "Residential Appraisal",
        "featureID": "87",
        "featureName": "Valuation Services"
      }]
    },
    "loanPurposes": {
      "$id": "/definitions/loanPurposes",
      "type": "string",
      "enum": [
        "Renewal with no new money",
        "Renewal with new money",
        "Purchase",
        "Construction Loan",
        "Line of Credit",
        "Foreclosure",
        "SBA"
      ],
      "examples": [
        "SBA"
      ]
    },
    "propertyTypes": {
      "$id": "/definitions/propertyTypes",
      "type": "string",
      "enum": [
        "Agricultural",
        "Health Care",
        "Industrial",
        "Land",
        "Lodging/Hospitality",
        "Multi-family",
        "Office",
        "Residential",
        "Retail",
        "Senior Housing",
        "Special Purpose",
        "Sport/Entertainment"
      ],
      "examples": [
        "SBA"
      ]
    },
    "cabinets": {
      "$id": "/definitions/cabinets",
      "type": "string",
      "enum": [
        "Vendor 1",
        "Vendor 2"
      ],
      "examples": [
        "Vendor 1"
      ]
    }
  },
  "required": [
    "projectName",
    "cabinet",
    "loanNumber",
    "accountOfficer",
    "requestor",
    "loanAmount",
    "currency",
    "borrower",
    "loanPurpose",
    "collaterals"
  ]
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
   <projectName />
   <cabinet />
   <loanNumber />
   <accountOfficer />
   <requestor />
   <loanAmount />
   <currency />
   <borrower />
   <extended />
   <loanPurpose />
   <collaterals>
      <collateral>
         <addresses>
            <address>
                <street_address>string</street_address>
                <optional_address>string</optional_address>
                <city>string</city>
                <state>string</state>
                <stateAbbreviated>string</stateAbbreviated>
                <zip>string</zip>
                <country>string</country>
                <countryAbbreviated>string</countryAbbreviated>
                <primary>boolean</primary>
            </address>
         </addresses>
         <address2 />
         <city />
         <state />
         <stateAbbreviated />
         <zip />
         <country />
         <propertyType />
         <services />
         <extended />
      </collateral>
   </collaterals>
</serviceRequestForm>
```

```javascript
{
  "projectName": "string",
  "cabinet": "string",
  "loanNumber": "string",
  "accountOfficer": "string",
  "requestor": "string",
  "loanAmount": "number",
  "currency": "string",
  "borrower": "string",
  "loanPurpose": "string",
  "extended": {},
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
              "country_abbreviated": "string",
              "primary": "boolean"
          }
      ],
      "propertyType": "string",
      "services": [
        {
          "siteType": "ResAppraisal",
          "displayName": "Residential Appraisal",
          "featureID": "87",
          "featureName": "Valuation Services"
        }
      ],
      "extended": {}
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
          "$id": "http://example.com/example.json",
          "type": "object",
          "$schema": "http://json-schema.org/draft-07/schema#",
          "properties": {
            "projectName": {
              "$id": "/properties/projectName",
              "type": "string",
              "title": "The Projectname Schema ",
              "default": "",
              "examples": [
                "string"
              ]
            },
            "cabinet": {
              "$id": "/properties/cabinet",
              "type": "string",
              "title": "The Cabinet Schema ",
              "description": "C360 organized vendor information as Cabinets, much like a filing cabinet. Even if you have one vendor, you form data is organized by Cabinet Name.",
              "default": "",
              "enum": [],
              "$ref": "#/definitions/cabinets",
              "examples": [
                "string"
              ]
            },
            "loanNumber": {
              "$id": "/properties/loanNumber",
              "type": "string",
              "title": "The Loannumber Schema ",
              "default": "",
              "examples": [
                "string"
              ]
            },
            "accountOfficer": {
              "$id": "/properties/accountOfficer",
              "type": "string",
              "title": "The Accountofficer Schema ",
              "default": "",
              "examples": [
                "string"
              ]
            },
            "requestor": {
              "$id": "/properties/requestor",
              "type": "string",
              "title": "The Requestor Schema ",
              "default": "",
              "examples": [
                "string"
              ]
            },
            "loanAmount": {
              "$id": "/properties/loanAmount",
              "type": "number",
              "title": "The Loanamount Schema ",
              "default": 0.00,
              "examples": [
                1000.00
              ]
            },
            "currency": {
              "$id": "/properties/currency",
              "type": "string",
              "title": "The Currency Schema ",
              "default": "USD",
              "enum": [
                "USD"
              ],
              "examples": [
                "USD"
              ]
            },
            "borrower": {
              "$id": "/properties/borrower",
              "type": "string",
              "title": "The Borrower Schema ",
              "default": "",
              "examples": [
                "string"
              ]
            },
            "loanPurpose": {
              "$id": "/properties/loanPurpose",
              "type": "string",
              "title": "The Loanpurpose Schema ",
              "default": "",
              "$ref": "#/definitions/loanPurposes",
              "examples": [
                "SBA"
              ]
            },
            "extended": {
              "$id": "/properties/extended",
              "type": "object"
            },
            "collaterals": {
              "$id": "/properties/collaterals",
              "type": "array",
              "items": {
                "$id": "/properties/collaterals/items",
                "type": "object",
                "properties": {
                  "addresses": {
                    "$id": "/properties/collaterals/items/properties/addresses",
                    "title": "The Addresses Schema ",
                    "type": "array",
                    "default": "",
                    "items": {
                      "$ref": "#/definitions/addresses"
                    },
                    "examples": [
                      "string"
                    ]
                  },
                  "propertyType": {
                    "$id": "/properties/collaterals/items/properties/propertyType",
                    "type": "string",
                    "title": "The Propertytype Schema ",
                    "default": "",
                    "$ref": "#/definitions/propertyTypes",
                    "examples": [
                      "string"
                    ]
                  },
                  "services": {
                    "$id": "/properties/collaterals/items/properties/services",
                    "title": "The Services Schema ",
                    "type": "array",
                    "default": "",
                    "items": {
                      "$ref": "#/definitions/services"
                    },
                    "examples": [
                      "string"
                    ]
                  },
                  "extended": {
                    "$id": "/properties/collaterals/items/properties/extended",
                    "type": "object"
                  }
                },
                "required": [
                  "addresses",
                  "propertyType",
                  "services",
                  "extended"
                ]
              }
            }
          },
          "definitions": {
            "addresses": {
              "$id": "/definitions/addresses",
              "title": "Address",
              "type": "object",
              "properties": {
                "street_address": {
                  "$id": "/definitions/address/properties/street_address",
                  "type": "string",
                  "title": "The Street Address Schema ",
                  "default": "",
                  "example": [
                    "string"
                  ]
                },
                "optional_address": {
                  "$id": "/definitions/address/properties/extra_address",
                  "type": "string",
                  "title": "The Optional Address Schema ",
                  "default": "",
                  "example": [
                    "string"
                  ]
                },
                "city": {
                  "$id": "/definitions/address/properties/city",
                  "type": "string",
                  "title": "The City Schema ",
                  "default": "",
                  "example": [
                    "string"
                  ]
                },
                "state": {
                  "$id": "/definitions/address/properties/state",
                  "type": "string",
                  "title": "The State Schema ",
                  "default": "",
                  "enum": [
                    "Aguascalientes", "Alabama", "Alaska", "Alberta", "Arizona", "Arkansas", "Baja California", "Baja California Sur", "British Columbia", "California", "Campeche", "Chiapas", "Chihuahua", "Coahuila", "Colima", "Colorado", "Connecticut", "Delaware", "District of Columbia", "Durango", "Federal District", "Florida", "Georgia", "Guanajuato", "Guerrero", "Hawaii", "Hidalgo", "Idaho", "Illinois", "Indiana", "Iowa", "Jalisco", "Kansas", "Kentucky", "Louisiana", "Maine", "Manitoba", "Maryland", "Massachusetts", "Mexico State", "Michigan", "Michoacán", "Minnesota", "Mississippi", "Missouri", "Montana", "Morelos", "Nayarit", "Nebraska", "Nevada", "New Brunswick", "New Hampshire", "New Jersey", "New Mexico", "New York", "Newfoundland", "North Carolina", "North Dakota", "Northwest Territories", "Nova Scotia", "Nuevo León", "Nunavut", "Oaxaca", "Ohio", "Oklahoma", "Ontario", "Oregon", "Pennsylvania", "Prince Edward Island", "Puebla", "Puerto Rico", "Quebec", "Querétaro", "Quintana Roo", "Rhode Island", "San Luis Potosí", "Saskatchewan", "Sinaloa", "Sonora", "South Carolina", "South Dakota", "Tabasco", "Tamaulipas", "Tennessee", "Texas", "Tlaxcala", "Utah", "Veracruz", "Vermont", "Virginia", "Washington", "West Virginia", "Wisconsin", "Wyoming", "Yucatán", "Yukon Territory", "Zacatecas"
                  ],
                  "example": [
                    "string"
                  ]
                },
                "state_abbreviated": {
                  "$id": "/definitions/address/properties/state_abbreviated",
                  "type": "string",
                  "title": "The State Abbreviated Schema ",
                  "default": "",
                  "enum": [
                    "AB", "AGU", "AK", "AL", "AR", "AZ", "BC", "BCN", "BCS", "CA", "CAM", "CHH", "CHP", "CO", "COA", "COL", "CT", "DC", "DE", "DIF", "DUR", "FL", "GA", "GRO", "GUA", "HI", "HID", "IA", "ID", "IL", "IN", "JAL", "KS", "KY", "LA", "MA", "MB", "MD", "ME", "MEX", "MI", "MIC", "MN", "MO", "MOR", "MS", "MT", "NAY", "NB", "NC", "ND", "NE", "NH", "NJ", "NL", "NLE", "NM", "NS", "NT", "NU", "NV", "NY", "OAX", "OH", "OK", "ON", "OR", "PA", "PE", "PR", "PUE", "QC", "QUE", "RI", "ROO", "SC", "SD", "SIN", "SK", "SLP", "SON", "TAB", "TAM", "TLA", "TN", "TX", "UT", "VA", "VER", "VT", "WA", "WI", "WV", "WY", "YT", "YUC", "ZAC"
                  ],
                  "example": [
                    "string"
                  ]
                },
                "zip": {
                  "$id": "/definitions/address/properties/zip",
                  "type": "string",
                  "title": "The Zip Schema ",
                  "default": "",
                  "example": [
                    "string"
                  ]
                },
                "country": {
                  "$id": "/definitions/address/properties/country",
                  "type": "string",
                  "title": "The country Schema ",
                  "default": "United States",
                  "enum": [
                    "Afghanistan", "Albania", "Algeria", "American Samoa", "Andorra", "Angola", "Anguilla", "Antarctica", "Antigua and Barbuda", "Argentina", "Armenia", "Aruba", "Australia", "Austria", "Azerbaijan", "Bahamas, The", "Bahrain", "Bangladesh", "Barbados", "Belarus", "Belgium", "Belize", "Benin", "Bermuda", "Bhutan", "Bolivia", "Bosnia and Herzegovina", "Botswana", "Bouvet Island", "Brazil", "British Indian Ocean Territory", "British Virgin Islands", "Brunei", "Bulgaria", "Burkina Faso", "Burundi", "Cambodia", "Cameroon", "Canada", "Cape Verde", "Cayman Islands", "Central African Republic", "Chad", "Chile", "China", "Christmas Island", "Cocos (Keeling) Islands", "Colombia", "Comoros", "Congo", "Congo, Democratic Republic of the", "Cook Islands", "Costa Rica", "Croatia", "Cuba", "Cyprus", "Czech Republic", "Denmark", "Djibouti", "Dominica", "Dominican Republic", "East Timor", "Ecuador", "Egypt", "El Salvador", "Equatorial Guinea", "Eritrea", "Estonia", "Ethiopia", "Falkland Islands (Islas Malvinas)", "Faroe Islands", "Federated States of Micronesia", "Fiji", "Finland", "France", "French Guiana", "French Polynesia", "Gabon", "Gambia,The", "Georgia", "Germany", "Ghana", "Gibraltar", "Greece", "Greenland", "Grenada", "Guadeloupe", "Guam", "Guatemala", "Guernsey", "Guinea", "Guinea-Bissau", "Guyana", "Haiti", "Heard Island and McDonald Islands", "Honduras", "Hong Kong", "Hungary", "Iceland", "India", "Indonesia", "Iran", "Iraq", "Ireland", "Isle of Man", "Israel", "Italy", "Ivory Coast (Cote d'Ivoire)", "Jamaica", "Japan", "Jersey", "Jordan", "Kazakhstan", "Kenya", "Kiribati", "Kuwait", "Kyrgyzstan", "Laos", "Latvia", "Lebanon", "Lesotho", "Liberia", "Libya", "Liechtenstein", "Lithuania", "Luxembourg", "Macao", "Macedonia", "Madagascar", "Malawi", "Malaysia", "Maldives", "Mali", "Malta", "Marshall Islands", "Martinique", "Mauritania", "Mauritius", "Mayotte", "Mexico", "Moldova", "Monaco", "Mongolia", "Montenegro", "Montserrat", "Morocco", "Mozambique", "Myanmar (Burma)", "Namibia", "Nauru", "Nepal", "Netherlands", "Netherlands Antilles", "New Caledonia", "New Zealand", "Nicaragua", "Niger", "Nigeria", "Niue", "Norfolk Island", "North Korea", "Northern Mariana Islands", "Norway", "Oman", "Pakistan", "Palau", "Panama", "Papua New Guinea", "Paraguay", "Peru", "Philippines", "Pitcairn Islands", "Poland", "Portugal", "Puerto Rico", "Qatar", "Reunion", "Romania", "Russia", "Rwanda", "Samoa", "San Marino", "Sao Tome and Principe", "Saudi Arabia", "Senegal", "Serbia", "Seychelles", "Sierra Leone", "Singapore", "Slovakia", "Slovenia", "Solomon Islands", "Somalia", "South Africa", "South Georgia and the South Sandwich Islands", "South Korea", "Spain", "Sri Lanka", "St. Helena", "St. Kitts and Nevis", "St. Lucia", "St. Pierre and Miquelon", "St. Vincent and the Grenadines", "Sudan", "Suriname", "Swaziland", "Sweden", "Switzerland", "Syria", "Taiwan", "Tajikistan", "Tanzania, United Republic of", "Thailand", "Togo", "Tokelau", "Tonga", "Trinidad and Tobago", "Tunisia", "Turkey", "Turkmenistan", "Turks and Caicos Islands", "Tuvalu", "Uganda", "Ukraine", "United Arab Emirates", "United Kingdom", "United States", "Uruguay", "Uzbekistan", "Vanuatu", "Vatican City (Holy See)", "Venezuela", "Vietnam", "Virgin Islands (US)", "Wallis and Futuna", "Western Sahara", "Yemen", "Zambia", "Zimbabwe"
                  ],
                  "example": [
                    "United States"
                  ]
                },
                "countryAbbreviated": {
                  "$id": "/definitions/address/properties/countryAbbreviated",
                  "type": "string",
                  "title": "The country Schema ",
                  "default": "United States",
                  "enum": [
                    "AA", "AC", "AE", "AF", "AG", "AJ", "AL", "AM", "AN", "AO", "AQ", "AR", "AS", "AU", "AV", "AY", "BA", "BB", "BC", "BD", "BE", "BF", "BG", "BH", "BK", "BL", "BM", "BN", "BO", "BP", "BR", "BT", "BU", "BV", "BX", "BY", "CA", "CB", "CD", "CE", "CF", "CG", "CH", "CI", "CJ", "CK", "CM", "CN", "CO", "CQ", "CS", "CT", "CU", "CV", "CW", "CY", "DA", "DJ", "DO", "DR", "EC", "EG", "EI", "EK", "EN", "ER", "ES", "ET", "EZ", "FG", "FI", "FJ", "FK", "FM", "FO", "FP", "FR", "GA", "GB", "GG", "GH", "GI", "GJ", "GK", "GL", "GM", "GP", "GQ", "GR", "GT", "GV", "GY", "HA", "HK", "HM", "HO", "HR", "HU", "IC", "ID", "IM", "IN", "IO", "IR", "IS", "IT", "IT", "IV", "IZ", "JA", "JE", "JM", "JO", "KE", "KG", "KN", "KR", "KS", "KT", "KU", "KZ", "LA", "LE", "LG", "LH", "LI", "LO", "LS", "LT", "LU", "LY", "MA", "MB", "MC", "MD", "MF", "MG", "MH", "MI", "MJ", "MK", "ML", "MN", "MO", "MP", "MR", "MT", "MU", "MV", "MX", "MY", "MZ", "NC", "NE", "NF", "NG", "NH", "NI", "NL", "NO", "NP", "NR", "NS", "NT", "NU", "NZ", "PA", "PC", "PE", "PK", "PL", "PM", "PO", "PP", "PS", "PU", "QA", "RB", "RE", "RM", "RO", "RP", "RQ", "RS", "RW", "SA", "SB", "SC", "SE", "SF", "SG", "SH", "SI", "SL", "SM", "SN", "SO", "SP", "ST", "SU", "SW", "SX", "SY", "SZ", "TD", "TH", "TI", "TK", "TL", "TN", "TO", "TP", "TS", "TT", "TU", "TV", "TW", "TX", "TZ", "UG", "UK", "UP", "US", "UV", "UY", "UZ", "VC", "VE", "VI", "VM", "VQ", "WA", "WF", "WI", "WS", "WZ", "YM", "ZA", "ZI"
                  ],
                  "example": [
                    "United States"
                  ]
                },
                "primary": {
                  "$id": "/definitions/address/properties/primary",
                  "type": "boolean",
                  "title": "The Primary Schema ",
                  "default": false,
                  "example": [
                    false
                  ]
                }
              },
              "required": [
                "street_address",
                "optional_address",
                "city",
                "state",
                "state_abbreviated",
                "zip",
                "country",
                "default"
              ]
            },
            "services": {
              "$id": "/definitions/services",
              "type": "object",
              "default": "",
              "enum": [{
                  "siteType": "PhaseI",
                  "displayName": "Phase I Environmental Site Assessment",
                  "featureID": "81",
                  "featureName": "Procure New Services"
                },
                {
                  "siteType": "ASTMPCA",
                  "displayName": "ASTM Property Condition Assessment",
                  "featureID": "122",
                  "featureName": "Procure New Services"
                },
                {
                  "siteType": "Appraisal",
                  "displayName": "Commercial Appraisal Report",
                  "featureID": "87",
                  "featureName": "Valuation Services"
                },
                {
                  "siteType": "AppraisalRev",
                  "displayName": "Commercial Appraisal Review",
                  "featureID": "87",
                  "featureName": "Valuation Services"
                },
                {
                  "siteType": "Evaluation",
                  "displayName": "Commercial Evaluation",
                  "featureID": "87",
                  "featureName": "Valuation Services"
                },
                {
                  "siteType": "LoanChkPlus",
                  "displayName": "Loan Check Plus",
                  "featureID": "81",
                  "featureName": "Procure New Services"
                },
                {
                  "siteType": "PhaseII",
                  "displayName": "Phase II Environmental Site Assessment",
                  "featureName": "81",
                  "": "Procure New Services"
                },
                {
                  "siteType": "ASTM",
                  "displayName": "ASTM Transaction Screen",
                  "featureID": "81",
                  "featureName": "Procure New Services"
                },
                {
                  "siteType": "DBReview",
                  "displayName": "Database Review",
                  "featureID": "81",
                  "featureName": "Procure New Services"
                },
                {
                  "siteType": "ResAppraisal",
                  "displayName": "Residential Appraisal",
                  "featureID": "87",
                  "featureName": "Valuation Services"
                }
              ],
              "examples": [{
                "siteType": "ResAppraisal",
                "displayName": "Residential Appraisal",
                "featureID": "87",
                "featureName": "Valuation Services"
              }]
            },
            "loanPurposes": {
              "$id": "/definitions/loanPurposes",
              "type": "string",
              "enum": [
                "Renewal with no new money",
                "Renewal with new money",
                "Purchase",
                "Construction Loan",
                "Line of Credit",
                "Foreclosure",
                "SBA"
              ],
              "examples": [
                "SBA"
              ]
            },
            "propertyTypes": {
              "$id": "/definitions/propertyTypes",
              "type": "string",
              "enum": [
                "Agricultural",
                "Health Care",
                "Industrial",
                "Land",
                "Lodging/Hospitality",
                "Multi-family",
                "Office",
                "Residential",
                "Retail",
                "Senior Housing",
                "Special Purpose",
                "Sport/Entertainment"
              ],
              "examples": [
                "SBA"
              ]
            },
            "cabinets": {
              "$id": "/definitions/cabinets",
              "type": "string",
              "enum": [
                "Vendor 1",
                "Vendor 2"
              ],
              "examples": [
                "Vendor 1"
              ]
            }
          },
          "required": [
            "projectName",
            "loanNumber",
            "accountOfficer",
            "requestor",
            "loanAmount",
            "currency",
            "borrower",
            "loanPurpose",
            "collaterals"
          ]
        }
      },
      "dataTemplates": {
        "JSON": {
          "meta": {
            "dataType": "json"
          },
          "serviceRequestData": {
            "projectName": "string",
            "cabinet": "string",
            "loanNumber": "string",
            "accountOfficer": "string",
            "requestor": "string",
            "loanAmount": 1000000.00,
            "currency": "USD",
            "borrower": "string",
            "loanPurpose": "string",
            "extended": {
              "lotSize": "3 acres",
              "parking": "garage"
            },
            "collaterals": [{
              "addresses": [{
                "street_address": "string",
                "optional_address": "string",
                "city": "string",
                "state": "string",
                "stateAbbreviated": "string",
                "zip": "string",
                "country": "string",
                "countryAbbreviated": "string",
                "primary": "boolean"
              }],
              "propertyType": "string",
              "services": [],
              "extended": {
                "lon": "",
                "lat": "",
                "tax": "abated"
              }
            }]
          }
        },
        "XML": "<?xml version="1.0" encoding="UTF-8"?>
            <serviceRequestForm>
                <meta>
                    <dataType>json</dataType>
                </meta>
                <serviceRequestData>
                    <accountOfficer>string</accountOfficer>
                    <cabinet>string</cabinet>
                    <borrower>string</borrower>
                    <collaterals>
                        <collateral>
                            <addresses>
                                <address>
                                    <street_address>string</street_address>
                                    <optional_address>string</optional_address>
                                    <city>string</city>
                                    <state>string</state>
                                    <stateAbbreviated>string</stateAbbreviated>
                                    <zip>string</zip>
                                    <country>string</country>
                                    <countryAbbreviated>string</countryAbbreviated>
                                    <primary>boolean</primary>
                                </address>
                            </addresses>
                            <extended>
                                <lat />
                                <lon />
                                <tax>abated</tax>
                            </extended>
                            <propertyType>string</propertyType>
                            <services>
                                <service />
                            </services>
                        </collateral>
                    </collaterals>
                    <extended>
                        <lotSize>3 acres</lotSize>
                        <parking>garage</parking>
                    </extended>
                    <loanAmount>1000.00</loanAmount>
                    <loanNumber>string</loanNumber>
                    <currency>USD</currency>
                    <loanPurpose>string</loanPurpose>
                    <projectName>string</projectName>
                    <requestor>string</requestor>
                </serviceRequestData>
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
