# Get Latest Available Versions

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Builds/AvailableVersions" %}
{% api-method-summary %}
Get Latest Available Versions
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to get the latest available versions.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
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
The latest versions have been successfully listed
{% endapi-method-response-example-description %}

```text
[{'Type': 0, 'Version': '5.9.0.274'}, {'Type': 1, 'Version': '5.9.0.274'}, {'Type': 2, 'Version': '2.4.3.11'}, {'Type': 3, 'Version': '2.4.3.11'}, {'Type': 4, 'Version': '2.4.3.11'}, {'Type': 5, 'Version': '2.3.1.42'}]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| Type | Build type | Windows = 0, VirtualMachine = 1, MacOS = 2, LinuxDeb = 3, LinuxRpm = 4, DedupServer = 5 |
| Version | Build version | String |

## Response Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
[{'Type': 0, 'Version': '5.9.0.274'}, 
 {'Type': 1, 'Version': '5.9.0.274'}, 
 {'Type': 2, 'Version': '2.4.3.11'}, 
 {'Type': 3, 'Version': '2.4.3.11'}, 
 {'Type': 4, 'Version': '2.4.3.11'}, 
 {'Type': 5, 'Version': '2.3.1.42'}]
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
<ArrayOfBuildEditionModel xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <BuildEditionModel>
    <Type>Windows</Type>
    <Version>sample string 1</Version>
  </BuildEditionModel>
  <BuildEditionModel>
    <Type>Windows</Type>
    <Version>sample string 1</Version>
  </BuildEditionModel>
</ArrayOfBuildEditionModel>
```
{% endtab %}
{% endtabs %}

## Sample Python Code

```python
import requests
def getLatestVersions(token):
        getLatestVersions = requests.get('https://api.mspbackups.com/api/Builds/AvailableVersions', headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token})

        if getLatestVersions.status_code == 200:
            print('200')
            return getLatestVersions.json()
        else: 
            return getLatestVersions.status_code

getLatestVersions("MBStoken")
```

