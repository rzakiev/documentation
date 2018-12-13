# Edit a User's Destinations

{% api-method method="put" host="https://api.mspbackups.com" path="/api/Destinations" %}
{% api-method-summary %}
Edit User's Destination
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to edit a user's destination.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Accept" type="string" %}
Specifies the type of data expected in response. Possible values:  "application/json" / "text/json" / "application/xml", "text/xml"
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the type of data expected in response. Possible values:  "application/json" / "text/json" / "application/xml", "text/xml"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="PackageID" type="string" required=false %}
Storage Limit ID. Can be modified.
{% endapi-method-parameter %}

{% api-method-parameter name="Destination" type="string" required=false %}
Storage bucket. Can be modified.
{% endapi-method-parameter %}

{% api-method-parameter name="AccountID" type="string" required=true %}
ID of the account to be edited
{% endapi-method-parameter %}

{% api-method-parameter name="UserID" type="string" required=true %}
ID of the MBS user for whose destination is to be edited
{% endapi-method-parameter %}

{% api-method-parameter name="ID" type="string" required=true %}
ID of the destination
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The user's destinations has been successfully modified
{% endapi-method-response-example-description %}

```
No message is returned
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Sample Python Code

```python
import requests
def editDestination(token, jsonNewDestination):
		editDestinationRequest = requests.put('https://api.mspbackups.com/api/Destinations', headers = { "Authorization": "Bearer " + token}, json = jsonNewDestination)

		if editDestinationRequest.status_code == 200:
			print("Destination has been successfully modified!")
		else:
			print("Error! " + str(editDestinationRequest.status_code))
			return editDestinationRequest.json()

modifiedDestination = {
	"ID" : "Destination ID. Cannot be modified.",
	"UserID" : "MBS user ID. Cannot be modified",
	"AccountID" : "94bf5b06-79a0-4a52-88ed-3sample",
	"Destination" : "main", #can be modified
	"PackageID" : "27755" # can be modified
}			

editDestination("MBSAPItoken", modifiedDestination)
```

