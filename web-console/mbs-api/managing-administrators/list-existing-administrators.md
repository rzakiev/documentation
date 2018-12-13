# List Existing Administrators

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Administrators" %}
{% api-method-summary %}
List Existing Administrators
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to list existing administrators.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
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
The list of administrators has been successfully received
{% endapi-method-response-example-description %}

```text
[{'AdminID': 'sample-1656-40b4-bc64-f4299a8303fc', 'Email': 'testuser', 'FirstName': 'Main', 'LastName': 'Administrator', 'Enabled': True, 'PermissionsModels': {'Users': 1, 'StorageLimit': 0, 'Notification': 1, 'OnlineAccess': 0, 'Licenses': 1, 'Billing': 1, 'Monitiring': 0, 'RemoteDeploy': 0, 'RemoteManagment': 0, 'HelpMarketing': 0, 'AuditLog': 0, 'PSA': 0, 'Administrators': 0, 'Rebranding': 0, 'Storage': 0, 'ADS': 0, 'LicenseBuy': 0, 'LicenseActivate': 0, 'StorageUsage': 1, 'CapacityReport': 1, 'GoogleApps': 0, 'Dashboard': 0}, 'LastLogin': None, 'DateCreated': '2018-05-15T15:44:51.07', 'Companies': []}]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| AdminID | ID of the administrator | String |
| Email | Administrator's email | String |
| FirstName | First name | String |
| LastName | Last name | String |
| Enabled | Indicates if the administrator is enabled or disabled | Bool |
| PermissionsModels | Administrator's permissions | PermissionsModels |
| LastLogin | Date of the last login | Date |
| DateCreated | Date when the administrator was created | Date |
| Companies | Companies to which the administrator is assigned | Collection of String |

* _PermissionModels_ parameters:

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

## Response Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
[
  {
    "AdminID": "someIDe-7aac-4177-a5a5-ebcee77ee97e",
    "Email": "sample string 2",
    "FirstName": "sample string 3",
    "LastName": "sample string 4",
    "Enabled": true,
    "PermissionsModels": {
      "Users": 0,
      "StorageLimit": 0,
      "Notification": 0,
      "OnlineAccess": 0,
      "Licenses": 0,
      "Billing": 0,
      "Monitiring": 0,
      "RemoteDeploy": 0,
      "RemoteManagment": 0,
      "HelpMarketing": 0,
      "AuditLog": 0,
      "PSA": 0,
      "Administrators": 0,
      "Rebranding": 0,
      "Storage": 0,
      "ADS": 0,
      "LicenseBuy": 0,
      "LicenseActivate": 0,
      "StorageUsage": 0,
      "CapacityReport": 0,
      "GoogleApps": 0,
      "Dashboard": 0
    },
    "LastLogin": "2018-05-15T14:08:30.8589271+00:00",
    "DateCreated": "2018-05-15T14:08:30.8589271+00:00",
    "Companies": [
      "sample string 1",
      "sample string 2"
    ]
  },
  {
    "AdminID": "773eb9de-7aac-4177-a5a5-ebcee77ee97e",
    "Email": "sample string 2",
    "FirstName": "sample string 3",
    "LastName": "sample string 4",
    "Enabled": true,
    "PermissionsModels": {
      "Users": 0,
      "StorageLimit": 0,
      "Notification": 0,
      "OnlineAccess": 0,
      "Licenses": 0,
      "Billing": 0,
      "Monitiring": 0,
      "RemoteDeploy": 0,
      "RemoteManagment": 0,
      "HelpMarketing": 0,
      "AuditLog": 0,
      "PSA": 0,
      "Administrators": 0,
      "Rebranding": 0,
      "Storage": 0,
      "ADS": 0,
      "LicenseBuy": 0,
      "LicenseActivate": 0,
      "StorageUsage": 0,
      "CapacityReport": 0,
      "GoogleApps": 0,
      "Dashboard": 0
    },
    "LastLogin": "2018-05-15T14:08:30.8589271+00:00",
    "DateCreated": "2018-05-15T14:08:30.8589271+00:00",
    "Companies": [
      "sample string 1",
      "sample string 2"
    ]
  }
]
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
<ArrayOfAdministratorsModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <AdministratorsModels>
    <AdminID>someID-a5a5-ebcee77ee97e</AdminID>
    <Companies xmlns:d3p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
      <d3p1:string>sample string 1</d3p1:string>
      <d3p1:string>sample string 2</d3p1:string>
    </Companies>
    <DateCreated>2018-05-15T14:08:30.8589271+00:00</DateCreated>
    <Email>sample string 2</Email>
    <Enabled>true</Enabled>
    <FirstName>sample string 3</FirstName>
    <LastLogin>2018-05-15T14:08:30.8589271+00:00</LastLogin>
    <LastName>sample string 4</LastName>
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
  </AdministratorsModels>
  <AdministratorsModels>
    <AdminID>773eb9de-7aac-4177-a5a5-ebcee77ee97e</AdminID>
    <Companies xmlns:d3p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
      <d3p1:string>sample string 1</d3p1:string>
      <d3p1:string>sample string 2</d3p1:string>
    </Companies>
    <DateCreated>2018-05-15T14:08:30.8589271+00:00</DateCreated>
    <Email>sample string 2</Email>
    <Enabled>true</Enabled>
    <FirstName>sample string 3</FirstName>
    <LastLogin>2018-05-15T14:08:30.8589271+00:00</LastLogin>
    <LastName>sample string 4</LastName>
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
  </AdministratorsModels>
</ArrayOfAdministratorsModels>
```
{% endtab %}
{% endtabs %}

## Sample Python Code

```python
import requests
def listAdministrators(token):
        listAdministratorsRequest = requests.get('https://api.mspbackups.com/api/Administrators', headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token})
        if listAdministratorsRequest.status_code == 200:
            print('200')
            return listAdministratorsRequest.json()
        else:
            return listAdministratorsRequest.status_code

listAdministrators("MBSAPItoken")
```

