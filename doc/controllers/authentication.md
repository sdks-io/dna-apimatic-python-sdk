# Authentication

Obtain access tokens required for all other API calls.

```python
authentication_api = client.authentication
```

## Class Name

`AuthenticationApi`


# Get Access Token

Prior to querying any Reporting or Settlement API endpoint, an access token must be obtained. This endpoint is shared by both the Reporting API and the Settlement API (both use the `partners_reporting` scope).

:information_source: **Note** This endpoint does not require authentication.

```python
def get_access_token(self,
                    grant_type,
                    scope,
                    client_id,
                    client_secret)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `grant_type` | [`GrantType`](../../doc/models/grant-type.md) | Form, Required | Authorisation type required to confirm the action required. |
| `scope` | [`Scope`](../../doc/models/scope.md) | Form, Required | Scope of the action to be performed with the credentials. |
| `client_id` | `str` | Form, Required | Provided to the integrator following successful creation of a test account. |
| `client_secret` | `str` | Form, Required | Provided to the integrator following successful creation of a test account. |

## Response Type

**200**: Access token successfully issued.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`AuthTokenResponse`](../../doc/models/auth-token-response.md).

## Example Usage

```python
grant_type = GrantType.CLIENT_CREDENTIALS

scope = Scope.PARTNERS_REPORTING

client_id = 'client_id8'

client_secret = 'client_secret8'

result = authentication_api.get_access_token(
    grant_type,
    scope,
    client_id,
    client_secret
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Example Response *(as JSON)*

```json
{
  "access_token": "D*OAeMXErWmCSWcZYsyJf0cRZlC5C$hCR2dEGJp7.2q1W*z_iSC9sa3JGLtAR3ZG",
  "expires_in": 7200,
  "refresh_token": "!NnycppKptqQE_w6!0oul!=bCEXlu=JX*7yW!h.xpuHJvs9ums9lPJ1FpUfmSfH7",
  "scope": "partners_reporting",
  "token_type": "Bearer"
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request — request format is invalid. | [`ErrorException`](../../doc/models/error-exception.md) |
| 401 | Unauthorized — invalid authentication credentials have been supplied. | [`ErrorException`](../../doc/models/error-exception.md) |

