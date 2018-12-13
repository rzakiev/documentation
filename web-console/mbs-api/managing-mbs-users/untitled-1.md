# Delete a User's Data in Backup Storage

{% api-method method="delete" host="https://api.mspbackups.com" path="/api/Users/{userID}/Computers" %}
{% api-method-summary %}
Delete User Data in Backup Storage
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to delete a user's data in the backup storage. Use this request if you don't want to delete the user from MBS or if you've already deleted them. The data will be purged from the backup storage within 24 hours.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="userID" type="string" required=true %}
ID of the MBS user whose data is to be deleted.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="ComputerName" type="string" required=true %}
Name of the computer on which the data was backed up
{% endapi-method-parameter %}

{% api-method-parameter name="DestinationId" type="string" required=true %}
Destination ID
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The user's data has been successfully deleted.
{% endapi-method-response-example-description %}

```text
No message is returned
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Request Format

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
[  {    "DestinationId": "b17266e7-8b8e-4c3f-b1bb-911b9sdf",    "ComputerName": "Charlie Marketing MacBook"  },  {    "DestinationId": "b17266e7-8b8e-4c3f-b1bb-911b9e8sdf",    "ComputerName": "Jane sales Acer"  }]
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<ArrayOfUserComputerData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">  <UserComputerData>    <ComputerName>sample string 2</ComputerName>    <DestinationId>b17266e7-8b8e-4c3f-b1bb-911b9e89f90e</DestinationId>  </UserComputerData>  <UserComputerData>    <ComputerName>sample string 2</ComputerName>    <DestinationId>b17266e7-8b8e-4c3f-b1bb-911b9e89f90e</DestinationId>  </UserComputerData></ArrayOfUserComputerData>
```
{% endtab %}
{% endtabs %}

## Response Information

None.

## Sample Python Code

```python
import requests 

def deleteUsersData (token, userID, json):
        deleteUsersDataRequest = requests.delete('https://api.mspbackups.com/api/Users/' + userID + '/Computers', headers = {"Authorization": "Bearer " + token}, json = json)
        print ("Delete user's data request status code: " + str(deleteUsersDataRequest.status_code) + "\n")
        return deleteUsersDataRequest.status_code

usersInfo = {
        "DestinationId" : "someID"
        "ComputerName" : "MBSuserComputerName"
}
deletedUsersData("MBSAPItoken", "MBSuserID", usersInfo)
```

{% hint style="info" %}
You can request the destination ID and computer names by sending the _GET api/Users/{userid}/Computers_ request described on the last page of this section.
{% endhint %}

