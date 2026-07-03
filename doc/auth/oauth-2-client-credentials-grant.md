
# OAuth 2 Client Credentials Grant



Documentation for accessing and setting credentials for BearerAuth.

## Auth Credentials

| Name | Type | Description | Getter |
|  --- | --- | --- | --- |
| OAuthClientId | `str` | OAuth 2 Client ID | `oauth_client_id` |
| OAuthClientSecret | `str` | OAuth 2 Client Secret | `oauth_client_secret` |
| OAuthToken | `OauthToken` | Object for storing information about the OAuth token | `oauth_token` |
| OAuthScopes | `List[OauthScope]` | List of scopes that apply to the OAuth token | `oauth_scopes` |
| OAuthTokenProvider | `Callable[[OAuthToken, OAuth2], OAuthToken]` | Registers a callback for oAuth Token Provider used for automatic token fetching/refreshing. | `oauth_token_provider` |
| OAuthOnTokenUpdate | `Callable[[OAuthToken], None]` | Registers a callback for token update event. | `oauth_on_token_update` |
| OAuthClockSkew | `int` | Clock skew time in seconds applied while checking the OAuth Token expiry. | `oauth_clock_skew` |



**Note:** Auth credentials can be set using `ClientCredentialsAuthCredentials` object, passed in as named parameter `client_credentials_auth_credentials` in the client initialization.

## Usage Example

### Client Initialization

You must initialize the client with *OAuth 2.0 Client Credentials Grant* credentials as shown in the following code snippet. This will fetch the OAuth token automatically when any of the endpoints, requiring *OAuth 2.0 Client Credentials Grant* authentication, are called.

```python
from dnapaymentspartnerreportingsettlementapis.dnapaymentspartnerreportingsettlementapis_client import DnapaymentspartnerreportingsettlementapisClient
from dnapaymentspartnerreportingsettlementapis.http.auth.oauth_2 import ClientCredentialsAuthCredentials
from dnapaymentspartnerreportingsettlementapis.models.oauth_scope import OauthScope

client = DnapaymentspartnerreportingsettlementapisClient(
    client_credentials_auth_credentials=ClientCredentialsAuthCredentials(
        oauth_client_id='OAuthClientId',
        oauth_client_secret='OAuthClientSecret',
        oauth_scopes=[
            OauthScope.PARTNERS_REPORTING
        ]
    )
)
```



Your application can also manually provide an OAuthToken using the setter `oauth_token` in `ClientCredentialsAuthCredentials` object. This function takes in an instance of OAuthToken containing information for authorizing client requests and refreshing the token itself.

You must have initialized the client with scopes for which you need permission to access.

### Scopes

Scopes enable your application to only request access to the resources it needs while enabling users to control the amount of access they grant to your application. Available scopes are defined in the [`OauthScope`](../../doc/models/oauth-scope.md) enumeration.

| Scope Name | Description |
|  --- | --- |
| `PARTNERS_REPORTING` | Access to the Partner Reporting and Settlement APIs. |

### Adding OAuth Token Update Callback

Whenever the OAuth Token gets updated, the provided callback implementation will be executed. For instance, you may use it to store your access token whenever it gets updated.

```python
from dnapaymentspartnerreportingsettlementapis.dnapaymentspartnerreportingsettlementapis_client import DnapaymentspartnerreportingsettlementapisClient
from dnapaymentspartnerreportingsettlementapis.http.auth.oauth_2 import ClientCredentialsAuthCredentials
from dnapaymentspartnerreportingsettlementapis.models.oauth_scope import OauthScope

client = DnapaymentspartnerreportingsettlementapisClient(
    client_credentials_auth_credentials=ClientCredentialsAuthCredentials(
        oauth_client_id='OAuthClientId',
        oauth_client_secret='OAuthClientSecret',
        oauth_scopes=[
            OauthScope.PARTNERS_REPORTING
        ],
        oauth_on_token_update=(lambda oauth_token:
                                # Add the callback handler to perform operations like save to DB or file etc.
                                # It will be triggered whenever the token gets updated
                                save_token_to_database(oauth_token))
    )
)
```

### Adding Custom OAuth Token Provider

To authorize a client using a stored access token, set up the `oauth_token_provider` in `ClientCredentialsAuthCredentials` along with the other auth parameters before creating the client:

```python
from dnapaymentspartnerreportingsettlementapis.dnapaymentspartnerreportingsettlementapis_client import DnapaymentspartnerreportingsettlementapisClient
from dnapaymentspartnerreportingsettlementapis.http.auth.oauth_2 import ClientCredentialsAuthCredentials
from dnapaymentspartnerreportingsettlementapis.models.oauth_scope import OauthScope

def _oauth_token_provider(last_oauth_token, auth_manager):
    # Add the callback handler to provide a new OAuth token
    # It will be triggered whenever the last provided o_auth_token is null or expired
    oauth_token = load_token_from_database()
    if oauth_token is None:
        oauth_token = auth_manager.fetch_token()
    return oauth_token


client = DnapaymentspartnerreportingsettlementapisClient(
    client_credentials_auth_credentials=ClientCredentialsAuthCredentials(
        oauth_client_id='OAuthClientId',
        oauth_client_secret='OAuthClientSecret',
        oauth_scopes=[
            OauthScope.PARTNERS_REPORTING
        ],
        oauth_token_provider=_oauth_token_provider
    )
)
```


