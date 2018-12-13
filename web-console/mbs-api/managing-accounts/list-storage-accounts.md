# List Storage Accounts

{% api-method method="get" host="https://api.mspbaackups.com" path="/api/Accounts" %}
{% api-method-summary %}
List Storage Accounts
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to get the list of all backup storage accounts in MBS
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
The list of accounts has been received
{% endapi-method-response-example-description %}

```text
[{'AccountID': 'someID-79a0-4a52-88ed-36da652f4254', 'DateCreated': '2017-01-16T14:34:23.427', 'DisplayName': 'Azure ', 'StorageType': 'AzureVM', 'Destinations': [{'AccountID': 'someID-79a0-4a52-88ed-36da652f4254', 'Destination': 'main', 'DestinationDisplayName': 'Azure '}]}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| AccountID | — | String |
| DateCreated | — | Date |
| DisplayName | — | String |
| StorageType |  | String |
| Destinations | List of destinations | Collection |

## Response Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
[
  {
    "AccountID": "sample string 1",
    "DateCreated": "2018-05-14T14:10:39.3637711+00:00",
    "DisplayName": "sample string 3",
    "StorageType": "sample string 4",
    "Destinations": [
      {
        "AccountID": "967b8014-652d-4972-9fb6-c499c33634cb",
        "Destination": "sample string 2",
        "DestinationDisplayName": "sample string 3"
      },
      {
        "AccountID": "967b8014-652d-4972-9fb6-c499c33634cb",
        "Destination": "sample string 2",
        "DestinationDisplayName": "sample string 3"
      }
    ]
  },
  {
    "AccountID": "sample string 1",
    "DateCreated": "2018-05-14T14:10:39.3637711+00:00",
    "DisplayName": "sample string 3",
    "StorageType": "sample string 4",
    "Destinations": [
      {
        "AccountID": "967b8014-652d-4972-9fb6-c499c33634cb",
        "Destination": "sample string 2",
        "DestinationDisplayName": "sample string 3"
      },
      {
        "AccountID": "967b8014-652d-4972-9fb6-c499c33634cb",
        "Destination": "sample string 2",
        "DestinationDisplayName": "sample string 3"
      }
    ]
  }
]
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<ArrayOfAccountsModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <AccountsModels>
    <AccountID>sample string 1</AccountID>
    <DateCreated>2018-05-14T14:10:39.3637711+00:00</DateCreated>
    <Destinations>
      <DestinationOfAccount>
        <AccountID>967b8014-652d-4972-9fb6-c499c33634cb</AccountID>
        <Destination>sample string 2</Destination>
        <DestinationDisplayName>sample string 3</DestinationDisplayName>
      </DestinationOfAccount>
      <DestinationOfAccount>
        <AccountID>967b8014-652d-4972-9fb6-c499c33634cb</AccountID>
        <Destination>sample string 2</Destination>
        <DestinationDisplayName>sample string 3</DestinationDisplayName>
      </DestinationOfAccount>
    </Destinations>
    <DisplayName>sample string 3</DisplayName>
    <StorageType>sample string 4</StorageType>
  </AccountsModels>
  <AccountsModels>
    <AccountID>sample string 1</AccountID>
    <DateCreated>2018-05-14T14:10:39.3637711+00:00</DateCreated>
    <Destinations>
      <DestinationOfAccount>
        <AccountID>967b8014-652d-4972-9fb6-c499c33634cb</AccountID>
        <Destination>sample string 2</Destination>
        <DestinationDisplayName>sample string 3</DestinationDisplayName>
      </DestinationOfAccount>
      <DestinationOfAccount>
        <AccountID>967b8014-652d-4972-9fb6-c499c33634cb</AccountID>
        <Destination>sample string 2</Destination>
        <DestinationDisplayName>sample string 3</DestinationDisplayName>
      </DestinationOfAccount>
    </Destinations>
    <DisplayName>sample string 3</DisplayName>
    <StorageType>sample string 4</StorageType>
  </AccountsModels>
</ArrayOfAccountsModels>
```
{% endtab %}
{% endtabs %}

## Sample Python Code

```python
import requests
def getAccounts(token):
        getAccountsRequest = requests.get('https://api.mspbackups.com/api/Accounts', headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token})

        if getAccountsRequest.status_code == 200:
            print('200')
            return getAccountsRequest.json()
        else:
            print("Error: " + str(getAccountsRequest.status_code))
            return getAccountsRequest.status_code

getAccounts(MBSAPItoken)
```

