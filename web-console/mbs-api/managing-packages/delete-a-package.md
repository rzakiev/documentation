# Delete a Package

{% api-method method="delete" host="https://api.mspbackups.com" path="/api/Packages/{id}" %}
{% api-method-summary %}
Delete Package
{% endapi-method-summary %}

{% api-method-description %}
This endpoint enables you to delete an MBS package.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
MBS package ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Specifies the authorization type and token. Possible value: "Bearer \*token\*"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The package has been successfully deleted!
{% endapi-method-response-example-description %}

```text
No message is returned!
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response Information

None.

## Sample Python Code

```python
import requests

def deletePackage(token, packageID):
        deletePackageRequest = requests.delete('https://api.mspbackups.com/api/Packages/' + packageID, headers = { "Authorization": "Bearer " + token})

        if deletePackageRequest.status_code == 200:
            print('The package has been successfully deleted!')
        else:
            print('Error: ' + deletePackageRequest.status_code)
            return deletePackageRequest.status_code

deletePackage("MBSAPItoken", "packageID")
```

