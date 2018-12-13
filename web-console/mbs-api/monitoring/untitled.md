# User's Plan Execution History

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Monitoring/{userId}" %}
{% api-method-summary %}
Monitor Plan Execution for User
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to receive a detailed history of the latest plan executions.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="userId" type="string" required=true %}
The MBS user whose plans execution status is to be requested
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

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

{% endapi-method-response-example-description %}

```
[{'PlanName': 'Anakonda backup', 'CompanyName': None, 'UserName': 'roberttech', 'UserID': 'someID-1ac6-42b9-8003-51808c40e077', 'ComputerName': 'roberts-mbp.dev.cbl.corp', 'BuildVersion': '2.4.0.17', 'StorageType': 'Cloud', 'LastStart': '2018-05-11T14:50:57', 'NextStart': None, 'Status': 0, 'ErrorMessage': None, 'FilesCopied': 3, 'FilesFailed': 0, 'DataCopied': 531582, 'Duration': '15 second(s)', 'DataToBackup': 531582, 'TotalData': 2425390, 'FilesScanned': 82, 'FilesToBackup': 3}, {'PlanName': 'Backup plan on
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Response Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| PlanName | — | String |
| CompanyName | Company to which the user is assigned | String |
| UserName | User email | String |
| UserID | MBS user ID | String |
| ComputerName | Computer on which the plan was executed | String |
| BuildVersion | Build version | String |
| StorageType | Storage type | String |
| LastStart | Date of the latest execution | Date |
| NextStart | Next execution date | Date |
| Status | Execution status | Success = 0, Overdue = 1, Error = 2, Running = 3, Unknown = 4, Interrupted = 5, UnexpectedlyClosed = 6 |

#### Response Formats

* application/json, text/json
* application/xml, text/xml

#### Sample Python Code

```python
import requests 

def monitoringForUser(token, userID):
		listPlansRequest = requests.get('https://api.mspbackups.com/api/Monitoring/' + userID, headers = {"Accept" : "application/json",
												   "Authorization": "Bearer " + token})

		if listPlansRequest.status_code == 200:
			print("Success!")
			return listPlansRequest.json()
		else:
			print("Error: " + str(listPlansRequest.status_code))
			return listPlansRequest.status_code
			
monitoring("MBSAPItoken", "MBSUserID")
```



