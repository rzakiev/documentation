# Add Destinations to a User

{% api-method method="post" host="https://api.mspbackups.com" path="/api/Destinations" %}
{% api-method-summary %}
Add Destinations to a User
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to add destinations to a particular user.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="PackageID" type="number" required=true %}
ID of the MBS package \(Can be listed using _GET api/Packages_\)
{% endapi-method-parameter %}

{% api-method-parameter name="Destination" type="string" required=true %}
Target storage bucket
{% endapi-method-parameter %}

{% api-method-parameter name="AccountID" type="string" required=true %}
ID of the destination
{% endapi-method-parameter %}

{% api-method-parameter name="UserID" type="string" required=true %}
ID of the MBS user
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The specified destinations have been successfully added to the user.
{% endapi-method-response-example-description %}

```text
No message is returned
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
Sample:
{
  "UserID": "MBS user ID",
  "AccountID": "Storage Account ID",
  "Destination": "Storage Bucket",
  "PackageID": "MBSpackageID"
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<AddUserDestination xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <AccountID>sample string 2</AccountID>
  <Destination>sample string 3</Destination>
  <PackageID>4</PackageID>
  <UserID>sample string 1</UserID>
</AddUserDestination>
```
{% endtab %}
{% endtabs %}

## Response Information

None.

## Sample Python Code

```python
import requests
def addDestinationToUser(token, userEmail, jsonDestinations):
        addDestinationToUserRequest = requests.post('https://api.mspbackups.com/api/Destinations', headers = { "Authorization": "Bearer " + token}, json = jsonDestinations)

        if addDestinationToUserRequest.status_code == 200:
            print("Destinations have been successfully added!")
        else:
            print("Error! " + addDestinationToUserRequest.status_code)

        return addDestinationToUserRequest.status_code

destinationToAppend = {
    "UserID" : "e6199730-f98c-4fbd-aa0d-b1b5551f2df3",
    "AccountID" : "94bf5b06-79a0-4a52-88ed-36da652f4254",
    "Destination" : "main",
    "PackageID" : "27755"
}

addDestinationToUser("MBSAPItoken", "user@company.com", destinationToAppend)
```

