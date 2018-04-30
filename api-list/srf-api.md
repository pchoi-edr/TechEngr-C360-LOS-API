# SRF API

## <span style="background-color: #5493dc; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">PUT</span> **Service Request Details**

```text
/v1/api/srf/:serivceRequestID
```

### Request

#### Path Parameters

| Path Parameter | Type | Description |
| :--- | :--- | :--- |
| serivceRequestID | Int | Service Request ID |

#### Body Parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |


### Response

```javascript
{
    "serivceRequestID": 1234567,
    "loanID": null,
    "locations": []
}
```

## <span style="background-color: #ebb747; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">POST</span> **Service Request Details**

```text
/v1/api/srf
```

### Request

#### Body Parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |


### Response

```javascript
{
    "serivceRequestID": 1234567,
    "loanID": null,
    "locations": []
}
```

