# Grant License to User

{% api-method method="post" host="https://api.mspbackups.com" path="/api/Licenses/Grant" %}
{% api-method-summary %}
Grant License to User
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to grant a license to a user.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="UserID" type="string" required=true %}
MBS user ID
{% endapi-method-parameter %}

{% api-method-parameter name="LicenseID" type="string" required=true %}
ID of the MBS license you'd like to grant.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The license has been successfully granted to the user.
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

#### Response Information

None.

#### Sample Python Code

```python
import requests
def grantLicenseToUser(token, licenseID, userID):

		grantLicenseToUserRequest = requests.post('https://api.mspbackups.com/api/Licenses/Grant', headers = {"Authorization": "Bearer " + token}, json = {"LicenseID" : licenseID, "UserID" : userID})

		if grantLicenseToUserRequest.status_code == 200:
			print("The license has been granted to the user!")
			try:
				grantLicenseToUserRequest.json()
				return 1
			except:
				return 0
		else:
			print("Error: " + str(grantLicenseToUserRequest.status_code))
			print(grantLicenseToUserRequest.json())
			return grantLicenseToUserRequest.status_code
			
grantLicenseToUser(MBSAPItoken, licenseID, userID)
```

