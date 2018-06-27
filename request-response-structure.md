# API Data Structures

With the exception of authentication-related API endpoints,
the HTTP body contents of every request to--or response
from--the LOS API conform to the following general JSON structure:

```
{
    "meta" : {},
    "data" : {}
}
```

The top-level `meta` element contains information about the
request or response itself, while the `data` element contains
data that are specific to the individual endpoint being called.

Since the contents of the `data` element will vary by endpoint,
you must refer to each API endpoint's documentation for the
specific values expected in this section. 

Note that some API endpoints use an HTTP method that expects
no body content (_e.g._ GET requests). In these cases, you
should not supply any HTTP body content to the API server.

Note also that the order of fields in the response is subject
to change. Your application should never assume that fields will
always be returned in the same order unless this specification
explicitly indicates that a particular data element will always
be returned in a given order by design.

## API Request Structure

At this time, no values in the `meta` element are honored
by the API server. This top-level element is reserved for
future use.

Note that all API requests must contain a valid
HTTP `Content-Type` header with a format that the API server
supports. Typically, this will be as follows:

    Content-Type: application/json

## HTTP Response Status Codes of API Responses

The API server will do its best to process any request it
receives. Whenever possible, it will return its responses
with HTTP response status codes of either 200 (indicating
success) or 303 (indicating a URL where a downloadable
resource is available).

Note that this is also true if an error occurs, inasmuch as
this is feasible. For example, if an API request is
malformed but was received by the API server, then an HTTP
server would normally return  400 HTTP response status code
(representing a "Bad Request" error). However, the LOS API
will instead return a 200 HTTP response status code (indicating
success), and will supply the 400 HTTP response status code
in the `responseCode` datum in its `meta` element. 

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
  to this field in the future.
  
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
  
  This value is currently a UUID (Universally Unique IDentifier),
  but the structure of this value should not be assumed to
  remain constant over time. This value should be treated as an
  opaque string by your application.
  
* The `success` datum is a Boolean value that indicates whether
  the API request was successfully handled or not.

Note that API responses that indicate the occurrence of an
error will have some additional data, as described in the
[Handling Errors](error-handling/errors.md) section of this document. 

Under some circumstances, it may be possible for the top-level
`data` element to be `null`. Your application should gracefully
handle this case as a normal condition.
