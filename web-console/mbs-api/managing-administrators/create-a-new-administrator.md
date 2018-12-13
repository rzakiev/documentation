# Create a New Administrator

{% api-method method="post" host="https://api.mspbackups.com" path="/api/Administrators" %}
{% api-method-summary %}
Create New Administrator
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to create a new administrator.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The administrator has been successfully created!
{% endapi-method-response-example-description %}

```text
adminID
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Request Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| Email \(REQUIRED\) | Administrator's email | String |
| InitialPassword \(REQUIRED\) | Initial password | String |
| FirstName | First name | String |
| LastName | Last name | String |
| Enabled | Indicates if the administrator is enabled or disabled | Bool |
| PermissionsModels \(REQUIRED\) | Administrator's permissions | PermissionsModels |
| Companies | Companies to which the administrator is assigned | Collection of String |

* PermissionsModels parameters:

| Parameter | Description | Value |
| :--- | :--- | :--- |
| Users | User management permission | Forbidden = 0, Permitted = 1 |
| StorageLimit | Storage limit management permission | Forbidden = 0, Permitted = 1 |
| Notification | Notification management permission | Forbidden = 0, Permitted = 1 |
| OnlineAccess | Online Access permission | Forbidden = 0, Permitted = 1 |
| Licenses | Licenses management permission | Forbidden = 0, Permitted = 1 |
| Billing | Billing management permission | Forbidden = 0, Permitted = 1 |
| Monitiring | Monitoring management permission | Forbidden = 0, Permitted = 1 |
| RemoteDeploy | Remote deploy management permission | Forbidden = 0, Permitted = 1 |
| RemoteManagment | Remote management permission | Forbidden = 0, Permitted = 1 |
| HelpMarketing | Marketing and help management permission | Forbidden = 0, Permitted = 1 |
| AuditLog | Log audit permission | Forbidden = 0, Permitted = 1 |
| PSA | ConnectWise & Autotask management permission | Forbidden = 0, Permitted = 1 |
| Administrators | Administrators management permission | Forbidden = 0, Permitted = 1 |
| Rebranding | Rebranding management permission | Forbidden = 0, Permitted = 1 |
| Storage | Storage management permission | Forbidden = 0, Permitted = 1 |
| ADS | AD Bridge management permission | Forbidden = 0, Permitted = 1 |
| LicenseBuy | License purchase permission | Forbidden = 0, Permitted = 1 |
| LicenseActivate | License activation permission | Forbidden = 0, Permitted = 1 |
| StorageUsage | Storage usage management permission | Forbidden = 0, Permitted = 1 |
| CapacityReport | Capacity report permission | Forbidden = 0, Permitted = 1 |
| GoogleApps | Google Apps management permission | Forbidden = 0, Permitted = 1 |
| Dashboard | Dashboard access | Forbidden = 0, Permitted = 1 |

## Request Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
newAdmin = {
    "Email" : "test@test.com",
    "InitialPassword" : "truepass",
    "SendInstruction" : "true",
    "FirstName" : "Robert",
    "LastName" : "QA",
    "Enabled" : "true",
    "PermissionsModels": {
        "Users": 1,
        "StorageLimit": 1,
        "Notification": 0,
        "OnlineAccess": 1,
        "Licenses": 1,
        "Billing":1,
        "Monitiring":1,
        "RemoteDeploy":1,
        "RemoteManagment":1,
        "HelpMarketing":1,
        "AuditLog":1,
        "PSA":1,
        "Administrators":1,
        "Rebranding":1,
        "Storage":1,
        "ADS":1,
        "LicenseBuy":1,
        "LicenseActivate":1,
        "StorageUsage":1,
        "CapacityReport":1,
        "GoogleApps":1,
        "Dashboard":1
    }
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<AdministratorsNewModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <Companies xmlns:d2p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
    <d2p1:string>sample string 1</d2p1:string>
    <d2p1:string>sample string 2</d2p1:string>
  </Companies>
  <Email>sample string 1</Email>
  <Enabled>true</Enabled>
  <FirstName>sample string 4</FirstName>
  <InitialPassword>sample string 2</InitialPassword>
  <LastName>sample string 5</LastName>
  <PermissionsModels>
    <ADS>None</ADS>
    <Administrators>None</Administrators>
    <AuditLog>None</AuditLog>
    <Billing>None</Billing>
    <CapacityReport>None</CapacityReport>
    <Dashboard>None</Dashboard>
    <GoogleApps>None</GoogleApps>
    <HelpMarketing>None</HelpMarketing>
    <LicenseActivate>None</LicenseActivate>
    <LicenseBuy>None</LicenseBuy>
    <Licenses>None</Licenses>
    <Monitiring>None</Monitiring>
    <Notification>None</Notification>
    <OnlineAccess>None</OnlineAccess>
    <PSA>None</PSA>
    <Rebranding>None</Rebranding>
    <RemoteDeploy>None</RemoteDeploy>
    <RemoteManagment>None</RemoteManagment>
    <Storage>None</Storage>
    <StorageLimit>None</StorageLimit>
    <StorageUsage>None</StorageUsage>
    <Users>None</Users>
  </PermissionsModels>
  <SendInstruction>true</SendInstruction>
</AdministratorsNewModels>
```
{% endtab %}
{% endtabs %}

## Response Information

ID of the newly created administrator.

## Sample Python Code

```python
import requests
def createNewAdministrator(token, newAdmin):
        createNewAdministratorRequest = requests.post('https://api.mspbackups.com/api/Administrators/', headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token}, json = newAdmin)

        if createNewAdministratorRequest.status_code == 200:
            print('200')
            return createNewAdministratorRequest.json()
        else:
            return createNewAdministratorRequest.status_code

newAdmin = {
    "Email" : "user@me.com",
    "InitialPassword" : "truepass",
    "SendInstruction" : "true",
    "FirstName" : "Robert",
    "LastName" : "QA",
    "Enabled" : "true",
    "PermissionsModels": {
        "Users": 1,
        "StorageLimit": 1,
        "Notification": 0,
        "OnlineAccess": 1,
        "Licenses": 1,
        "Billing":1,
        "Monitiring":1,
        "RemoteDeploy":1,
        "RemoteManagment":1,
        "HelpMarketing":1,
        "AuditLog":1,
        "PSA":1,
        "Administrators":1,
        "Rebranding":1,
        "Storage":1,
        "ADS":1,
        "LicenseBuy":1,
        "LicenseActivate":1,
        "StorageUsage":1,
        "CapacityReport":1,
        "GoogleApps":1,
        "Dashboard":1
    }
}

createNewAdministrator("MBSAPItoken", newAdmin)
```

