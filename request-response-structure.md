# API Data Structures

With the exception of authentication-related API endpoints,
the HTTP body contents of every request to--or response
from--the LOS API conforms to the following general JSON structure:

```
{
    "meta" : {},
    "data" : {}
}
```

However, note that some API endpoints use an HTTP method that
expects no body content (_e.g._ `GET` requests). In these cases,
you should not supply any HTTP body content to the API server.

Note also that the order of fields in the response is subject
to change. Your application should never assume that fields will
always be returned in the same order unless this specification
explicitly indicates that a particular data element will always
be returned in a given order by design.

## Contents of the `meta` and `data` Elements.

The contents of the `meta` and `data` elements will always be
specific to the individual API endpoint being invoked. As such,
you must refer to each API endpoint's documentation for the
specific values that are expected in these elements. 

The distinction between the contents of the _meta_ and _data_
elements is a semantic one that depends on the context of each
API endpoint. If general, the `data` element will contains the
primary data being sent or received, and the `meta` element will
contain supporting metadata that is in some way ancillary to
or descriptive of the data in the `data` element.

## API Request `Content-Type` Header

All API requests must contain a valid HTTP `Content-Type` header
with a format that the API server supports. Currently, this must
be as follows:

    Content-Type: application/json

## HTTP Response Status Codes of API Responses

The API server will do its best to process any request it
receives. Whenever possible, it will return its responses
with HTTP response status codes of either 200 (indicating
success) or 303 (indicating a URL where a downloadable
resource is available).

Note that this is also true if an error occurs (inasmuch as
this is feasible). For example, if an API request is
malformed but was received by the API server, then an HTTP
server would normally return 400 HTTP response status code
(representing a "Bad Request" error). However, the LOS API
will instead return a 200 HTTP response status code (indicating
success), and will instead supply a 400 HTTP response status
code in the `responseCode` datum in its `meta` element. 

# API Response Structure

Every API response that contains HTTP body content will have
the following values in its `meta` element:

* The `date` datum will contain the date when the API response
  was processed, per ISO 8601. This date will always be
  expressed in UTC (Universal Coördinated Time) with a Zulu
  suffix. For example:
  
      2018-06-21T21:57:57Z
  
* The `function` datum is a semantically meaningful,
  human-readable string that describes the nature of either
  the API endpoint or the specific response. This is currently
  for descriptive purposes and to facilitate debugging client
  applications, but EDR may decide to assign permanent meaning
  to this field in the future. It should be treated as an
  opaque string by your application, and this specification
  neither defines its values nor guarantees they will not
  change (even within a single version of the API).
  
* The `responseCode` datum contains an integer code that
  describes how the API request was processed. This code
  represents an HTTP response status code, which may differ
  from the actual HTTP response status code sent back in the
  response's HTTP headers.
  
  Note that, just as in the HTTP specification, a `responseCode`
  value below 400 indicates a successful response. However,
  your application may wish to check the `success` datum instead
  of performing this calculation.
   
* The `responseID` datum will contain a unique identifier for
  the response. This will change every time a new request is
  made, even if the request was identical to a previous request.
  
  This value is currently a UUID (Universally Unique Identifier),
  but the structure of this value should not be assumed to
  remain constant over time. This value should be treated as an
  opaque string by your application.
  
* The `success` datum is a Boolean value that indicates whether
  the API request was successfully handled or not.

Note that an API response that indicate the occurrence of an
error will typically have some additional data in its `meta`
element, as described in the
[Handling Errors](error-handling/errors.md) section of this
document. 
