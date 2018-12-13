# List a User's Computers and Backup Storage

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Users/{userID}/Computers" %}
{% api-method-summary %}
List User's Computers and Backup Storage
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to receive the list of computers and backup storages for the specified MBS user.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="userID" type="string" required=true %}
ID of the MBS user
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
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
The list of computers and destinations for the specified user has been successfully received
{% endapi-method-response-example-description %}

```
{'DestinationId': '5ca40a3a-9e91-4013-b749-9qwerty', 'ComputerName': 'roberts-mbp.qwerty'}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Response Data

| Parameter | Description | Value |
| :--- | :--- | :--- |
| DestintationId | Bucket that contains the data | String |
| Computer's Name | The name of the computer whose data is to be deleted | String |

#### Response Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
[  {    "DestinationId": "74c0060b-1ca5-4342-9d02-2a7f57ewer",    "ComputerName": "roberts-mbp.dev.corp"  },  {    "DestinationId": "74c0060b-1ca5-4342-9d02-2a7f57ewer",    "ComputerName": "acer computer name"  }]
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<ArrayOfUserComputerData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">  <UserComputerData>    <ComputerName>sample string 2</ComputerName>    <DestinationId>74c0060b-1ca5-4342-9d02-2a7f57e378c4</DestinationId>  </UserComputerData>  <UserComputerData>    <ComputerName>sample string 2</ComputerName>    <DestinationId>74c0060b-1ca5-4342-9d02-2a7f57e378c4</DestinationId>  </UserComputerData></ArrayOfUserComputerData>
```
{% endtab %}
{% endtabs %}

#### Sample Python Code

```python
import requests 
def listUsersComputersandStorage(token, userID):
		listUsersComputersandStorageRequest = requests.get('https://api.mspbackups.com/api/Users/' + userID + '/Computers', headers = {"Accept" : "application/json",
												   "Authorization": "Bearer " + token})
		print("List user's computers and Storage request status code:" + str(listUsersComputersandStorageRequest.status_code) + "\n")

		return listUsersComputersandStorageRequest.json()

listUsersComputersandStorage ("MBSAPItoken", "MBSuserID")
```

