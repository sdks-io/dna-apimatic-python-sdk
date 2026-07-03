
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](../README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| http_client_instance | `Union[Session, HttpClientProvider]` | The Http Client passed from the sdk user for making requests |
| override_http_client_configuration | `bool` | The value which determines to override properties of the passed Http Client from the sdk user |
| http_call_back | `HttpCallBack` | The callback value that is invoked before and after an HTTP call is made to an endpoint |
| timeout | `float` | The value to use for connection timeout. <br> **Default: 30** |
| max_retries | `int` | The number of times to retry an endpoint call if it fails. <br> **Default: 0** |
| backoff_factor | `float` | A backoff factor to apply between attempts after the second try. <br> **Default: 2** |
| retry_statuses | `Array of int` | The http statuses on which retry is to be done. <br> **Default: [408, 413, 429, 500, 502, 503, 504, 521, 522, 524]** |
| retry_methods | `Array of string` | The http methods on which retry is to be done. <br> **Default: ["GET", "PUT"]** |
| proxy_settings | [`ProxySettings`](../doc/proxy-settings.md) | Optional proxy configuration to route HTTP requests through a proxy server. |
| logging_configuration | [`LoggingConfiguration`](../doc/logging-configuration.md) | The SDK logging configuration for API calls |
| client_credentials_auth_credentials | [`ClientCredentialsAuthCredentials`](auth/oauth-2-client-credentials-grant.md) | The credential object for OAuth 2 Client Credentials Grant |

The API client can be initialized as follows:

## Code-Based Client Initialization

```python
import logging

from dnapaymentspartnerreportingsettlementapis.configuration import Environment
from dnapaymentspartnerreportingsettlementapis.dnapaymentspartnerreportingsettlementapis_client import DnapaymentspartnerreportingsettlementapisClient
from dnapaymentspartnerreportingsettlementapis.http.auth.oauth_2 import ClientCredentialsAuthCredentials
from dnapaymentspartnerreportingsettlementapis.logging.configuration.api_logging_configuration import LoggingConfiguration
from dnapaymentspartnerreportingsettlementapis.logging.configuration.api_logging_configuration import RequestLoggingConfiguration
from dnapaymentspartnerreportingsettlementapis.logging.configuration.api_logging_configuration import ResponseLoggingConfiguration
from dnapaymentspartnerreportingsettlementapis.models.oauth_scope import OauthScope

client = DnapaymentspartnerreportingsettlementapisClient(
    client_credentials_auth_credentials=ClientCredentialsAuthCredentials(
        oauth_client_id='OAuthClientId',
        oauth_client_secret='OAuthClientSecret',
        oauth_scopes=[
            OauthScope.PARTNERS_REPORTING
        ]
    ),
    environment=Environment.PRODUCTION,
    logging_configuration=LoggingConfiguration(
        log_level=logging.INFO,
        request_logging_config=RequestLoggingConfiguration(
            log_body=True
        ),
        response_logging_config=ResponseLoggingConfiguration(
            log_headers=True
        )
    )
)
```

## Environment-Based Client Initialization

```python
from dnapaymentspartnerreportingsettlementapis.dnapaymentspartnerreportingsettlementapis_client import DnapaymentspartnerreportingsettlementapisClient

# Specify the path to your .env file if it’s located outside the project’s root directory.
client = DnapaymentspartnerreportingsettlementapisClient.from_environment(dotenv_path='/path/to/.env')
```

See the [Environment-Based Client Initialization](../doc/environment-based-client-initialization.md) section for details.

## DNA Payments Partner Reporting & Settlement APIs Client

The gateway for the SDK. This class acts as a factory for the Apis and also holds the configuration of the SDK.

## Apis

| Name | Description |
|  --- | --- |
| authentication | Gets AuthenticationApi |
| merchants | Gets MerchantsApi |
| ecommerce_transactions | Gets EcommerceTransactionsApi |
| pos_transactions | Gets PosTransactionsApi |
| settlements | Gets SettlementsApi |
| oauth_authorization | Gets OauthAuthorizationApi |

