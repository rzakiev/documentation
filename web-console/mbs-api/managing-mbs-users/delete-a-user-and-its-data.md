# Delete a User and their Data

{% api-method method="delete" host="https://api.mspbackups.com" path="/api/Users/{id}" %}
{% api-method-summary %}
Delete User and their Data
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to delete a user and all of the information related to this user. The user's data will be deleted from the backup storage within 24 hours.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="ID" type="string" required=true %}
ID of the MBS user to be deleted.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The user's data has been successfully deleted
{% endapi-method-response-example-description %}

```text
No message is returned
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response Information

None.

## Sample Python Code

```python
import requests 
def deleteUserAndData(token, userID):
        deleteUserRequest = requests.delete('https://api.mspbackups.com/api/Users/' + userID, headers = {"Authorization": "Bearer " + token})
        print("Delete user status code: " + str(deleteUserRequest.status_code) + "\n")
        return deleteUserRequest.status_code

deleteUserAndData("MBSAPItoken", "MBSuserID")
```

