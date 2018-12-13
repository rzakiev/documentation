# List a User's Destinations

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Destinations/{userEmail}" %}
{% api-method-summary %}
List User's Destinations
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to list available destinations for a particular user.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="userEmail" type="string" required=true %}
Email of the user whose destinations are to be listed
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter required=true name="Authorization" type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}

{% api-method-parameter name="Accept" type="string" %}
Specifies the type of data expected in response. Possible values:  "application/json" / "text/json" / "application/xml", "text/xml"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The list of destinations has been successfully retrieved
{% endapi-method-response-example-description %}

```
[{'ID': 'sample-4240-bc15-474850696692', 'CurrentVolume': 13031, 'PackageID': 27755, 'AccountID': 'sample37bb-4761-bc4e-f07ab8b7deb0', 'AccountDisplayName': 'test', 'Destination': 'seedingbucket', 'DestinationDisplayName': 'testStorage'}]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Response Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| ID | ID of the user | String |
| CurrentVolume | — | String |
| PackageID | — | String |
| AccountID | Internal MBS backup storage ID | String |
| AccountDisplayName | Internal MBS storage name displayed to the end user | String |
| Destination | Target bucket | String |
| DestinationDisplayName | Backup storage name displayed to the end user | String |

#### Response Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
[
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
]
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample
<ArrayOfUserDestinationsModel xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <UserDestinationsModel>
    <AccountDisplayName>sample string 5</AccountDisplayName>
    <AccountID>sample string 4</AccountID>
    <Destination>sample string 6</Destination>
    <DestinationDisplayName>sample string 7</DestinationDisplayName>
    <CurrentVolume>2</CurrentVolume>
    <ID>sample string 1</ID>
    <PackageID>3</PackageID>
  </UserDestinationsModel>
  <UserDestinationsModel>
    <AccountDisplayName>sample string 5</AccountDisplayName>
    <AccountID>sample string 4</AccountID>
    <Destination>sample string 6</Destination>
    <DestinationDisplayName>sample string 7</DestinationDisplayName>
    <CurrentVolume>2</CurrentVolume>
    <ID>sample string 1</ID>
    <PackageID>3</PackageID>
  </UserDestinationsModel>
</ArrayOfUserDestinationsModel>
```
{% endtab %}
{% endtabs %}

#### Sample Python Code

```python
import requests

def listDestinationsForUser (token, userEmail):
		listDestinationsForUserRequest = requests.get(self.baseURL + 'https://api.mspbackups.com/api/Destinations/' + userEmail, headers = {"Accept" : "application/json",
												   "Authorization": "Bearer " + token})
		print ("List destinations for user status code: " + str(listDestinationsForUserRequest.status_code) + "\n")
		return listDestinationsForUserRequest.json()

print(listDestinationsforUser ("MBStoken", "user@company.com"))
```

