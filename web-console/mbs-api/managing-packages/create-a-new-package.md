# Create a New Package

{% api-method method="post" host="https://api.mspbackups.com" path="/api/Packages" %}
{% api-method-summary %}
Create a New Package
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to create a new MBS package.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
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
The package has been successfully created!
{% endapi-method-response-example-description %}

```text
No message is returned
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Request Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
{
    "Name" : "30-GB Limit",
    "Description" : "30-gigabyte limit for new employees.",
    "StorageLimit" : 30.0,
    "isGlacierRestoreLimit" : False,
    "GlacierRestoreType" : 0,
    "Cost" : 40.0,
    "UseRestoreLimit" : True
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<PackageCreate xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <Cost>6</Cost>
  <Description>sample string 2</Description>
  <GlacierRestoreType>Standard</GlacierRestoreType>
  <Name>sample string 1</Name>
  <RestoreLimit>5.1</RestoreLimit>
  <StorageLimit>3.1</StorageLimit>
  <UseRestoreLimit>true</UseRestoreLimit>
  <isGlacierRestoreLimit>true</isGlacierRestoreLimit>
</PackageCreate>
```
{% endtab %}
{% endtabs %}

## Response Information

None.

## Sample Python Code

```python
import requests

def createNewPackage(token, package):
        createNewPackageRequest = requests.post('https://api.mspbackups.com/api/Packages', headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token}, json = package)
        if createNewPackageRequest.status_code == 200:
            print ("Create new package: success!")
        else:
            print("Error: " + str(createNewPackageRequest.status_code))
            return createNewPackageRequest.status_code

newPackage = {
    "Name" : "30-GB Limit",
    "Description" : "30-gigabyte limit for new employees.",
    "StorageLimit" : 30.0,
    "isGlacierRestoreLimit" : False,
    "GlacierRestoreType" : 0,
    "Cost" : 40.0,
    "UseRestoreLimit" : True
}

createNewPackage ("MBSAPItoken", newPackage)
```

