# Get a Package Structure

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Packages/{id}" %}
{% api-method-summary %}
Get a Package Structure
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to get a breakdown of a storage limit.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the Package
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
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
The user's packages have been successfully received
{% endapi-method-response-example-description %}

```text
{'ID': 20988, 'Cost': 0.0, 'Description': "10-gig limit", 'Enabled': True, 'Name': '10 gigs', 'StorageLimit': 10.0, 'isGlacierRestoreLimit': False, 'RestoreLimit': -1.0, 'GlacierRestoreType': 0, 'UseRestoreLimit': True}
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

## Response Formats

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
def getPackageStructure(token, packageID):
        listPackageStructureRequest = requests.get('https://api.mspbackups.com/api/Packages/' + packageID, headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token})
        try:
            return listPackageStructureRequest.json()
        except:
            return listPackageStructureRequest.status_code

packageStructure = getPackageStructure("MBSAPItoken", "packageID")
```

