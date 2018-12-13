# List Available Licenses

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Licenses?isAvailable={bool}" %}
{% api-method-summary %}
List Available Licenses
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to list all available/unavailable licenses.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="isAvailable" type="string" required=true %}
Indicates if only available licenses should be listed
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
License have been successfully received!
{% endapi-method-response-example-description %}

```
{'ID': 'license-023a-4555-88db-02f811894b00', 'Number': 6, 'ComputerName': None, 'OperatingSystem': None, 'IsTrial': False, 'IsTaken': False, 'LicenseType': 'Ultimate', 'DateExpired': '2018-02-09T00:00:00', 'Transaction': 'transactionID-f3de-4233-a1cd-ac0e9086015b', 'User': None, 'UserID': None}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Response Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| ID | License ID | String |
| Number | License number | Integer |
| ComputerName | Computer name | String |
| OperatingSystem | — | String |
| IsTrial | Indicates if the license is a trial one | Boolean |
| isTaken | Indicates if the license if activated | Boolean |
| LicensyType | License type | String |
| DateExpired | License expiration date | Date |
| Transaction | License transaction | String |
| User | License user | String |
| UserID | License userID  | String |

#### Response Formats

* application/json, text/json
* application/xml, text/xml

#### Sample Python Code

```python
import requests
def getLicenses(token, isAvailable):
		getLicensesRequest = requests.get('https://api.mspbackups.com/api/Licenses?isAvailable=' + str(isAvailable), headers = {"Accept" : "application/json",
												   "Authorization": "Bearer " + token})

		if getLicensesRequest.status_code == 200:
			print("Successful license listing!")
			return getLicensesRequest.json()
		else:
			print("Error: " + str(getLicensesRequest.status_code))
			getLicensesRequest.status_code

getLicenses("MBSAPItoken", True)
```

