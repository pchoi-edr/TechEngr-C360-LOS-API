# Handling Errors

Unless a catastrophic error occurs, LOS API responses should
always contain an HTTP response status code indicating either
success or redirection. Any errors encountered by the API
server will be identified by the value of the API response's
`responseCode` datum in its top-level `meta` element, which
will be equal to an HTTP response status code that describes
the error that occurred.

## Additional Error Metadata

When an error occurs, the API response's top-level `meta`
element will contain the following additional data:

* The `errors` datum will be an array consisting of all
  relevant error messages. Each error message will have a
  `description` attribute that contains the text of the
  error message.
  
  EDR may add more attributes to each error message over
  time. Your application should be written in such a way
  that the addition of these new attributes will not cause
  an error.

  An example of the `errors` datum follows:
  
  ```
  "errors" : [
    {
      "description": "The \"First Name\" field is required."
    },
    {
      "description": "The \"Surname\" field is required."
    }
  ]
  ```

* The `reason` datum will contain a brief textual description
  of the `responseCode` datum's value (for example, if the
  `responseCode` is 404, then the `reason` may be equal to
  "Not Found").
  
  The specific text is subject to change over time, and should
  be considered informational only. While applicaitons may
  choose to display or record this text as part of an error
  message or debugging capability, the application's logic
  should only rely on the `responseCode` field's corresponding
  integer value. 
