# Edit an Account

{% api-method method="put" host="https://api.mspbackups.com" path="/api/Accounts" %}
{% api-method-summary %}
Edit Account
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to edit an MBS storage account
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}

{% api-method-parameter name="Accept" type="string" %}
Specifies the type of data expected in response. Possible values: "application/json" / "text/json" / "application/xml", "text/xml"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The account has been successfully edited.
{% endapi-method-response-example-description %}

```text
No message is returned
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Request Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| AccountID | Account ID | String |
| DisplayName | Display name | String |
| Type | Account type | AccountType \(see Create New Account\) |
| AccountSettings | Storage-specific settings | Settings \(see Create New Account\) |

## Request Formats

Identical to formats in [_Add a New Account_](add-a-new-account.md).

## Response Information

None if the request has been sent successfully. Otherwise, a JSON is returned containing the error message.

## Sample Python Code

```python
import requests
def editAccount(token, editedAccount):
        editAccountRequest = requests.put('https://api.mspbackups.com/api/Accounts', headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token}, json = editedAccount)

        if editAccountRequest.status_code == 200:
            print('200')
            return editAccountRequest.json()
        else:
            print("Error: " + str(editAccountRequest.status_code))
            return editAccountRequest.status_code

editedAccount = {
    "AccountID" : "MBSID-97f0-4df9-a867-f158ad01220d",
    "DisplayName" : "My S3 account NEW",
    "Type" : 0,
    "AccountSettings" : {
        "AmazonS3": {
            "AccessKey" : "sampleIXPUW2UXRWQYYBYQ",
            "SecretKey" : "samplewed4kunLB+sxKPaRsEEfQe8J6Y33huFOWcZ4T",
            "IsGovCloud" : False
        }
    }
}

editAccount("MBSAPItoken", editedAccount)
```

