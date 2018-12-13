# Get a User's Info by ID

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Users/{id}" %}
{% api-method-summary %}
Get User by ID
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to receive a user's information by ID.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="ID" type="string" required=true %}
ID of the user
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="Accept" %}
Specifies the type of data expected in response. Possible values: "application/json" / "text/json" / "application/xml", "text/xml"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The user's information has been successfully received
{% endapi-method-response-example-description %}

```text
{'ID': 'someID', 'Email': 'someEmail', 'FirstName': '', 'LastName': '', 'NotificationEmails': [], 'Company': '', 'Enabled': True, 'LicenseManagmentMode': 1, 'DestinationList': [], 'SpaceUsed': 0}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
{  "ID": "fake-7567-4965-8c8a-bee5bf6b056d",  "Email": "CharlieMarketing",  "FirstName": "Charlie",  "LastName": "Green",  "NotificationEmails": [    "charliem@maggiesdonuts.com",    "admin@maggiesdonuts.com"  ],  "Company": "Maggie's Donuts",  "Enabled": true,  "LicenseManagmentMode": 0,  "DestinationList": [    {      "ID": "detinationID",       "CurrentVolume": 2,      "PackageID": 3,      "AccountID": "sample string 4",      "AccountDisplayName": "sample string 5",      "Destination": "sample string 6",      "DestinationDisplayName": "sample string 7"    },    {      "ID": "sample string 1",      "CurrentVolume": 2,      "PackageID": 3,      "AccountID": "sample string 4",      "AccountDisplayName": "sample string 5",      "Destination": "sample string 6",      "DestinationDisplayName": "sample string 7"    }  ],  "SpaceUsed": 7}
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
def getUserByID(token, ID):
        getUserByIDRequest = requests.get('https://api.mspbackups.com/api/Users/' + ID, headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token})
        print("Get User by ID status code: " + str(getUserByIDRequest.status_code) + "\n")
        print(getUserByIDRequest.json())

getUserByID ("MBSAPItoken", "MBSuserID")
```

