# Edit a Package

{% api-method method="put" host="https://api.mspbackups.com" path="/api/Packages" %}
{% api-method-summary %}
Edit Package
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to edit an existing MBS package.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="ID" type="string" required=true %}
Package ID
{% endapi-method-parameter %}

{% api-method-parameter name="Enabled" type="boolean" required=true %}
Indicates if the packages is enabled or disabled
{% endapi-method-parameter %}

{% api-method-parameter name="Name" type="string" required=true %}
Package name.
{% endapi-method-parameter %}

{% api-method-parameter name="StorageLimit" type="number" required=true %}
Storage limit in gigabytes.
{% endapi-method-parameter %}

{% api-method-parameter name="isGlacierRestoreLimit" type="boolean" required=true %}
Indicates if Glacier Restore Limit applies to the package.
{% endapi-method-parameter %}

{% api-method-parameter name="Cost" type="string" required=true %}
Cost limit.
{% endapi-method-parameter %}

{% api-method-parameter name="Description" type="string" required=false %}
Package description.
{% endapi-method-parameter %}

{% api-method-parameter name="RestoreLimit" type="string" required=false %}
Restore limit.
{% endapi-method-parameter %}

{% api-method-parameter name="GlacierRestoreType" type="number" %}
Standard = 0, Bulk = 1, Expedited = 2, No = 3.
{% endapi-method-parameter %}

{% api-method-parameter name="UseRestoreLimit" type="string" required=false %}
Indicates if restore limit is used.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The package has been successfully modified!
{% endapi-method-response-example-description %}

```
No message is returned
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
	"ID" : "44988",
	"Enabled" : True,
	"Name" : "100-GB Limit",
	"Description" : "Royal Limit",
	"StorageLimit" : 100.0,
	"isGlacierRestoreLimit" : False,
	"GlacierRestoreType" : 0,
	"Cost" : 100.0,
	"UseRestoreLimit" : True
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<PackagesModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
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
```
{% endtab %}
{% endtabs %}

#### Response Information

None.

#### Sample Python Code

```python
import requests
def editPackage(token, package):
		editPackageRequest = requests.put('https://api.mspbackups.com/api/Packages', headers = {"Accept" : "application/json",
												   "Authorization": "Bearer " + token}, json = package)

		if editPackageRequest.status_code == 200:
			print("Package has been successfully modified!")
		else:
			print("Error :" + str(editPackageRequest.status_code))
			return editPackageRequest.status_code
			
editedPackage = {
	"ID" : "44988",
	"Enabled" : True,
	"Name" : "100-GB Limit",
	"Description" : "Royal Limit",
	"StorageLimit" : 100.0,
	"isGlacierRestoreLimit" : False,
	"GlacierRestoreType" : 0,
	"Cost" : 100.0,
	"UseRestoreLimit" : True
}

editPackage(editedPackage)
```



