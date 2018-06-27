# API Transfer Protocol

Requests and responses issued as part of the LOS API are
transferred across the public Internet. The requirements of
this process are detailed in this section.

## Communication Protocols

Properly formatted API requests and responses are communicated
over HTTP (Hypertext Transfer Protocol), and are cryptographically
secured using TLS (Transport Layer Security). The "https" protocol
specifier is used within the LOS API system's URLs instead of
"http" because of the presence of this encryption.

The LOS API will issue HTTP response codes that are only
available to HTTP 1.1-compliant user agents. As such, your
client application must be capable of communicating using
HTTP 1.1. 

## Authentication

Requests issued to the LOS API are only acted upon if they
contain a token indicating that the sender has been
authenticated as a known client applicaiton registered with
EDR.

The authentication framework used by the LOS API is OAuth2.
The details of the authentication process are described fully
in the [Authentication](authentication.md) section of this
document. 

## Character Encodings

The LOS API uses Unicode code points encoded as UTF-8 for all
requests and responses. Its underlying system currently uses
three-byte encoding instead of the full four-byte encoding
necessary to represent all Unicode code points, so client
applications must not send code points above `U+FFFF`.

Note also that, despite the presence of Unicode support in
the LOS API, certain HTTP header values are required to be
encoded in ASCII according to web standards. For example,
RFC 7231, section 3.1.1.1. dictates that HTTP `Content-Type`
headers must only contain characters whose code points fall
within range permitted by seven-bit ASCII. Your application
must respect these specifications when constructing HTTP
requests.
