# Add Destination to Account

{% api-method method="post" host="https://api.mspbaackups.com" path="/api/Accounts/AdDestination" %}
{% api-method-summary %}
Add Destination to Account
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you add a destination \(bucket\) to your MBS account.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="AccountID" type="string" required=true %}
MBS account ID.
{% endapi-method-parameter %}

{% api-method-parameter name="Destination" type="string" required=true %}
Name fo the bucket that will contain the data
{% endapi-method-parameter %}

{% api-method-parameter name="DestinationDisplayName" type="string" required=false %}
Display name for the destination
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The destination has been successfully added.
{% endapi-method-response-example-description %}

```text
No message is returned
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Request Formats

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

{% tab title="Second Tab" %}
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

## Response Information

None if the request has been sent successfully. Otherwise, a JSON is returned containing the error message.

## Sample Python Code

```python
import requests
def addDestination(token, destination):
        addDestinationRequest = requests.post('https://api.mspbackups.com/api/Accounts/AddDestination', headers = {"Authorization": "Bearer " + token}, json = destination)

        if addDestinationRequest.status_code == 200:
            print('200')
        else:
            print('Error: ' + str(addDestinationRequest.status_code))

        return addDestinationRequest.status_code

newDestination = {
    "AccountID" : "someMBSaccountID-97f0-4df9-a867-f158ad01220d",
    "Destination" : "s3bucketName",
    "DestinationDisplayName" : "Personal Bucket"
}

addDestination("MBSAPItoken", newDestination)
```

