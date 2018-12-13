# Create a New User

{% api-method method="post" host="https://api.mspbackups.com" path="/api/Users" %}
{% api-method-summary %}
Create New User
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to to create a new MBS user.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Accept" type="string" %}
Specifies the type of data expected in response. Possible values:  "application/json" / "text/json" / "application/xml", "text/xml"
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
Specifies the authorization type and token. Value: "Bearer  MBSAPItoken"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The user has been successfully created!
{% endapi-method-response-example-description %}

```
"userID"
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Format

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
{  "Email": "sample string 1", //REQUIRED  "FirstName": "sample string 2",  "LastName": "sample string 3",  "NotificationEmails": [    "sample string 1",    "sample string 2"  ],  "Company": "sample string 4",  "Enabled": true, //REQUIRED  "Password": "sample string 6", //REQUIRED  "DestinationList": [    {      "AccountID": "sample string 1",      "Destination": "sample string 2",      "PackageID": 3    },    {      "AccountID": "sample string 1",      "Destination": "sample string 2",      "PackageID": 3    }  ],  "SendEmailInstruction": true,  "LicenseManagmentMode": 0}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<UsersAddModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">  <Company>sample string 4</Company>  <DestinationList>    <DestinationForNewUser>      <AccountID>sample string 1</AccountID>      <Destination>sample string 2</Destination>      <PackageID>3</PackageID>    </DestinationForNewUser>    <DestinationForNewUser>      <AccountID>sample string 1</AccountID>      <Destination>sample string 2</Destination>      <PackageID>3</PackageID>    </DestinationForNewUser>  </DestinationList>  <Email>sample string 1</Email>  <Enabled>true</Enabled>  <FirstName>sample string 2</FirstName>  <LastName>sample string 3</LastName>  <LicenseManagmentMode>Manual</LicenseManagmentMode>  <NotificationEmails xmlns:d2p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">    <d2p1:string>sample string 1</d2p1:string>    <d2p1:string>sample string 2</d2p1:string>  </NotificationEmails>  <Password>sample string 6</Password>  <SendEmailInstruction>true</SendEmailInstruction></UsersAddModels>
```
{% endtab %}
{% endtabs %}

#### Response Formats

* application/json, text/json
* application/xml, text/xml

Response represents the ID of the new user.

#### Sample Python Code:

```python
import requests
def createUser(token, newUserJson):
		createUserRequest = requests.post('https://api.mspbackups.com/api/Users', json = newUserJson, headers = {"Accept" : "application/json", "Authorization": "Bearer " + token})
		print ("Create user request status code: " + str(createUserRequest.status_code) + "\n")

		if createUserRequest.status_code != 200:
			print("ERROR!")

		print(createUserRequest.json())

newUser = {
 	"Email" : "roberttech1", #required
 	"Password" : "splendidpass", #required
 	"Enabled" : True #required
}

createUser("mbsAPItoken", newUser)
```

