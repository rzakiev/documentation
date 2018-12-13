# Get Billing for Current Month

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Billing" %}
{% api-method-summary %}
Get Billing Information for Current Month
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to get billing information for the current month.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
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
The billing information for the current month has been successfully received.
{% endapi-method-response-example-description %}

```text
{'CurrentSpaceUsed': 77060622, 'AverageSpaceUsed': 71852916, 'TotalRestore': 0, 'StatisticBilling': [{'UserId': 'sample-7567-4965-8c8a-bee5bf6b056d', 'Email': 'user', 'FirstName': 'John', 'LastName': 'Techhead', 'CompanyName': None, 'AverageSpace': 0, 'TotalVolumeRestore': 0, 'PlanCost': 1.0, 'StorageCost': 0.0, 'RestoreCost': 0.0, 'TotalCost': 1.0, 'LicensesUsed': 0},
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| CurrentSpaceUsed | Space currently used by all users in bytes. The value is updated daily. | Integer |
| AverageSpaceUsed | Average of space used by all users for the current month in bytes. | Integer |
| TotalRestore | Gross restore volume. | Integer |
| StatisticBilling | Detailed information for each user | StatisticBilliingModel |

* StatisticBillingModel parameters:

| Parameter | Description | Value |
| :--- | :--- | :--- |
| UserId | MBS user ID | String |
| Email | User login \(email\) | String |
| FirstName | User's first name | String |
| LastName | User's last name | String |
| CompanyName | Company Name | String |
| AverageSpace | Average space used | Integer |
| TotalVolumeRestore | Gross Restore Volume | Integer |
| PlanCost | Plan cost | Decimal |
| StorageCost | Storage cost | Decimal |
| RestoreCost | Restore cost | Decimal |
| TotalCost | Total Cost | Decimal |
| LicensesUsed | Number of licenses use by the user | Integer |

## Response Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
{
  "CurrentSpaceUsed": 1,
  "AverageSpaceUsed": 2,
  "TotalRestore": 3,
  "StatisticBilling": [
    {
      "UserId": "e9e498ce-4cec-4df7-83d4-c7065143795e",
      "Email": "sample string 2",
      "FirstName": "sample string 3",
      "LastName": "sample string 4",
      "CompanyName": "sample string 5",
      "AverageSpace": 6,
      "TotalVolumeRestore": 7,
      "PlanCost": 8.0,
      "StorageCost": 9.0,
      "RestoreCost": 10.0,
      "TotalCost": 11.0,
      "LicensesUsed": 12
    },
    {
      "UserId": "e9e498ce-4cec-4df7-83d4-c7065143795e",
      "Email": "sample string 2",
      "FirstName": "sample string 3",
      "LastName": "sample string 4",
      "CompanyName": "sample string 5",
      "AverageSpace": 6,
      "TotalVolumeRestore": 7,
      "PlanCost": 8.0,
      "StorageCost": 9.0,
      "RestoreCost": 10.0,
      "TotalCost": 11.0,
      "LicensesUsed": 12
    }
  ]
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<BillingModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <AverageSpaceUsed>2</AverageSpaceUsed>
  <CurrentSpaceUsed>1</CurrentSpaceUsed>
  <StatisticBilling>
    <StatisticBillingModels>
      <AverageSpace>6</AverageSpace>
      <CompanyName>sample string 5</CompanyName>
      <Email>sample string 2</Email>
      <FirstName>sample string 3</FirstName>
      <LastName>sample string 4</LastName>
      <LicensesUsed>12</LicensesUsed>
      <PlanCost>8</PlanCost>
      <RestoreCost>10</RestoreCost>
      <StorageCost>9</StorageCost>
      <TotalCost>11</TotalCost>
      <TotalVolumeRestore>7</TotalVolumeRestore>
      <UserId>e9e498ce-4cec-4df7-83d4-c7065143795e</UserId>
    </StatisticBillingModels>
    <StatisticBillingModels>
      <AverageSpace>6</AverageSpace>
      <CompanyName>sample string 5</CompanyName>
      <Email>sample string 2</Email>
      <FirstName>sample string 3</FirstName>
      <LastName>sample string 4</LastName>
      <LicensesUsed>12</LicensesUsed>
      <PlanCost>8</PlanCost>
      <RestoreCost>10</RestoreCost>
      <StorageCost>9</StorageCost>
      <TotalCost>11</TotalCost>
      <TotalVolumeRestore>7</TotalVolumeRestore>
      <UserId>e9e498ce-4cec-4df7-83d4-c7065143795e</UserId>
    </StatisticBillingModels>
  </StatisticBilling>
  <TotalRestore>3</TotalRestore>
</BillingModels>
```
{% endtab %}
{% endtabs %}

## Sample Python Code

```python
import requests
def billingDetailsForCurrentMonth(token):
        billingDetailsForCurrentMonthRequest = requests.get('https://api.mspbackups.com/api/Billing', headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token})

        if billingDetailsForCurrentMonthRequest.status_code == 200:
            print('200')
            return billingDetailsForCurrentMonthRequest.json()
        else:
            return billingDetailsForCurrentMonthRequest.status_code

billingDetailsForCurrentMonth(MBSAPItoken)
```

