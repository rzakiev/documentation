# Release License from User

{% api-method method="post" host="https://api.mspbackups.com" path="/api/Licenses/Release" %}
{% api-method-summary %}
Release License from User
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to release a license form user. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="UserID" type="string" required=true %}
MBS user ID
{% endapi-method-parameter %}

{% api-method-parameter name="LicenseID" type="string" required=true %}
ID of the license to be released
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The license has been successfully released from the user
{% endapi-method-response-example-description %}

```
No message is returned
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

####  Request Formats <a id="request-formats"></a>

{% tabs %}
{% tab title="JSON" %}
* applications/json, text/json

```javascript
Sample:
{  
"LicenseID": "sample string 1",  
"UserID": "sample string 2"
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<LicenseOperation xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models"> 
    <LicenseID>sample string 1</LicenseID>  
    <UserID>sample string 2</UserID>
</LicenseOperation>
```
{% endtab %}
{% endtabs %}

#### Response Information <a id="response-information-2"></a>

None if the request has been sent successfully. Otherwise, a JSON is returned containing the error message.  


#### Sample Python Code

```python
import requests
def releaseLicenseFromUser(token, licenseID, userID):
		releaseLicenseFromUserRequest = requests.post('https://api.mspbackups.com/api/Licenses/Release', headers = {"Authorization": "Bearer " + token}, json = {"LicenseID" : licenseID, "UserID" : userID})

		if releaseLicenseFromUserRequest.status_code == 200:
			print("200")
			try:
				print(releaseLicenseFromUserRequest.json())
				return 1
			except:
				return 0
		else:
			print("Error :" + str(releaseLicenseFromUserRequest.status_code))
			return releaseLicenseFromUserRequest.status_code()

releaseLicenseFromUser(MBSAPItoken, licenseID, userID):
```

