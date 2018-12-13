# Delete a User's Destination

{% api-method method="delete" host="https://api.mspbackups.com" path="/api/Destinations/{id}?userId={userId}" %}
{% api-method-summary %}
Delete a User's Destination
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to delete a user's destinations.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="userID" type="string" required=true %}
ID of the user for whom the destination is to be removed
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
Id of the destination to be removed
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Destinations have been successfully deleted. 
{% endapi-method-response-example-description %}

```
No message is returned
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Response Information

None.

#### Sample Python Code

```python
import requests
def deleteDestinationForUser(token, destinationID, userID):
		deleteDestinationForUserRequest = requests.delete('https://api.mspbackups.com/api/Destinations/' + destinationID + '?userId=' + userID, headers = { "Authorization": "Bearer " + token})

		if deleteDestinationForUserRequest.status_code == 200:
			print("Destinations have been successfully deleted!")
		else:
			print('Error! ' + str(deleteDestinationForUserRequest.status_code))

deleteDestinationsForUser("MBSAPItoken", "destinationID", "MBSUserID")
```

