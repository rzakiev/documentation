# Get Filtered Billing Records

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Billing" %}
{% api-method-summary %}
Get Filtered Billing records
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to get billing records filtered by company name and date.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}

{% api-method-parameter name="Accept" type="string" %}
Specifies the type of data expected in response. Possible values:  "application/json" / "text/json" / "application/xml", "text/xml"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="Date" type="string" required=false %}
Date. If empty, the current date will be set.
{% endapi-method-parameter %}

{% api-method-parameter name="CompanyName" type="string" required=false %}
Company name
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{'CurrentSpaceUsed': 0, 'AverageSpaceUsed': 0, 'TotalRestore': 0, 'StatisticBilling': [{'UserId': 'someID-f98c-4fbd-aa0d-b1b5551f2df3', 'Email': 'zakiev@me.com', 'FirstName': 'Robert', 'LastName': 'Zakiev', 'CompanyName': 'QA team', 'AverageSpace': 0, 'TotalVolumeRestore': 0, 'PlanCost': 1.0, 'StorageCost': 0.0, 'RestoreCost': 0.0, 'TotalCost': 1.0, 'LicensesUsed': 0}]}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
{
  "CompanyName": "Los Pollos Hermanos",
  "Date": "2018-05-15T12:38:46.8345309+00:00"
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<FilterTotalModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <CompanyName>sample string 1</CompanyName>
  <Date>2018-05-15T12:38:46.8345309+00:00</Date>
</FilterTotalModels>
```
{% endtab %}
{% endtabs %}

#### Response Information

Identical to the information received when requesting billing records for the current month

#### Sample Python Code

```python
import requests
def billingDetailsFilteredBy(criteria, token):
		billingDetailsRequest = requests.put('https://api.mspbackups.com/api/Billing', headers = {"Accept" : "application/json",
												   "Authorization": "Bearer " + token}, json = criteria)

		if billingDetailsRequest.status_code == 200:
			print('200')
			return billingDetailsRequest.json()
		else:
			return billingDetailsRequest.status_code

criteria = {
	"CompanyName" : "QA team",
	"Date" : "2018-05-15T12:38:46.8345309+00:00"
}

billingDetailsFilteredBy(criteria, "MBSAPItoken")
```

