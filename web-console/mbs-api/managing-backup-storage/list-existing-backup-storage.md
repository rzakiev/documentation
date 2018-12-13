# List Existing Destinations

{% hint style="info" %}
Backup storage for a particular user is referred to as _destinations_ in the internal MBS terminology.
{% endhint %}

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Destinations" %}
{% api-method-summary %}
List Existing Destinations
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to list available destinations \(backup storage\).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter type="string" name="Authorization" required=true %}
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
{'AccountID': 'Sample94bf5b06-79a0-4a52-88ed-36da6wer4', 'AccountDisplayName': 'Azure ', 'Destination': 'main', 'DestinationDisplayName': 'Azure '}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Response Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| AccountID | ID of the backup storage | String |
| AccountDisplayName | Internal MBS name of the backup storage | String |
| Destination | Target bucket | String |
| DestinationDisplayName | Backup Storage name displayed to the end user | String |

#### Response Format

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
[
  {
    "AccountID": "sample string 1",
    "AccountDisplayName": "sample string 2",
    "Destination": "sample string 3",
    "DestinationDisplayName": "sample string 4"
  },
  {
    "AccountID": "sample string 1",
    "AccountDisplayName": "sample string 2",
    "Destination": "sample string 3",
    "DestinationDisplayName": "sample string 4"
  }
]
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<ArrayOfDestinationsModel xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <DestinationsModel>
    <AccountDisplayName>sample string 2</AccountDisplayName>
    <AccountID>sample string 1</AccountID>
    <Destination>sample string 3</Destination>
    <DestinationDisplayName>sample string 4</DestinationDisplayName>
  </DestinationsModel>
  <DestinationsModel>
    <AccountDisplayName>sample string 2</AccountDisplayName>
    <AccountID>sample string 1</AccountID>
    <Destination>sample string 3</Destination>
    <DestinationDisplayName>sample string 4</DestinationDisplayName>
  </DestinationsModel>
</ArrayOfDestinationsModel>
```
{% endtab %}
{% endtabs %}

#### Sample Python Code

```python
import requests
 
def listDestinations (token):
		listDestinationsRequest = requests.get('https://api.mspbackups.com/api/Destinations', headers = {"Accept" : "application/json",
												   "Authorization": "Bearer " + token})
		print("List destinations request status code: " + str(listDestinationsRequest.status_code) + "\n")
		return listDestinationsRequest.json()
		
listDestinations(token)
```

