# API List

This section contains a systematic list of all API endpoints
supported by the LOS API.

## Conventions

API endpoints are listed as URL paths. Hostnames are omitted,
while any query string parameters are listed separately.

Certain parts of a URL may contain variable data meant to be
selected by the client application. In these cases, the variables
will be prefixed by a colon (":"). For example, in the following
URL, the value `:variable` is a variable:

```
/example/url/path/:variable
```

When this variable is replaced by an actual value in your
API requests, do not include the leading colon. For example,
the preceding URL would look like so with the variable replaced
by the value `123`: 

```
/example/url/path/123
```

For each endpoint, the supported HTTP methods are indicated like so:

  * <span style="background-color: #72b566; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">GET</span>
  
  * <span style="background-color: #ebb747; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">POST</span>

  * <span style="background-color: #5493dc; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">PUT</span>

