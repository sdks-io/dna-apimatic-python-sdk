
# Auth Token Response

*This model accepts additional fields of type Any.*

## Structure

`AuthTokenResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `access_token` | `str` | Optional | Access token to be used in subsequent API calls. |
| `expires_in` | `int` | Optional | Number of seconds until the access_token expires. |
| `refresh_token` | `str` | Optional | Reserved for future use. |
| `scope` | `str` | Optional | - |
| `token_type` | [`TokenType`](../../doc/models/token-type.md) | Optional | - |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from dnapaymentspartnerreportingsettlementapis.models.auth_token_response import AuthTokenResponse
from dnapaymentspartnerreportingsettlementapis.models.token_type import TokenType

auth_token_response = AuthTokenResponse(
    access_token='access_token6',
    expires_in=204,
    refresh_token='refresh_token8',
    scope='partners_reporting',
    token_type=TokenType.BEARER,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

