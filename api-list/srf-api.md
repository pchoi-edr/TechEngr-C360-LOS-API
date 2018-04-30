# SRF API

{% api-method method="get" host="https://api-c360-los.edrnet.com" path="/v1/srf/:serviceRequestID" %}
{% api-method-summary %}
Get Service Request Details
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get service request details.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="serviceRequestID" type="number" %}
ID of the service request
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
SRF successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
    "serviceRequestID": 12345678,
    "loanID": null,
    "locations": []
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
SRF Error
{% endapi-method-response-example-description %}

```javascript
{
    "code": 400,
    "description": "Something wrong",
    "reason": ""
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find an SRF matching this query.
{% endapi-method-response-example-description %}

```javascript
{
    "code": 404,
    "description": "Not Found"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api-c360-los.edrnet.com" path="/v1/srf/:serviceRequestID" %}
{% api-method-summary %}
Update Service Request Details
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to update service request details.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="serviceRequestID" type="number" required=false %}
ID of the service request
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "serviceRequestID": 12345678,
    "loanID": null,
    "locations": []
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "code": 400,
    "description": "Something wrong",
    "reason": ""
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "code": 404,
    "description": "Not Found"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api-c360-los.edrnet.com" path="/v1/srf" %}
{% api-method-summary %}
Add New Service Request Details
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to add a new service request.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="test" type="string" required=false %}
test
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

| test |
| --- |


