# Errors Codes

### Simple Errors {#simple-errors}

| **Name** | **Code** | **Description** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Bad request | 400 | The request was unacceptable |
| Unauthorized | 401 | The request has not been applied because it lacks valid authentication credentials for the target resource. |
| Forbidden | 403 | The server understood the request, but is refusing to fulfill it |
| Not Found | 404 | The server has not found anything matching the request URI |
| Not acceptable | 406 | The server is unable to return a response in the format that was requested by the client |
| Unsupported Media Type | 415 | The server is refusing to service the request because the entity of the request is in a format not supported by the requested resource for the requested method |
| Too many requests | 429 | Too many requests hit the API too quickly |
| Server error | 500 | A technical error occured in Restlet Cloud |

### Detailed Errors {#detailed-errors}

| **Name** | **Code** | **Description** |
| --- | --- |
| Unprocessable entity | 422 | The server understands the content type of the request entity, and the syntax of the request entity is correct, but was unable to process the contained instructions. |

​

