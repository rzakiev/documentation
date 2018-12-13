# Revoke License from User

{% api-method method="post" host="https://api.mspbackups.com" path="/api/Licenses/Revoke" %}
{% api-method-summary %}
Revoke License from User
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to revoke a license from a computer. Unlike license release, license revocation deactivates a license from the user's computer but retains it in the list of licenses available to the user. 
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
ID of the MBS user
{% endapi-method-parameter %}

{% api-method-parameter name="LicenseID" type="string" required=true %}
ID of the license to be released
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The license has been successfully returned
{% endapi-method-response-example-description %}

```
No message is returned
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="warning" %}
The user shouldn't be allowed to activate licenses from the global pool automatically. Otherwise, license revocation will not work properly.  
{% endhint %}

#### Request Format

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

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

```python
import requests
def revokeLicenseFromUser(token, licenseID, userID):
		revokeLicenseFromUserRequest = requests.post('https://api.mspbackups.com/api/Licenses/Revoke', headers = {"Authorization": "Bearer " + token}, json = {"LicenseID" : licenseID, "UserID" : userID})

		if revokeLicenseFromUserRequest.status_code == 200:
			print("200")
			try:
				print(revokeLicenseFromUserRequest.json())
				return 1
			except:
				return 0
		else:
			print("Error :" + str(revokeLicenseFromUserRequest.status_code))
			return revokeLicenseFromUserRequest.status_code()
			
revokeLicenseFromUser(MBStoken, licenseID, userID)
```



