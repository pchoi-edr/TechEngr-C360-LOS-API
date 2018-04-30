# SRF API

<span style="background-color: #5493dc; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 10px;">PUT</span> **PUT Service Request Details**

```
/v1/api/srf/:serivceRequestID

```

### Request

##### Path Parameters

| Path Parameter | Type | Description |
|:---------------|:-----|:------------|
|serivceRequestID| Int  |             |

##### Body Parameters

| Parameter      | Type | Description |
|:---------------|:-----|:------------|

### Response

```javascript
{
    "serivceRequestID": 1234567,
    "loanID": null,
    "locations": []
}

```

---

<span style="background-color: #ebb747; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 10px;">POST</span> **Post Service Request Details**

```
/v1/api/srf

```

### Request

##### Path Parameters

| Path Parameter | Type | Description |
|:---------------|:-----|:------------|

##### Body Parameters

| Parameter      | Type | Description |
|:---------------|:-----|:------------|

### Response

```javascript
{
    "serivceRequestID": 1234567,
    "loanID": null,
    "locations": []
}

```
