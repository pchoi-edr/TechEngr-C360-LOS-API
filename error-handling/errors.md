# Errors

This API uses standard HTTP status codes to indicate the status of a response.

There are two main categories of error responses. Each have a different response payload structure.

```javascript
{
    "meta": {
        "responseCode": 400,
        "description": "Could not process",
        "reason": "Bad Request"
    },
    "data": null
}
```

## Code

Codes will be provided from [Error Codes](errors-codes.md).

## Description

When possible EDR will provide a detailed description as provided by the system for the error.

## Reason

The reasons can range from but limited to the following list.

| Reason | Description |
|:-------|:------------|
| Bad Request | Bad Request pertains to situations a fault is generated due to a query string or parameter |
| Forbidden | Pertains to operations which are forbidden by the client |
