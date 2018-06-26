# SRF OAuth2 Token API

## <span style="background-color: #ebb747; font-weight: bold; color: #ffffff; padding: 3px 10px; border-radius: 14px;">POST</span> **OAuth2 Access Token**

```text
/api/v1/oauth/token
```

### Request

> POST Request parameters

| Request Parameter | Type | Description |
| :--- | :--- | :--- |
| grant_type | String | client_credentials |
| client_id | String | UUID Format |
| client_secret | String | JWT Encoded |
| scope | String | * |

```
curl https://security.edrnet.com/oauth/token \
  -H "Content-Type: application/json" \
  --request POST \
  --data '{"grant_type":"client_credentials","client_id":"xyz-123","client_secret":"...secret_key...","scope":"*"}' \
```

```javascript
{
    "grant_type":"client_credentials",
    "client_id":"xyz-123",
    "client_secret":"...secret_key...",
    "scope":"*"
}
```

### Response

```javascript
{
    "meta": {
        "success": true,
        "responseCode": 200,
        "responseID": "e3733640-789c-11e8-9dfc-81c439846400",
        "date": "2018-06-17T22:18:45Z",
        "function": "oauth"
    },
    "data": {
        "token_type": "Bearer",
        "expires_in": 3600,
        "access_token": "72ab415822b56cf0f9f93f07fe978d9aae859325"
    }
}

```
