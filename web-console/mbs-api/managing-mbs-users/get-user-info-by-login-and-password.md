# Get a User's Info by Login & Password

{% api-method method="put" host="https://api.mspbackups.com" path="/api/Users/Authenticate" %}
{% api-method-summary %}
Get User info via Login and Password
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to receive a user's information by authenticating with login and password.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer + \*token\*"
{% endapi-method-parameter %}

{% api-method-parameter name="Accept" type="string" %}
Specifies the type of data expected in response. Possible values: "application/json" / "text/json" / "application/xml", "text/xml"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="Email" type="string" required=true %}
User login or email
{% endapi-method-parameter %}

{% api-method-parameter name="Password" type="string" required=true %}
User password
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The user's information has been successfully received.
{% endapi-method-response-example-description %}

```text
{'ID': 'someID', 'Email': 'someEmail', 'FirstName': '', 'LastName': '', 'NotificationEmails': [], 'Company': '', 'Enabled': True, 'LicenseManagmentMode': 1, 'DestinationList': [], 'SpaceUsed': 0}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Request Format

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
{  "Email": "sample string 1",  "Password": "sample string 2"}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
<UserAuthData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">  <Email>sample string 1</Email>  <Password>sample string 2</Password></UserAuthData>
```
{% endtab %}
{% endtabs %}

## Response Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
{  "ID": "sample string 1",  "Email": "sample string 2",  "FirstName": "sample string 3",  "LastName": "sample string 4",  "NotificationEmails": [    "sample string 1",    "sample string 2"  ],  "Company": "sample string 5",  "Enabled": true,  "LicenseManagmentMode": 0,  "DestinationList": [    {      "ID": "sample string 1",      "CurrentVolume": 2,      "PackageID": 3,      "AccountID": "sample string 4",      "AccountDisplayName": "sample string 5",      "Destination": "sample string 6",      "DestinationDisplayName": "sample string 7"    },    {      "ID": "sample string 1",      "CurrentVolume": 2,      "PackageID": 3,      "AccountID": "sample string 4",      "AccountDisplayName": "sample string 5",      "Destination": "sample string 6",      "DestinationDisplayName": "sample string 7"    }  ],  "SpaceUsed": 7}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<UsersModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">  <Company>sample string 5</Company>  <DestinationList>    <UserDestinationsModel>      <AccountDisplayName>sample string 5</AccountDisplayName>      <AccountID>sample string 4</AccountID>      <Destination>sample string 6</Destination>      <DestinationDisplayName>sample string 7</DestinationDisplayName>      <CurrentVolume>2</CurrentVolume>      <ID>sample string 1</ID>      <PackageID>3</PackageID>    </UserDestinationsModel>    <UserDestinationsModel>      <AccountDisplayName>sample string 5</AccountDisplayName>      <AccountID>sample string 4</AccountID>      <Destination>sample string 6</Destination>      <DestinationDisplayName>sample string 7</DestinationDisplayName>      <CurrentVolume>2</CurrentVolume>      <ID>sample string 1</ID>      <PackageID>3</PackageID>    </UserDestinationsModel>  </DestinationList>  <Email>sample string 2</Email>  <Enabled>true</Enabled>  <FirstName>sample string 3</FirstName>  <ID>sample string 1</ID>  <LastName>sample string 4</LastName>  <LicenseManagmentMode>Manual</LicenseManagmentMode>  <NotificationEmails xmlns:d2p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">    <d2p1:string>sample string 1</d2p1:string>    <d2p1:string>sample string 2</d2p1:string>  </NotificationEmails>  <SpaceUsed>7</SpaceUsed></UsersModels>
```
{% endtab %}
{% endtabs %}

## Sample Python Code:

```python
import requests
def getUserByLoginPassword (token, login, password):
        getUserByLoginPasswordRequest = requests.put('https://api.mspbackups.com/api/Users/Authenticate', headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token}, json = {"Email" : login, "Password" : password})
        print("Get User by login & password status code: " + str(getUserByLoginPasswordRequest.status_code) + "\n")
        print(getUserByLoginPasswordRequest.json())

getUserByLoginPassword(token, "login", "password")
```

