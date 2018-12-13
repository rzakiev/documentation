# List Available Builds

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Builds" %}
{% api-method-summary %}
List Available Builds
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to list builds available to users.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorize" required=true type="string" %}
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
The builds have been successfully listed
{% endapi-method-response-example-description %}

```text
[{'Type': 'Windows', 'Version': '5.8.6.28', 'DownloadLink': 'http://s3.amazonaws.com/cb_setups/MBS/B91F2C34-88AD-43C0-8648/CBLCompanyonlinebackup_v5.8.6.28_netv4.0_ALLEDITIONS_Setup_20180503154124.exe'}, {'Type': 'macOS', 'Version': '2.4.0.17', 'DownloadLink': 'http://s3.amazonaws.com/cb_setups/MBS/B91F2C34-88AD-43C0-8648/mac_CBLCompany_onlinebackup_v2.4.0.17_20180503154137.pkg'}]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| Type | Build type | String |
| Version | Build version | String |
| DownloadLink | Download link | String |

## Response Information

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
[
  {
    "Type": "sample string 1",
    "Version": "sample string 2",
    "DownloadLink": "sample string 3"
  },
  {
    "Type": "sample string 1",
    "Version": "sample string 2",
    "DownloadLink": "sample string 3"
  }
]
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<ArrayOfBuildModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <BuildModels>
    <DownloadLink>sample string 3</DownloadLink>
    <Type>sample string 1</Type>
    <Version>sample string 2</Version>
  </BuildModels>
  <BuildModels>
    <DownloadLink>sample string 3</DownloadLink>
    <Type>sample string 1</Type>
    <Version>sample string 2</Version>
  </BuildModels>
</ArrayOfBuildModels>
```
{% endtab %}
{% endtabs %}

## Sample Python Code

```python
import requests
def getBuilds(token):
        getBuildsRequest = requests.get('https://api.mspbackups.com/api/Builds', headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token})

        if getBuildsRequest.status_code == 200:
            print('200')
            return getBuildsRequest.json()
        else:
            return getBuildsRequest.status_code

getBuilds("MBSAPItoken")
```

