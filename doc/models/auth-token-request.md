
# Auth Token Request

*This model accepts additional fields of type Any.*

## Structure

`AuthTokenRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `grant_type` | `str` | Required, Constant | Authorisation type required to confirm the action required.<br><br>**Value**: `"client_credentials"` |
| `scope` | `str` | Required, Constant | Scope of the action to be performed with the credentials.<br><br>**Value**: `"partners_reporting"` |
| `client_id` | `str` | Required | Provided to the integrator following successful creation of a test account. |
| `client_secret` | `str` | Required | Provided to the integrator following successful creation of a test account. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from dnapaymentspartnerreportingsettlementapis.models.auth_token_request import AuthTokenRequest

auth_token_request = AuthTokenRequest(
    client_id='client_id4',
    client_secret='client_secret0',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

