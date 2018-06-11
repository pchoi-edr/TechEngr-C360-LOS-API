# Errors

To simplify processing by client applications, the API will always attempt to return an HTTP response with a "200 OK" HTTP status code in its headers. The contents of the response can then be read to determine if the API request was successfully executed.

The API response's payload will contain a data element with a value equal to the HTTP status code that represents the result of the API server's attempt to process the request. For example, if an internal server error occurs within the API server itself, the API response will be returned with an "200 OK" HTTP status code in its headers, but the data in the response will indicate that a "500 Internal Server Error" actually occurred.

There are two main categories of error responses. Each has a different response payload structure.

```javascript
{
    "response": {
        "code": 400,
        "reason": "Bad Request"
        "description": "Could not process",
    },
    "data": null
}
```

## Code

This data element contains the HTTP status code that the response should be treated as (even though the response's HTTP headers actually contain a "200 OK" status code). The list of possible status codes is described in the IETF (Internet Engineering Task Force) HTTP 1.1 specification and its associated RFCs, but a partial list of common responses from the API server can be found in the [Error Codes](errors-codes.md) section.

## Reason

The reason is the brief textual name of the HTTP status code returned from the API in the `code` data element. For example, a non-exhaustive list follows:

| Reason | Description |
|:-------|:------------|
| Bad Request | Pertains to situations where a fault is generated due to an incorrect query string or parameter |
| Forbidden | Pertains to operations which are forbidden from the client |

## Description

When possible, EDR will provide a detailed description as provided by the system for the error.
