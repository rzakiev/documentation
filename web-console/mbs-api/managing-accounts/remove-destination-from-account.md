# Remove Destination from Account

{% api-method method="put" host="https://api.mspbackups.com" path="/api/Accounts/RemoveDestination" %}
{% api-method-summary %}
Remove Destination From Account
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to remove a destination from an MBS account.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="AccountID" type="string" required=true %}
Account ID that contains the destination
{% endapi-method-parameter %}

{% api-method-parameter name="Destination" type="string" required=true %}
Target bucket name
{% endapi-method-parameter %}

{% api-method-parameter name="DestinationDisplayName" type="string" required=false %}
Display name for the destination
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The destination has been successfully removed from the account.
{% endapi-method-response-example-description %}

```
No message is returned
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
  "AccountID": "adfc2826-3776-4f36-985d-a95cd3b59894",
  "Destination": "targetBucket",
  "DestinationDisplayName": "Backup Container"
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<DestinationOfAccount xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <AccountID>adfc2826-3776-4f36-985d-a95cd3b59894</AccountID>
  <Destination>sample string 2</Destination>
  <DestinationDisplayName>sample string 3</DestinationDisplayName>
</DestinationOfAccount>
```
{% endtab %}
{% endtabs %}

#### Response Information

None if the request has been sent successfully. Otherwise, a JSON is returned containing the error message.

#### Sample Python Code

```python
import requests
def removeDestination(token, destination):
		removeDestinationRequest = requests.put('https://api.mspbackups.com/api/Accounts/RemoveDestination', headers = {"Authorization": "Bearer " + token}, json = destination)

		if removeDestinationRequest.status_code == 200:
			print('200')
		else:
			print("Error: " + str(removeDestinationRequest.status_code))

		return removeDestinationRequest.status_code
		
destinationToRemove = {
	"AccountID" : "someID-97f0-4df9-a867-f158ad01220d",
	"Destination" : "s3bucketName",
	"DestinationDisplayName" : "Personal Bucket"
}

removeDestination(destinationToRemove)
```

{% hint style="warning" %}
Before removing a destination, ensure that it is not assigned to any user. 
{% endhint %}

