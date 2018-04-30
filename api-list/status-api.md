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
            "address1": "123 street",
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
