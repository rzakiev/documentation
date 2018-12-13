# Get Account Information

{% api-method method="get" host="https://api.mspbackups.com" path="/api/Accounts/{id}" %}
{% api-method-summary %}
Get Account Information
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to receive information on a particular account.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Account ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

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
The account information has been successfully received
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
| StorageType | Storage Type | String |
| Destinations | List of destinations | Collection |

## Response Formats

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
{
  "AccountID": "sample string 1",
  "DateCreated": "2018-05-14T14:10:41.1918293+00:00",
  "DisplayName": "sample string 3",
  "StorageType": "sample string 4",
  "Destinations": [
    {
      "AccountID": "8f34e9b8-1e38-4780-b75f-37c9dc7b795f",
      "Destination": "sample string 2",
      "DestinationDisplayName": "sample string 3"
    },
    {
      "AccountID": "8f34e9b8-1e38-4780-b75f-37c9dc7b795f",
      "Destination": "sample string 2",
      "DestinationDisplayName": "sample string 3"
    }
  ]
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<AccountsModels xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <AccountID>sample string 1</AccountID>
  <DateCreated>2018-05-14T14:10:41.1918293+00:00</DateCreated>
  <Destinations>
    <DestinationOfAccount>
      <AccountID>8f34e9b8-1e38-4780-b75f-37c9dc7b795f</AccountID>
      <Destination>sample string 2</Destination>
      <DestinationDisplayName>sample string 3</DestinationDisplayName>
    </DestinationOfAccount>
    <DestinationOfAccount>
      <AccountID>8f34e9b8-1e38-4780-b75f-37c9dc7b795f</AccountID>
      <Destination>sample string 2</Destination>
      <DestinationDisplayName>sample string 3</DestinationDisplayName>
    </DestinationOfAccount>
  </Destinations>
  <DisplayName>sample string 3</DisplayName>
  <StorageType>sample string 4</StorageType>
</AccountsModels>
```
{% endtab %}
{% endtabs %}

## Sample Python Code

```python
import requests
def getAccountInfo(token, accountID):
        getAccountInfoRequest = requests.get('https://api.mspbackups.com/api/Accounts/' + accountID, headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token})

        if getAccountInfoRequest.status_code == 200:
            print('200')
            return getAccountInfoRequest.json()
        else:
            print('Error: ' +str(getAccountInfoRequest.status_code))
            return getAccountInfoRequest.status_code

getAccountInfo("MBStoken", "accountID")
```

