# Get a User's Packages

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Packages/{userID}" %}
{% api-method-summary %}
Get a User's Packages
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to list a user's packages.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Value: "Bearer \*token\*"
{% endapi-method-parameter %}

{% api-method-parameter name="Accept" type="string" %}
Specifies the type of data expected in response. Possible values: "application/json" / "text/json" / "application/xml", "text/xml"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The packages have been successfully listed
{% endapi-method-response-example-description %}

```text
{'ID': someID, 'Cost': 30.0, 'Description': '20-gigabyte limit for new employees.', 'Enabled': True, 'Name': '20-GB Limit', 'StorageLimit': 20.0, 'isGlacierRestoreLimit': False, 'RestoreLimit': -1.0, 'GlacierRestoreType': 0, 'UseRestoreLimit': False}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| ID | Package unique identifier | Integer |
| Cost | Cost limit | Decimal |
| Description | — | String |
| Enabled | Indicates if the limit is enabled | Boolean |
| Name | Name of the package | String |
| StorageLimit | Storage limit | Decimal |
| isGlacierRestoreLimit | Indicates of Glacier restore limit applies to the package | Boolean |
| RestoreLimit | Restore limit | Decimal |
| GlacierRestoreType | Glacier Restore Type | Standard = 0, Bulk = 1, Expedited = 2, No = 3 |
| UserRestoreLimit | Indicates if restore limit is used | Boolean |

## Response Formatsa

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
[
  {
    "ID": 1,
    "Cost": 2.0,
    "Description": "sample string 3",
    "Enabled": true,
    "Name": "sample string 5",
    "StorageLimit": 6.1,
    "isGlacierRestoreLimit": true,
    "RestoreLimit": 8.1,
    "GlacierRestoreType": 0,
    "UseRestoreLimit": true
  },
  {
    "ID": 1,
    "Cost": 2.0,
    "Description": "sample string 3",
    "Enabled": true,
    "Name": "sample string 5",
    "StorageLimit": 6.1,
    "isGlacierRestoreLimit": true,
    "RestoreLimit": 8.1,
    "GlacierRestoreType": 0,
    "UseRestoreLimit": true
  }
]
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<ArrayOfPackagesModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <PackagesModels>
    <Cost>2</Cost>
    <Description>sample string 3</Description>
    <Enabled>true</Enabled>
    <GlacierRestoreType>Standard</GlacierRestoreType>
    <ID>1</ID>
    <Name>sample string 5</Name>
    <RestoreLimit>8.1</RestoreLimit>
    <StorageLimit>6.1</StorageLimit>
    <UseRestoreLimit>true</UseRestoreLimit>
    <isGlacierRestoreLimit>true</isGlacierRestoreLimit>
  </PackagesModels>
  <PackagesModels>
    <Cost>2</Cost>
    <Description>sample string 3</Description>
    <Enabled>true</Enabled>
    <GlacierRestoreType>Standard</GlacierRestoreType>
    <ID>1</ID>
    <Name>sample string 5</Name>
    <RestoreLimit>8.1</RestoreLimit>
    <StorageLimit>6.1</StorageLimit>
    <UseRestoreLimit>true</UseRestoreLimit>
    <isGlacierRestoreLimit>true</isGlacierRestoreLimit>
  </PackagesModels>
</ArrayOfPackagesModels>
```
{% endtab %}
{% endtabs %}

## Sample Python Code

```python
import requests
def getUsersPackages(token, userID):
        listPackageStructureRequest = requests.get('https://api.mspbackups.com/api/Packages/' + userID, headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token})
        try:
            return listPackageStructureRequest.json()
        except:
            return listPackageStructureRequest.status_code

charliesPackages = getUsersPackages("MBSAPItoken", "Charlie's ID")
```

