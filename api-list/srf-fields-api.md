# SRF Fields API

The SRF Fields API will return a template of JSON or XML data schema. It will be up to the developer to make sure they provide proper data according to the JSON Schema in order to properly create a SRF within C360.

### JSON Schema Model

This JSON Schema represents the minimal data requirements and the required fields

```javascript
{
  "$id": "http://example.com/example.json",
  "type": "object",
  "definitions": {},
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
      "default": "0.00",
      "examples": [
        "1000.00"
      ]
    },
    "currency": {
      "$id": "/properties/currency",
      "type": "string",
      "title": "The Currency Schema ",
      "default": "USD",
      "items": {
        "type": "string",
        "enum": ["USD"]
      }
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
      "examples": [
        "string"
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
          "address1": {
            "$id": "/properties/collaterals/items/properties/address1",
            "type": "string",
            "title": "The Address1 Schema ",
            "default": "",
            "examples": [
              "string"
            ]
          },
          "address2": {
            "$id": "/properties/collaterals/items/properties/address2",
            "type": "string",
            "title": "The Address2 Schema ",
            "default": "",
            "examples": [
              "string"
            ]
          },
          "city": {
            "$id": "/properties/collaterals/items/properties/city",
            "type": "string",
            "title": "The City Schema ",
            "default": "",
            "examples": [
              "string"
            ]
          },
          "state": {
            "$id": "/properties/collaterals/items/properties/state",
            "type": "string",
            "title": "The State Schema ",
            "default": "",
            "items": {
              "type": "string",
              "enum": [
                  "Aguascalientes","Alabama","Alaska","Alberta","Arizona","Arkansas","Baja California","Baja California Sur","British Columbia","California","Campeche","Chiapas","Chihuahua","Coahuila","Colima","Colorado","Connecticut","Delaware","District of Columbia","Durango","Federal District","Florida","Georgia","Guanajuato","Guerrero","Hawaii","Hidalgo","Idaho","Illinois","Indiana","Iowa","Jalisco","Kansas","Kentucky","Louisiana","Maine","Manitoba","Maryland","Massachusetts","Mexico State","Michigan","Michoacán","Minnesota","Mississippi","Missouri","Montana","Morelos","Nayarit","Nebraska","Nevada","New Brunswick","New Hampshire","New Jersey","New Mexico","New York","Newfoundland","North Carolina","North Dakota","Northwest Territories","Nova Scotia","Nuevo León","Nunavut","Oaxaca","Ohio","Oklahoma","Ontario","Oregon","Pennsylvania","Prince Edward Island","Puebla","Puerto Rico","Quebec","Querétaro","Quintana Roo","Rhode Island","San Luis Potosí","Saskatchewan","Sinaloa","Sonora","South Carolina","South Dakota","Tabasco","Tamaulipas","Tennessee","Texas","Tlaxcala","Utah","Veracruz","Vermont","Virginia","Washington","West Virginia","Wisconsin","Wyoming","Yucatán","Yukon Territory","Zacatecas"
              ]
            }
            "examples": [
              "string"
            ]
          },
          "stateAbbreviated": {
            "$id": "/properties/collaterals/items/properties/stateAbbreviated",
            "type": "string",
            "title": "The Stateabbreviated Schema ",
            "default": "",
            "items": {
              "type": "string",
              "enum": [
                  "AB","AGU","AK","AL","AR","AZ","BC","BCN","BCS","CA","CAM","CHH","CHP","CO","COA","COL","CT","DC","DE","DIF","DUR","FL","GA","GRO","GUA","HI","HID","IA","ID","IL","IN","JAL","KS","KY","LA","MA","MB","MD","ME","MEX","MI","MIC","MN","MO","MOR","MS","MT","NAY","NB","NC","ND","NE","NH","NJ","NL","NLE","NM","NS","NT","NU","NV","NY","OAX","OH","OK","ON","OR","PA","PE","PR","PUE","QC","QUE","RI","ROO","SC","SD","SIN","SK","SLP","SON","TAB","TAM","TLA","TN","TX","UT","VA","VER","VT","WA","WI","WV","WY","YT","YUC","ZAC"
              ]
            }
            "examples": [
              "string"
            ]
          },
          "zip": {
            "$id": "/properties/collaterals/items/properties/zip",
            "type": "string",
            "title": "The Zip Schema ",
            "default": "",
            "examples": [
              "string"
            ]
          },
          "country": {
            "$id": "/properties/collaterals/items/properties/country",
            "type": "string",
            "title": "The Country Schema ",
            "default": "United States",
            "items": {
              "type": "string",
              "enum": [
                  "Afghanistan","Albania","Algeria","American Samoa","Andorra","Angola","Anguilla","Antarctica","Antigua and Barbuda","Argentina","Armenia","Aruba","Australia","Austria","Azerbaijan","Bahamas, The","Bahrain","Bangladesh","Barbados","Belarus","Belgium","Belize","Benin","Bermuda","Bhutan","Bolivia","Bosnia and Herzegovina","Botswana","Bouvet Island","Brazil","British Indian Ocean Territory","British Virgin Islands","Brunei","Bulgaria","Burkina Faso","Burundi","Cambodia","Cameroon","Canada","Cape Verde","Cayman Islands","Central African Republic","Chad","Chile","China","Christmas Island","Cocos (Keeling) Islands","Colombia","Comoros","Congo","Congo, Democratic Republic of the","Cook Islands","Costa Rica","Croatia","Cuba","Cyprus","Czech Republic","Denmark","Djibouti","Dominica","Dominican Republic","East Timor","Ecuador","Egypt","El Salvador","Equatorial Guinea","Eritrea","Estonia","Ethiopia","Falkland Islands (Islas Malvinas)","Faroe Islands","Federated States of Micronesia","Fiji","Finland","France","French Guiana","French Polynesia","Gabon","Gambia,The","Georgia","Germany","Ghana","Gibraltar","Greece","Greenland","Grenada","Guadeloupe","Guam","Guatemala","Guernsey","Guinea","Guinea-Bissau","Guyana","Haiti","Heard Island and McDonald Islands","Honduras","Hong Kong","Hungary","Iceland","India","Indonesia","Iran","Iraq","Ireland","Isle of Man","Israel","Italy","Ivory Coast (Cote d'Ivoire)","Jamaica","Japan","Jersey","Jordan","Kazakhstan","Kenya","Kiribati","Kuwait","Kyrgyzstan","Laos","Latvia","Lebanon","Lesotho","Liberia","Libya","Liechtenstein","Lithuania","Luxembourg","Macao","Macedonia","Madagascar","Malawi","Malaysia","Maldives","Mali","Malta","Marshall Islands","Martinique","Mauritania","Mauritius","Mayotte","Mexico","Moldova","Monaco","Mongolia","Montenegro","Montserrat","Morocco","Mozambique","Myanmar (Burma)","Namibia","Nauru","Nepal","Netherlands","Netherlands Antilles","New Caledonia","New Zealand","Nicaragua","Niger","Nigeria","Niue","Norfolk Island","North Korea","Northern Mariana Islands","Norway","Oman","Pakistan","Palau","Panama","Papua New Guinea","Paraguay","Peru","Philippines","Pitcairn Islands","Poland","Portugal","Puerto Rico","Qatar","Reunion","Romania","Russia","Rwanda","Samoa","San Marino","Sao Tome and Principe","Saudi Arabia","Senegal","Serbia","Seychelles","Sierra Leone","Singapore","Slovakia","Slovenia","Solomon Islands","Somalia","South Africa","South Georgia and the South Sandwich Islands","South Korea","Spain","Sri Lanka","St. Helena","St. Kitts and Nevis","St. Lucia","St. Pierre and Miquelon","St. Vincent and the Grenadines","Sudan","Suriname","Swaziland","Sweden","Switzerland","Syria","Taiwan","Tajikistan","Tanzania, United Republic of","Thailand","Togo","Tokelau","Tonga","Trinidad and Tobago","Tunisia","Turkey","Turkmenistan","Turks and Caicos Islands","Tuvalu","Uganda","Ukraine","United Arab Emirates","United Kingdom","United States","Uruguay","Uzbekistan","Vanuatu","Vatican City (Holy See)","Venezuela","Vietnam","Virgin Islands (US)","Wallis and Futuna","Western Sahara","Yemen","Zambia","Zimbabwe"
              ]
            }
            "examples": [
              "string"
            ]
          },
          "propertyType": {
            "$id": "/properties/collaterals/items/properties/propertyType",
            "type": "string",
            "title": "The Propertytype Schema ",
            "default": "",
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
        "address1",
        "address2",
        "city",
        "state",
        "zip",
        "propertyType",
        "extended"
        ]
      }
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
```

#### Collateral Model

This JSON Schema represents the Collateral Data Model.

```javascript
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "address1": {
        "$id": "/properties/collaterals/items/properties/address1",
        "type": "string",
        "title": "The Address1 Schema ",
        "default": "",
        "examples": [
            "string"
        ]
    },
    "address2": {
        "$id": "/properties/collaterals/items/properties/address2",
        "type": "string",
        "title": "The Address2 Schema ",
        "default": "",
        "examples": [
            "string"
        ]
    },
    "city": {
        "$id": "/properties/collaterals/items/properties/city",
        "type": "string",
        "title": "The City Schema ",
        "default": "",
        "examples": [
            "string"
        ]
    },
    "state": {
        "$id": "/properties/collaterals/items/properties/state",
        "type": "string",
        "title": "The State Schema ",
        "default": "",
        "items": {
            "type": "string",
            "enum": [
                "Aguascalientes","Alabama","Alaska","Alberta","Arizona","Arkansas","Baja California","Baja California Sur","British Columbia","California","Campeche","Chiapas","Chihuahua","Coahuila","Colima","Colorado","Connecticut","Delaware","District of Columbia","Durango","Federal District","Florida","Georgia","Guanajuato","Guerrero","Hawaii","Hidalgo","Idaho","Illinois","Indiana","Iowa","Jalisco","Kansas","Kentucky","Louisiana","Maine","Manitoba","Maryland","Massachusetts","Mexico State","Michigan","Michoacán","Minnesota","Mississippi","Missouri","Montana","Morelos","Nayarit","Nebraska","Nevada","New Brunswick","New Hampshire","New Jersey","New Mexico","New York","Newfoundland","North Carolina","North Dakota","Northwest Territories","Nova Scotia","Nuevo León","Nunavut","Oaxaca","Ohio","Oklahoma","Ontario","Oregon","Pennsylvania","Prince Edward Island","Puebla","Puerto Rico","Quebec","Querétaro","Quintana Roo","Rhode Island","San Luis Potosí","Saskatchewan","Sinaloa","Sonora","South Carolina","South Dakota","Tabasco","Tamaulipas","Tennessee","Texas","Tlaxcala","Utah","Veracruz","Vermont","Virginia","Washington","West Virginia","Wisconsin","Wyoming","Yucatán","Yukon Territory","Zacatecas"
            ]
        }
        "examples": [
            "string"
        ]
    },
    "stateAbbreviated": {
        "$id": "/properties/collaterals/items/properties/stateAbbreviated",
        "type": "string",
        "title": "The Stateabbreviated Schema ",
        "default": "",
        "items": {
            "type": "string",
            "enum": [
                "AB","AGU","AK","AL","AR","AZ","BC","BCN","BCS","CA","CAM","CHH","CHP","CO","COA","COL","CT","DC","DE","DIF","DUR","FL","GA","GRO","GUA","HI","HID","IA","ID","IL","IN","JAL","KS","KY","LA","MA","MB","MD","ME","MEX","MI","MIC","MN","MO","MOR","MS","MT","NAY","NB","NC","ND","NE","NH","NJ","NL","NLE","NM","NS","NT","NU","NV","NY","OAX","OH","OK","ON","OR","PA","PE","PR","PUE","QC","QUE","RI","ROO","SC","SD","SIN","SK","SLP","SON","TAB","TAM","TLA","TN","TX","UT","VA","VER","VT","WA","WI","WV","WY","YT","YUC","ZAC"
            ]
        }
        "examples": [
            "string"
        ]
    },
    "zip": {
        "$id": "/properties/collaterals/items/properties/zip",
        "type": "string",
        "title": "The Zip Schema ",
        "default": "",
        "examples": [
            "string"
        ]
    },
    "country": {
        "$id": "/properties/collaterals/items/properties/country",
        "type": "string",
        "title": "The Country Schema ",
        "default": "United States",
        "items": {
            "type": "string",
            "enum": [
                "Afghanistan","Albania","Algeria","American Samoa","Andorra","Angola","Anguilla","Antarctica","Antigua and Barbuda","Argentina","Armenia","Aruba","Australia","Austria","Azerbaijan","Bahamas, The","Bahrain","Bangladesh","Barbados","Belarus","Belgium","Belize","Benin","Bermuda","Bhutan","Bolivia","Bosnia and Herzegovina","Botswana","Bouvet Island","Brazil","British Indian Ocean Territory","British Virgin Islands","Brunei","Bulgaria","Burkina Faso","Burundi","Cambodia","Cameroon","Canada","Cape Verde","Cayman Islands","Central African Republic","Chad","Chile","China","Christmas Island","Cocos (Keeling) Islands","Colombia","Comoros","Congo","Congo, Democratic Republic of the","Cook Islands","Costa Rica","Croatia","Cuba","Cyprus","Czech Republic","Denmark","Djibouti","Dominica","Dominican Republic","East Timor","Ecuador","Egypt","El Salvador","Equatorial Guinea","Eritrea","Estonia","Ethiopia","Falkland Islands (Islas Malvinas)","Faroe Islands","Federated States of Micronesia","Fiji","Finland","France","French Guiana","French Polynesia","Gabon","Gambia,The","Georgia","Germany","Ghana","Gibraltar","Greece","Greenland","Grenada","Guadeloupe","Guam","Guatemala","Guernsey","Guinea","Guinea-Bissau","Guyana","Haiti","Heard Island and McDonald Islands","Honduras","Hong Kong","Hungary","Iceland","India","Indonesia","Iran","Iraq","Ireland","Isle of Man","Israel","Italy","Ivory Coast (Cote d'Ivoire)","Jamaica","Japan","Jersey","Jordan","Kazakhstan","Kenya","Kiribati","Kuwait","Kyrgyzstan","Laos","Latvia","Lebanon","Lesotho","Liberia","Libya","Liechtenstein","Lithuania","Luxembourg","Macao","Macedonia","Madagascar","Malawi","Malaysia","Maldives","Mali","Malta","Marshall Islands","Martinique","Mauritania","Mauritius","Mayotte","Mexico","Moldova","Monaco","Mongolia","Montenegro","Montserrat","Morocco","Mozambique","Myanmar (Burma)","Namibia","Nauru","Nepal","Netherlands","Netherlands Antilles","New Caledonia","New Zealand","Nicaragua","Niger","Nigeria","Niue","Norfolk Island","North Korea","Northern Mariana Islands","Norway","Oman","Pakistan","Palau","Panama","Papua New Guinea","Paraguay","Peru","Philippines","Pitcairn Islands","Poland","Portugal","Puerto Rico","Qatar","Reunion","Romania","Russia","Rwanda","Samoa","San Marino","Sao Tome and Principe","Saudi Arabia","Senegal","Serbia","Seychelles","Sierra Leone","Singapore","Slovakia","Slovenia","Solomon Islands","Somalia","South Africa","South Georgia and the South Sandwich Islands","South Korea","Spain","Sri Lanka","St. Helena","St. Kitts and Nevis","St. Lucia","St. Pierre and Miquelon","St. Vincent and the Grenadines","Sudan","Suriname","Swaziland","Sweden","Switzerland","Syria","Taiwan","Tajikistan","Tanzania, United Republic of","Thailand","Togo","Tokelau","Tonga","Trinidad and Tobago","Tunisia","Turkey","Turkmenistan","Turks and Caicos Islands","Tuvalu","Uganda","Ukraine","United Arab Emirates","United Kingdom","United States","Uruguay","Uzbekistan","Vanuatu","Vatican City (Holy See)","Venezuela","Vietnam","Virgin Islands (US)","Wallis and Futuna","Western Sahara","Yemen","Zambia","Zimbabwe"
            ]
        }
        "examples": [
            "string"
        ]
    },
    "propertyType": {
        "$id": "/properties/collaterals/items/properties/propertyType",
        "type": "string",
        "title": "The Propertytype Schema ",
        "default": "",
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
    "address1",
    "address2",
    "city",
    "state",
    "zip",
    "propertyType"
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
         <address1 />
         <address2 />
         <city />
         <state />
         <stateAbbreviated />
         <zip />
         <country />
         <propertyType />
         <extended />
      </collateral>
   </collaterals>
</serviceRequestForm>
```

```javascript
{
  "projectName": "string",
  "loanNumber": "string",
  "accountOfficer": "string",
  "requestor": "string",
  "loanAmount": "number",
  "currency": "array",
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
      "country": "string",
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
                "projectName": "string",
                "loanNumber": "string",
                "accountOfficer": "string",
                "requestor": "string",
                "loanAmount": "number",
                "currency": "USD",
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
                        "country": "string",
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
                    <loanAmount>1000.00</loanAmount>
                    <loanNumber>string</loanNumber>
                    <currency>USD</currency>
                    <loanPurpose>string</loanPurpose>
                    <projectName>string</projectName>
                    <requestor>string</requestor>
                </serviceRequestData>
            </serviceRequestForm>
        "
    }
}
```

## C360 Cabinets

C360 organizes loan information as Cabinets, much like a filing cabinet. Even if you have one loan, you form data is organized by Cabinet Name.

{need more info}

## Custom Fields

Within C360, we have provide a means to provide custom fields. Custom Fields can to added to the data schema by adding to the "extended" object either as objects or xml tags when submitting new data.
