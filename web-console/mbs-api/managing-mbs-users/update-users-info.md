# Update a User's Info

{% api-method method="put" host="https://api.mspbackups.com" path="/api/Users" %}
{% api-method-summary %}
Update User Info
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to update a user's information.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter type="string" name="Authorization" required=true %}
Specifies the authorization type and token. Possible value: "Bearer  \*token\*"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="LicenseManagementMode" type="integer" required=false %}
0 \(Manual\), Automatic \(1\)
{% endapi-method-parameter %}

{% api-method-parameter name="Enabled" type="boolean" required=false %}
Indicates if the user should be enabled
{% endapi-method-parameter %}

{% api-method-parameter name="ID" type="string" required=false %}
User ID
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
No message is returned
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Format

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json:

```javascript
Sample:
{  "ID": "sample string 1",  "Email": "sample string 2",  "FirstName": "sample string 3",  "LastName": "sample string 4",  "NotificationEmails": [    "sample string 1",    "sample string 2"  ],  "Company": "sample string 5",  "Enabled": true,  "Password": "sample string 7",  "LicenseManagmentMode": 0}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml:

```markup
Sample:
<UsersEditModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">  <Company>sample string 5</Company>  <Email>sample string 2</Email>  <Enabled>true</Enabled>  <FirstName>sample string 3</FirstName>  <ID>sample string 1</ID>  <LastName>sample string 4</LastName>  <LicenseManagmentMode>Manual</LicenseManagmentMode>  <NotificationEmails xmlns:d2p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">    <d2p1:string>sample string 1</d2p1:string>    <d2p1:string>sample string 2</d2p1:string>  </NotificationEmails>  <Password>sample string 7</Password></UsersEditModels>
```
{% endtab %}
{% endtabs %}

#### Response Information

None.

#### Sample Python Code

```python
import requests

def updateUserInfo(token, newInfoJSON):
		updateUserInfoRequest = requests.put('https/api.mspbackups.com/api/Users', headers = {"Authorization": "Bearer " + token}, json = newInfoJSON)
		print("Updated user status code: " + str(updateUserInfoRequest.status_code) + "\n")
		return updateUserInfoRequest.status_code
		
updatedUser = {
	"ID" : "9d6de082-741c-44fe-b067-1a36eb03fa40", #required
	"Password" : "newUnhackablePass", #required
	"Enabled" : False #required
}

print(updateUserInfo("mbsAPItoken", updatedUser))
```



