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

A POST call to the oauth/token api endpoint with the client credentials and the grant type in request body:

* Headers
    * Content-Type: "application/json"

        * (for example, to use confidentialApplication:topSecret, you should send request body)
    * Request Body
        * {
            "grant_type":"client_credentials",
            "client_id":"xyz-123",
            "client_secret":"...secret_key...",
            "scope":"*"
          }

For example, using curl:

```
curl https://security.edrnet.com/oauth/token \
  -H "Content-Type: application/json" \
  --request POST \
  --data '{"grant_type":"client_credentials","client_id":"xyz-123","client_secret":"...secret_key...","scope":"*"}' \
```

```javascript
{
	"token_type": "bearer",
	"access_token": "72ab415822b56cf0f9f93f07fe978d9aae859325",
	"expires_in": 3600
}
```

### Using the token

Now, you can use your brand-new token to access restricted areas. For example, you can GET to https://api.edrnet.com/ including your token at headers:

* Headers
    * Authorization: "Bearer " + access_token
(for example, Bearer 72ab415822b56cf0f9f93f07fe978d9aae859325)

For example, using curl:

```
curl https://api.edrnet.com/ \
  -H "Authorization: Bearer 72ab415822b56cf0f9f93f07fe978d9aae859325"
```
