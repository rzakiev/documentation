# Delete an Administrator

{% api-method method="delete" host="https://api.mspbackups.com" path="/api/Administrators/{id}" %}
{% api-method-summary %}
Delete Administrator
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to delete an MBS administrator.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the administrator to be deleted
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
The administrator has been successfully deleted
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
def deleteAdministrator(token, adminID):
		deleteAdministratorRequest = requests.delete('https://api.mspbackups.com/api/Administrators/' + adminID, headers = {"Authorization": "Bearer " + token})

		if deleteAdministratorRequest.status_code == 200:
			print('200')
			return deleteAdministratorRequest.json()
		else:
			return deleteAdministratorRequest.status_code
			
deleteAdministrator(MBSAPItoken)
```

