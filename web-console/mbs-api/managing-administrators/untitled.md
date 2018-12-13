# Get an Administrator's Information by ID

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Administrators/{id}" %}
{% api-method-summary %}
Get Administrator Info by ID
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to request information on a particular administrator.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the administrator.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
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
The administrator's information has been successfully received
{% endapi-method-response-example-description %}

```
[{'AdminID': 'sample-1656-40b4-bc64-f4299a8303fc', 'Email': 'testuser', 'FirstName': 'Main', 'LastName': 'Administrator', 'Enabled': True, 'PermissionsModels': {'Users': 1, 'StorageLimit': 0, 'Notification': 1, 'OnlineAccess': 0, 'Licenses': 1, 'Billing': 1, 'Monitiring': 0, 'RemoteDeploy': 0, 'RemoteManagment': 0, 'HelpMarketing': 0, 'AuditLog': 0, 'PSA': 0, 'Administrators': 0, 'Rebranding': 0, 'Storage': 0, 'ADS': 0, 'LicenseBuy': 0, 'LicenseActivate': 0, 'StorageUsage': 1, 'CapacityReport': 1, 'GoogleApps': 0, 'Dashboard': 0}, 'LastLogin': None, 'DateCreated': '2018-05-15T15:44:51.07', 'Companies': []}]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Response Information

Identical to the information received when listing administrators.

#### Response Formats

* application/json, text/json
* application/xml, text/xml

#### Sample Python Code

```python
import requests
def getAdministratorByID(token, adminID):
		getAdministratorByIDRequest = requests.get('https://api.mspbackups.com/api/Administrators/' + adminID, headers = {"Accept" : "application/json",
												   "Authorization": "Bearer " + token})

		if getAdministratorByIDRequest.status_code == 200:
			print('200')
			return getAdministratorByIDRequest.json()
		else:
			return getAdministratorByIDRequest.status_code
			
getAdministratorByID("MBSAPItoken", "adminID")
```

