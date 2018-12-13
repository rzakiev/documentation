# List Existing Users

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Users" %}
{% api-method-summary %}
List Existing Users
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to list the existing users.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}

{% api-method-parameter name="Accept" type="string" required=true %}
Specifies the type of data expected in response. Possible values: "application/json" / "text/json" / "application/xml", "text/xml"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{'ID': 'userID-7567-4965-8c8a-bee5bf6bfake', 'Email': 'robert.z', 'FirstName': 'Robert', 'LastName': 'Techhead', 'NotificationEmails': ['techie@somedomain.com'], 'Company': '', 'Enabled': True, 'LicenseManagmentMode': 0, 'DestinationList': [{'ID': 'someID', 'CurrentVolume': 0, 'PackageID': 27755, 'AccountID': 'someID', 'AccountDisplayName': 'CorporateS3', 'Destination': 'storageBucket', 'DestinationDisplayName': 'Cloud Account'}], 'SpaceUsed': 745908}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Incorrect request URL.
{% endapi-method-response-example-description %}

```javascript
{
    "message": "No HTTP resource was found that matches the request URI 'https://api.mspbackups.com/api/Useers'.."
}
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
[
  {
    "ID": "userID",
    "Email": "user email",
    "FirstName": "sample string 3",
    "LastName": "sample string 4",
    "NotificationEmails": [
      "emailtoWhichNotificationsWillBeSent",
      "sample string 2"
    ],
    "Company": "sample string 5",
    "Enabled": true,
    "LicenseManagmentMode": 0,
    "DestinationList": [
      {
        "ID": "sample string 1",
        "CurrentVolume": 2,
        "PackageID": 3,
        "AccountID": "sample string 4",
        "AccountDisplayName": "sample string 5",
        "Destination": "sample string 6",
        "DestinationDisplayName": "sample string 7"
      },
      {
        "ID": "sample string 1",
        "CurrentVolume": 2,
        "PackageID": 3,
        "AccountID": "sample string 4",
        "AccountDisplayName": "sample string 5",
        "Destination": "sample string 6",
        "DestinationDisplayName": "sample string 7"
      }
    ],
    "SpaceUsed": 7
  },
  {
    "ID": "sample string 1",
    "Email": "sample string 2",
    "FirstName": "sample string 3",
    "LastName": "sample string 4",
    "NotificationEmails": [
      "sample string 1",
      "sample string 2"
    ],
    "Company": "sample string 5",
    "Enabled": true,
    "LicenseManagmentMode": 0,
    "DestinationList": [
      {
        "ID": "sample string 1",
        "CurrentVolume": 2,
        "PackageID": 3,
        "AccountID": "sample string 4",
        "AccountDisplayName": "sample string 5",
        "Destination": "sample string 6",
        "DestinationDisplayName": "sample string 7"
      },
      {
        "ID": "sample string 1",
        "CurrentVolume": 2,
        "PackageID": 3,
        "AccountID": "sample string 4",
        "AccountDisplayName": "sample string 5",
        "Destination": "sample string 6",
        "DestinationDisplayName": "sample string 7"
      }
    ],
    "SpaceUsed": 7
  }
]
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<ArrayOfUsersModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">  <UsersModels>    <Company>sample string 5</Company>    <DestinationList>      <UserDestinationsModel>        <AccountDisplayName>sample string 5</AccountDisplayName>        <AccountID>sample string 4</AccountID>        <Destination>sample string 6</Destination>        <DestinationDisplayName>sample string 7</DestinationDisplayName>        <CurrentVolume>2</CurrentVolume>        <ID>sample string 1</ID>        <PackageID>3</PackageID>      </UserDestinationsModel>      <UserDestinationsModel>        <AccountDisplayName>sample string 5</AccountDisplayName>        <AccountID>sample string 4</AccountID>        <Destination>sample string 6</Destination>        <DestinationDisplayName>sample string 7</DestinationDisplayName>        <CurrentVolume>2</CurrentVolume>        <ID>sample string 1</ID>        <PackageID>3</PackageID>      </UserDestinationsModel>    </DestinationList>    <Email>sample string 2</Email>    <Enabled>true</Enabled>    <FirstName>sample string 3</FirstName>    <ID>sample string 1</ID>    <LastName>sample string 4</LastName>    <LicenseManagmentMode>Manual</LicenseManagmentMode>    <NotificationEmails xmlns:d3p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">      <d3p1:string>sample string 1</d3p1:string>      <d3p1:string>sample string 2</d3p1:string>    </NotificationEmails>    <SpaceUsed>7</SpaceUsed>  </UsersModels>  <UsersModels>    <Company>sample string 5</Company>    <DestinationList>      <UserDestinationsModel>        <AccountDisplayName>sample string 5</AccountDisplayName>        <AccountID>sample string 4</AccountID>        <Destination>sample string 6</Destination>        <DestinationDisplayName>sample string 7</DestinationDisplayName>        <CurrentVolume>2</CurrentVolume>        <ID>sample string 1</ID>        <PackageID>3</PackageID>      </UserDestinationsModel>      <UserDestinationsModel>        <AccountDisplayName>sample string 5</AccountDisplayName>        <AccountID>sample string 4</AccountID>        <Destination>sample string 6</Destination>        <DestinationDisplayName>sample string 7</DestinationDisplayName>        <CurrentVolume>2</CurrentVolume>        <ID>sample string 1</ID>        <PackageID>3</PackageID>      </UserDestinationsModel>    </DestinationList>    <Email>sample string 2</Email>    <Enabled>true</Enabled>    <FirstName>sample string 3</FirstName>    <ID>sample string 1</ID>    <LastName>sample string 4</LastName>    <LicenseManagmentMode>Manual</LicenseManagmentMode>    <NotificationEmails xmlns:d3p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">      <d3p1:string>sample string 1</d3p1:string>      <d3p1:string>sample string 2</d3p1:string>    </NotificationEmails>    <SpaceUsed>7</SpaceUsed>  </UsersModels></ArrayOfUsersModels>
```
{% endtab %}
{% endtabs %}

## Response Information

| Name | Description | Type |
| :--- | :--- | :--- |
| ID | User ID | String |
| Email | User email or login | String |
| FirstName | — | String |
| LastName | — | String |
| NotificationEmails | — | Collection of String |
| Company | Company to which the user is assigned | String |
| Enabled | Indicates if the user is enabled | String |
| LicenseManagementMode | User license management mode | UserModeType \(Manual == 0, Automatic == 1\) |
| SpaceUsed | Used space in Kilobytes | Integer |

## Sample Python Code

```python
import requests 
def listUsers(token):
        listUsersRequest = requests.get('https://api.mspbackups.com/api/Users',
                                        headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token})
        print("Status code: " + str(listUsersRequest.status_code) + "\n")
        print (listUsersRequest.json())

listUsers("MBSAPItoken")
```

