# Get Billing Information for User

{% api-method method="put" host="https://api.mspbakcups.com" path="/api/Billing/Details" %}
{% api-method-summary %}
Billing Information for User
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to request billing records for a particular user or date
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}

{% api-method-parameter name="Accept" type="string" %}
Specifies the type of data expected in response. Possible values:  "application/json" / "text/json" / "application/xml", "text/xml"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="Date" type="string" required=false %}
Date. If empty, the current date will be set.
{% endapi-method-parameter %}

{% api-method-parameter name="UserID" type="string" required=false %}
MBS user ID.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The billing records have been successfully received
{% endapi-method-response-example-description %}

```
{'TotalBackupBytes': 0, 'TotalRestoreBytes': 0, 'UserID': 'someID-f98c-4fbd-aa0d-b1b5551f2df3', 'UserDetailList': [{'Computer': None, 'SizeBackup': 0, 'SizeRestore': 0, 'Prefix': None, 'AccountID': 'someID-dd51-45bf-9e2b-91f0ff9b5e41', 'Destination': 'Cloud Account (bucketName)'}]}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
{
  "UserID": "4bf78e21-96e4-4033-8658-ab1ac6882039",
  "Date": "2018-05-15T12:38:47.3032803+00:00"
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<FilterDetailModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <Date>2018-05-15T12:38:47.3032803+00:00</Date>
  <UserID>4bf78e21-96e4-4033-8658-ab1ac6882039</UserID>
</FilterDetailModels>
```
{% endtab %}
{% endtabs %}

#### Response Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| TotalBackupBytes | Total backed up data | Integer |
| TotalRestoreBytes | Total restored data | Integer |
| UserID | MBS user ID | String |
| UserDetailList | Backup details for the user | UserDetailModels |

* UserDetailModels parameters:

| Parameter | Description | Value |
| :--- | :--- | :--- |
| Computer | Computer Name | String |
| SizeBackup | Total backup volume | Integer |
| SizeRestore | Total restore volume | Integer |
| Prefix | Prefix name | String |
| AccountID | Storage account ID | String |
| Destination | Backup/Restore destination | String |

#### Response Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
{
  "TotalBackupBytes": 1,
  "TotalRestoreBytes": 2,
  "UserID": "425a1173-c4a2-48d3-96fc-59f367bf7a2b",
  "UserDetailList": [
    {
      "Computer": "sample string 1",
      "SizeBackup": 2,
      "SizeRestore": 3,
      "Prefix": "sample string 4",
      "AccountID": "0beeabc4-bdd4-4741-88b8-d3883ae090b1",
      "Destination": "sample string 6"
    },
    {
      "Computer": "sample string 1",
      "SizeBackup": 2,
      "SizeRestore": 3,
      "Prefix": "sample string 4",
      "AccountID": "0beeabc4-bdd4-4741-88b8-d3883ae090b1",
      "Destination": "sample string 6"
    }
  ]
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<DetailModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <TotalBackupBytes>1</TotalBackupBytes>
  <TotalRestoreBytes>2</TotalRestoreBytes>
  <UserDetailList>
    <UserDetailModels>
      <AccountID>0beeabc4-bdd4-4741-88b8-d3883ae090b1</AccountID>
      <Computer>sample string 1</Computer>
      <Destination>sample string 6</Destination>
      <Prefix>sample string 4</Prefix>
      <SizeBackup>2</SizeBackup>
      <SizeRestore>3</SizeRestore>
    </UserDetailModels>
    <UserDetailModels>
      <AccountID>0beeabc4-bdd4-4741-88b8-d3883ae090b1</AccountID>
      <Computer>sample string 1</Computer>
      <Destination>sample string 6</Destination>
      <Prefix>sample string 4</Prefix>
      <SizeBackup>2</SizeBackup>
      <SizeRestore>3</SizeRestore>
    </UserDetailModels>
  </UserDetailList>
  <UserID>425a1173-c4a2-48d3-96fc-59f367bf7a2b</UserID>
</DetailModels>
```
{% endtab %}
{% endtabs %}

#### Sample Python Code

```python
import requests
def billingDetailsForUser(token, criteria):
		billingDetailsForUserRequest = requests.put('https://api.mspbackups.com/api/Billing/Details', headers = {"Accept" : "application/json",
												   "Authorization": "Bearer " + token}, json = criteria)

		if billingDetailsForUserRequest.status_code == 200:
			print('200')
			return billingDetailsForUserRequest.json()
		else:
			return billingDetailsForUserRequest.status_code

criteria = {
	"UserID" : "e6199730-f98c-4fbd-aa0d-b1b5551f2df3",
	"Date" : ""
}

billingDetailsForUser(MBSAPItoken, criteria)
```

