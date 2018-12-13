# Request Custom Builds

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Builds/RequestCustomBuilds" %}
{% api-method-summary %}
Request Custom Builds
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to request custom builds with specified editions
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="Type" type="string" required=true %}
Build Type. Available to end users = 0, Sandbox = 1.
{% endapi-method-parameter %}

{% api-method-parameter name="Editions" type="string" required=true %}
Windows = 0, VirtualMachine = 1, MacOS = 2, LinuxDeb = 3, LinuxRpm = 4, DedupServer = 5
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The build has been successfully requested
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
{
  "Editions": [0, 2, 5],
  "Type": 0
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
<RequestBuilds xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <Editions>
    <BuildEdition>Windows</BuildEdition>
    <BuildEdition>Windows</BuildEdition>
  </Editions>
  <Type>Custom</Type>
</RequestBuilds>
```
{% endtab %}
{% endtabs %}

#### Sample Python Code

```python
import requests
def requestCustomBuild(token, editionType):
		getCustomBuildRequest = requests.post('https://api.mspbakcups.com/api/Builds/requestCustomBuilds', headers = {"Accept" : "application/json",
												   "Authorization": "Bearer " + token}, json = editionType)

		if getCustomBuildRequest.status_code == 200:
			print('200')
		else:
			return getCustomBuildRequest.status_code

build = {
	"Editions" : [0,2,5],
	"Type" : "0"
}

requestCustomBuild("MBStoken", build)
```

