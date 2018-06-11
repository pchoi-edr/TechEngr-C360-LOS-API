# Authentication

## OAuth2

> EDR uses only the Client Credentials grant. A general OAuth2 workflow can be seen in the following diagram.

<div style="text-align: center; border: 1px solid #ccc; padding: 20px">
    <img src="./auth-seq.png" width="400">
</div>

The client must register for a `clientId` and `secret` key.

* clientId: confidentialApplication
* secret: topSecret

### Obtaining a token

To obtain a token you should POST your clientId and secret key to https://security.edrnet.com/oauth/token.

You need to include the client credentials in request headers and the grant type in request body:

* Headers
    * Authorization: "Basic " + clientId:secret base64'd

        * (for example, to use confidentialApplication:topSecret, you should send Basic Y29uZmlkZW50aWFsQXBwbGljYXRpb246dG9wU2VjcmV0)
Content-Type: application/x-www-form-urlencoded

For example, using curl:

```
curl https://security.edrnet.com/oauth/token \
  -H "Authorization: Basic Y29uZmlkZW50aWFsQXBwbGljYXRpb246dG9wU2VjcmV0" \
  -H "Content-Type: application/x-www-form-urlencoded"
```

```javascript
{
	"token_type": "bearer",
	"access_token": "72ab415822b56cf0f9f93f07fe978d9aae859325",
	"expires_in": 3600
}
```

### Using the token

Now, you can use your brand-new token to access restricted areas. For example, you can perform an HTTP GET request for https://api.edrnet.com/ by including your token in the headers:

* Headers
    * Authorization: "Bearer " + access_token
(for example, Bearer 72ab415822b56cf0f9f93f07fe978d9aae859325)

For example, using curl:

```
curl https://api.edrnet.com/ \
  -H "Authorization: Bearer 72ab415822b56cf0f9f93f07fe978d9aae859325"
```
