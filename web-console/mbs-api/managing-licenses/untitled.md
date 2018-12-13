# Get License Information

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Licenses{id}" %}
{% api-method-summary %}
Get License Information
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to receive information on a particular license.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
MBS License ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}

{% api-method-parameter name="Accept" type="string" %}
Specifies the type of data expected in response. Possible values: "application/json" / "text/json" / "application/xml", "text/xml"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The license information has been successfully received
{% endapi-method-response-example-description %}

```text
{'ID': 'license-eaa1-4628-9fbf-sample', 'Number': 4, 'ComputerName': None, 'OperatingSystem': None, 'IsTrial': False, 'IsTaken': False, 'LicenseType': 'File Backup', 'DateExpired': '2017-12-07T00:00:00', 'Transaction': 'transaction-e205-4efa-87b2-f36bbc5eda6e', 'User': None, 'UserID': None}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response Information

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
| UserID | License userID | String |

## Response Formats

* application/json, text/json
* application/xml, text/xml

## Sample Python Code

```python
import requests
def getLicenseInfo(token, licenseID):
        getLicensesForuserRequest = requests.get('https://api.mspbackups.com/api/Licenses/' + licenseID, headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token})

        if getLicensesForuserRequest.status_code == 200:
            print('Successful license listing!')
            return getLicensesForuserRequest.json()
        else:
            print("Error: " +str(getLicensesForuserRequest.status_code))
            return getLicensesForuserRequest.status_code

getLicenseInfo("MBSAPItoken", "MBSlicenseID")
```

