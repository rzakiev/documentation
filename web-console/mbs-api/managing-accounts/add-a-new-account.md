# Add a New Account

{% api-method method="post" host="https://api.mspbackups.com" path="/api/Accounts" %}
{% api-method-summary %}
Add New Account
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to add a new account.
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
The account has been successfully added.
{% endapi-method-response-example-description %}

```text
No message is returned
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Request Information

| Parameter | Description | Value |
| :--- | :--- | :--- |
| DisplayName | — | String |
| Type | Account type | AccountType |
| AccountSettings | Storage-specific settings | _Settings_ |

* _AccountType_ parameters:

| Name | Value |
| :--- | :--- |
| Amazon S3 | 0 |
| AmazonS3China | 1 |
| Azure | 2 |
| OpenStack | 3 |
| OracleCloud | 4 |
| S3Compatible | 5 |
| Scality | 6 |
| CenturyLink | 7 |
| ArubaCloud | 8 |
| BackBlaze B2 | 9 |
| Cloudian | 10 |
| Connectria | 11 |
| Constant | 12 |
| DreamObjects | 13 |
| Dunkel | 14 |
| GreenQloud | 15 |
| HostEurope | 16 |
| Seeweb | 17 |
| ThinkOn | 18 |
| Tiscali | 19 |
| Walrus | 20 |

* Settings \_\_parameters:

| Name | Description | Type |
| :--- | :--- | :--- |
| AmazonS3 | Parameters required to add an S3 storage | AmazonS3Settings |
| Azure | Parameters required to add an Azure storage | AzureSettings |
| OpenStack | Parameters required to add an S3 | OpenStackSettings |
| Oracle | Parameters required to add an Oracle | OpenStackCompatible |
| S3Compatible | Parameters required to add an S3-compatible storage | S3CompatibleSettings |
| Cloudian | Parameters required to add a Cloudian account | CloudianSettings |

* AmazonS3Settings parameters:

| Name | Description | Type |
| :--- | :--- | :--- |
| AccessKey | S3 Access key | String |
| SecretKey | S3 Secret key | String |
| IsGovCloud | Indicates if the account is a government account | Bool |

* S3CompatibleSettings parameters:

| Name | Description | Type |
| :--- | :--- | :--- |
| AccessKey | S3 Access Key | String |
| SecretKey | S3 Secret key | String |
| IsGovCloud | Indicates if the account is a government account | Bool |
| UseNativeMultipartUpload | Required for Aruba Cloud, BackBlaze B2, Connectria, Constant, DreamObjects, Dunkel, GreenQloud, HostEurope, Seeweb, ThinkOn, Tiscali, and Walrus. | Bool |
| HTTPEndpoint | HTTP endpoint | String |
| HTTPSEndpoint | HTTPS endpoint | String |
| IgnoreCertificate | — | Bool |
| NotCheckCredentials | Used if there's no public access | Bool |
| SignatureVersion | Required for S3-compatible accounts | Version2, Version4 |

* AzureSettings parameters:

| Name | Description | Type |
| :--- | :--- | :--- |
| AccountName | Account name | String |
| SharedKey | Shared key | String |

* OpenStackSettings parameters:

| Name | Description | Type |
| :--- | :--- | :--- |
| IgnoreCertificate | — | Bool |
| NotCheckCredentials | Used if there's no public access | Bool |
| UserName | — | String |
| ApiKey | — | String |
| AuthService | Authentication service | String |
| KeyStoneVersion | — | DoNotUse, Two \(v2\), Three \(v3\) |
| TenantType | — | {"Name": "value", "ID" : "value"} |
| Tenant | Tenant | String |
| UserInternalURLs | Indicates if internal URLs should be used | Bool |
| DomainType | Required for Key Stone v3 | {"Name": "value", "ID" : "value"} |
| Domain | Required for Key Stone v3 | String |
| UseScope | Required for Key Stone v3 | Bool |
| ProjectType | Required if UseScope is true and Key Stone v3 is used | {"Name":"value", "ID":"value"} |
| Project | Required if UseScope is true and Key Stone v3 is used | String |

* OpenStackCompatible parameters:

| Name | Description | Type |
| :--- | :--- | :--- |
| UserName | — | String |
| ApiKey | — | String |
| AuthService | Authentication service | String |
| KeyStoneVersion | — | DoNotUse, Two \(v2\), Three \(v3\) |
| TenantType | — | {"Name": "value", "ID" : "value"} |
| Tenant | Tenant | String |
| UserInternalURLs | Indicates if internal URLs should be used | Bool |
| DomainType | Required for Key Stone v3 | {"Name": "value", "ID" : "value"} |
| Domain | Required for Key Stone v3 | String |
| UseScope | Required for Key Stone v3 | Bool |
| ProjectType | Required if UseScope is true and Key Stone v3 is used | {"Name":"value", "ID":"value"} |
| Project | Required if UseScope is true and Key Stone v3 is used | String |

* CloudianSettings parameters:

| Name | Description | Value |
| :--- | :--- | :--- |
| AccessKey | Access key | String |
| SecretKey | Secret key | String |
| IsGovCloud | Indicates if the account is a government account | Bool |
| UserNativeMultipartUpload | Required for Aruba Cloud, BackBlaze B2, Connectria, Constant, DreamObjects, Dunkel, GreenQloud, HostEurope, Seeweb, ThinkOn, Tiscali, and Walrus. | Bool |
| HTTPEndpoint | HTTP endpoint | String |
| HTTPSEndpoint | HTTPS endpoint | String |
| IgnoreCertificate | — | Bool |
| NotCheckCredentials | Used if there's no public access | Bool |
| SignatureVersion | Signature version | Version2, Version4 |

## Request Format

{% tabs %}
{% tab title="JSON" %}
* application/json, text/json

```javascript
Sample:
{
  "DisplayName": "sample string 1",
  "Type": 0,
  "AccountSettings": {
    "AmazonS3": {
      "AccessKey": "sample string 1",
      "SecretKey": "sample string 2",
      "IsGovCloud": true
    },
    "Azure": {
      "AccountName": "sample string 1",
      "SharedKey": "sample string 2"
    },
    "OpenStack": {
      "IgnoreCertificate": true,
      "NotCheckCredentials": true,
      "UserName": "sample string 3",
      "ApiKey": "sample string 4",
      "AuthService": "sample string 5",
      "KeyStoneVersion": 0,
      "TenantType": 0,
      "Tenant": "sample string 6",
      "UseInternalURLs": true,
      "DomainType": 0,
      "Domain": "sample string 8",
      "UseScope": true,
      "ProjectType": 0,
      "Project": "sample string 10"
    },
    "Oracle": {
      "UserName": "sample string 1",
      "ApiKey": "sample string 2",
      "AuthService": "sample string 3",
      "KeyStoneVersion": 0,
      "TenantType": 0,
      "Tenant": "sample string 4",
      "UseInternalURLs": true,
      "DomainType": 0,
      "Domain": "sample string 6",
      "UseScope": true,
      "ProjectType": 0,
      "Project": "sample string 8"
    },
    "S3Compatible": {
      "UseNativeMultipartUpload": true,
      "HTTPEnpoint": "sample string 2",
      "HTTPSEndpoint": "sample string 3",
      "IgnoreCertificate": true,
      "NotCheckCredentials": true,
      "SignatureVersion": 2,
      "AccessKey": "sample string 6",
      "SecretKey": "sample string 7",
      "IsGovCloud": true
    },
    "Cloudian": {
      "UseNativeMultipartUpload": true,
      "HTTPEnpoint": "sample string 2",
      "HTTPSEndpoint": "sample string 3",
      "IgnoreCertificate": true,
      "NotCheckCredentials": true,
      "SignatureVersion": 2,
      "AccessKey": "sample string 6",
      "SecretKey": "sample string 7",
      "IsGovCloud": true
    }
  }
}
```
{% endtab %}

{% tab title="XML" %}
* application/xml, text/xml

```markup
Sample:
<Account xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/MBSAPImvc.Engine.Models">
  <AccountSettings>
    <AmazonS3>
      <AccessKey>sample string 1</AccessKey>
      <IsGovCloud>true</IsGovCloud>
      <SecretKey>sample string 2</SecretKey>
    </AmazonS3>
    <Azure>
      <AccountName>sample string 1</AccountName>
      <SharedKey>sample string 2</SharedKey>
    </Azure>
    <Cloudian>
      <AccessKey>sample string 6</AccessKey>
      <IsGovCloud>true</IsGovCloud>
      <SecretKey>sample string 7</SecretKey>
      <HTTPEnpoint>sample string 2</HTTPEnpoint>
      <HTTPSEndpoint>sample string 3</HTTPSEndpoint>
      <IgnoreCertificate>true</IgnoreCertificate>
      <NotCheckCredentials>true</NotCheckCredentials>
      <SignatureVersion>Version2</SignatureVersion>
      <UseNativeMultipartUpload>true</UseNativeMultipartUpload>
    </Cloudian>
    <OpenStack>
      <ApiKey>sample string 4</ApiKey>
      <AuthService>sample string 5</AuthService>
      <Domain>sample string 8</Domain>
      <DomainType>Name</DomainType>
      <KeyStoneVersion>DoNotUse</KeyStoneVersion>
      <Project>sample string 10</Project>
      <ProjectType>Name</ProjectType>
      <Tenant>sample string 6</Tenant>
      <TenantType>Name</TenantType>
      <UseInternalURLs>true</UseInternalURLs>
      <UseScope>true</UseScope>
      <UserName>sample string 3</UserName>
      <IgnoreCertificate>true</IgnoreCertificate>
      <NotCheckCredentials>true</NotCheckCredentials>
    </OpenStack>
    <Oracle>
      <ApiKey>sample string 2</ApiKey>
      <AuthService>sample string 3</AuthService>
      <Domain>sample string 6</Domain>
      <DomainType>Name</DomainType>
      <KeyStoneVersion>DoNotUse</KeyStoneVersion>
      <Project>sample string 8</Project>
      <ProjectType>Name</ProjectType>
      <Tenant>sample string 4</Tenant>
      <TenantType>Name</TenantType>
      <UseInternalURLs>true</UseInternalURLs>
      <UseScope>true</UseScope>
      <UserName>sample string 1</UserName>
    </Oracle>
    <S3Compatible>
      <AccessKey>sample string 6</AccessKey>
      <IsGovCloud>true</IsGovCloud>
      <SecretKey>sample string 7</SecretKey>
      <HTTPEnpoint>sample string 2</HTTPEnpoint>
      <HTTPSEndpoint>sample string 3</HTTPSEndpoint>
      <IgnoreCertificate>true</IgnoreCertificate>
      <NotCheckCredentials>true</NotCheckCredentials>
      <SignatureVersion>Version2</SignatureVersion>
      <UseNativeMultipartUpload>true</UseNativeMultipartUpload>
    </S3Compatible>
  </AccountSettings>
  <DisplayName>sample string 1</DisplayName>
  <Type>AmazonS3</Type>
</Account>
```
{% endtab %}
{% endtabs %}

## Response Information

None if the request has been sent successfully. Otherwise, a JSON is returned containing the error message.

## Sample Python Code

```python
import requests
def addAccount(token, accountJSON):
        addAccountRequest = requests.post('https://api.mspbackups.com/api/Accounts', headers = {"Accept" : "application/json",
                                                   "Authorization": "Bearer " + token}, json = accountJSON)

        if addAccountRequest.status_code == 200:
            print('200')
            return addAccountRequest.json()
        else:
            print('Error: ' + str(addAccountRequest.status_code))
            print(addAccountRequest.json())
            return addAccountRequest.status_code

newAccount = {
    "DisplayName" : "My S3 account",
    "Type" : 0,
    "AccountSettings" : {
        "AmazonS3": {
            "AccessKey" : "sampleAIXPUW2UXRWQYYBYQ",
            "SecretKey" : "sampleunLB+sxKPaRsEEfQe8J6Y33huFOWcZ4T",
            "IsGovCloud" : False
        }
    }
}

addAccount(newAccounts)
```

