# Delete a User Without Its Data

{% api-method method="delete" host="https://api.mspbackups.com" path="/api/Users/{id}/Account" %}
{% api-method-summary %}
Delete User without Data
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to delete a user without deleting their data in the backup storage. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the MBS user to be deleted.
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
The user has been successfully deleted
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
def deleteUser(token, userID):
		deleteUserRequest = requests.delete('https://api.mspbackups.com/api/Users/' + userID + '/Account', headers = {
												   "Authorization": "Bearer " + token})
		print("Delete user status code: " + str(deleteUserRequest.status_code) + "\n")
		return deleteUserRequest.status_code

deleteUser("mbsAPItoken", "MBSUserID")
```

