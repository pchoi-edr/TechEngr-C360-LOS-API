# SRF Status API

## <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span> **Service Request Details**

```text
/v1/api/status/:serivceRequestID
```

```text
/v1/api/status/:loanID
```

### Request

#### Path Parameters

> Path parameters can use either serviceRequestID or loanID but not both.

| Path Parameter | Type | Description |
| :--- | :--- | :--- |
| serivceRequestID | Int | Service Request ID |
| loanID | Int | Loan ID |

> locationID can be used alone to retrieve all service related data or with a specific serviceID to return status on one service item.

#### GET Parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| locationID | Int | Location ID |
| serviceID | Int | Service ID |

> Sample status requests with locationID usage and locationID & serviceID usage.

```text
/v1/api/status/:serivceRequestID?locationID=1234567
```

```text
/v1/api/status/:serivceRequestID?locationID=1234567&serviceID=1234567
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
        "{serviceRequestID}": [
            {
            "locationID": {locationID},
            "address": [
                {
                    "street_address": "123 street",
                    "optional_address": "Suite #1",
                    "city": "city",
                    "state": "state",
                    "stateAbbreviated": "stateAbbreviated",
                    "zip": "zip",
                    "country": "country",
                    "countryAbbreviated": "countryAbbreviated"
                }
            ],
            "status": "Pending",
            "services": [
                {
                "serviceID": {serviceID},
                "jobNumber": "11-1111111",
                "status": "Pending",
                "fee": null,
                "startDate": "12-13-2018 10:10:10",
                "dueDate": "12-13-2018 10:10:10",
                "completeDate": "12-13-2018 10:10:10",
                "createdAt": "",
                "updatedAt": ""
                }
            ]
            },
            {
            "locationID": {locationID},
            "address": [
                {
                    "street_address": "123 street",
                    "optional_address": "Suite #1",
                    "city": "city",
                    "state": "state",
                    "stateAbbreviated": "stateAbbreviated",
                    "zip": "zip",
                    "country": "country",
                    "countryAbbreviated": "countryAbbreviated"
                }
            ],
            "status": "Hold",
            "services": [
                {
                "serviceID": {serviceID},
                "jobNumber": "11-1111111",
                "status": "Hold",
                "fee": null,
                "startDate": "12-13-2018 10:10:10",
                "dueDate": "12-13-2018 10:10:10",
                "completeDate": "12-13-2018 10:10:10",
                }
            ]
            }
        ],
        "meta": {}
    }
}
```
