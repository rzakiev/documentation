---
description: This page describes authentication via MBS API
---

# Initial Authentication

{% api-method method="post" host="https://api.mspbackups.com" path="/api/Provider/Login" %}
{% api-method-summary %}
Login
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to request an access token that will be used in all future requests.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Accept" type="string" required=false %}
Specifies the type of data expected in response to the requests. Possible values: "application/json"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="UserName" type="string" required=true %}
The MBS API username that can be generated in MBS Web Console.
{% endapi-method-parameter %}

{% api-method-parameter name="Password" type="string" required=true %}
The MBS API password. Length: between 3 and 100 \(including\).
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Access token has been successfully generated
{% endapi-method-response-example-description %}

```text
Status code: 200

access_token: fakeEkt8_niPVUehjYUSgKCTqC6w40s7aUfakez16m7egNZQkId1LMUhUEeMlNGfake

token_type: bearer

expires_in: 1209599

userName: wejfiwejf

.issued: Sat, 28 Apr 2018 13:50:43 GMT

.expires: Sat, 12 May 2018 13:50:43 GMT
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Incorrect credentials
{% endapi-method-response-example-description %}

```bash
error: invalid_grant

error_description: The user name or password is incorrect.
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Incorrect request URL
{% endapi-method-response-example-description %}

```text
Message: No HTTP resource was found that matches the request URI 'https://api.mspbackups.com/api/Prrovider/Login'.
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Request Formats:

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
{
  "UserName": "Charlie",
  "Password": "qwertyuiop"
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
<ProviderController.LoginUserBindingModel xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Controllers">
  <Password>Charlie</Password>
  <UserName>qwertyuiop</UserName>
</ProviderController.LoginUserBindingModel>
```
{% endtab %}
{% endtabs %}

## Response Information:

| Name | Description | Type |
| :--- | :--- | :--- |
| access\_token | Access token that will be used in all future requests | String |
| token\_type | Token type | String |
| expires\_in | Displays expiration date | String |
| userName | MBS API username | String |
| .issued | Displays the token issue date | String |
| .expires | Displays the token expiration date | String |

## Sample Python code

```python
#The library required to make HTTP requests
import requests

#Function that sends a request and prints out the response
def initialiAuth (jsonCreds, requestURL):
    authenticationRequest = requests.post('https://api.mspbackups.com/' + requestURL, json = jsonCreds)
    print ("Status code: " + str(authenticationRequest.status_code) + "\n")

    authenticationData = authenticationRequest.json()
    for key, value in authenticationData.items():
        print (str(key) + ": " + str(value) + "\n")

#Credentials that can be generated in MBS Web Console, in settings.
apiCreds = {
    "UserName" : "fake9xJKZcsy",
    "Password" : "fakeXkjwZmAJvAQBYjja"
}

#Call the function
initialiAuth (apiCreds, "api/Provider/Login")
```

