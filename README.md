
# Getting Started with DNA Payments Partner Reporting & Settlement APIs

## Introduction

Combined OpenAPI 3.0 specification for DNA Payments' Partner Tools: the Reporting API (Ecommerce & POS transaction reporting, Merchants) and the Settlement API. Generated from https://developer.dnapayments.com/docs/partner-tools/reporting/ documentation.

NOTE: The 'Reference' page (https://developer.dnapayments.com/docs/partner-tools/reporting/reporting-api/ecommerce/reference) which defines the full canonical enumerations of Transaction Statuses, Transaction Types, and Payment Methods for the Ecommerce endpoints could not be retrieved (the page returned a redirect error). Fields that rely on that reference (status, type, paymentMethod, cardType on Ecommerce transactions) are therefore modeled as free-form strings with illustrative examples rather than strict enums. Supply that page's content to tighten these definitions.

All URLs shown are the TEST/sandbox environment URLs published in the documentation; no production base URLs were provided in the source documentation.

## Install the Package

The package is compatible with Python versions `3.7+`.
Install the package from PyPi using the following pip command:

```bash
pip install dna-apimatic-sdk==5.0.0
```

You can also view the package at:
https://pypi.python.org/pypi/dna-apimatic-sdk/5.0.0

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| http_client_instance | `Union[Session, HttpClientProvider]` | The Http Client passed from the sdk user for making requests |
| override_http_client_configuration | `bool` | The value which determines to override properties of the passed Http Client from the sdk user |
| http_call_back | `HttpCallBack` | The callback value that is invoked before and after an HTTP call is made to an endpoint |
| timeout | `float` | The value to use for connection timeout. <br> **Default: 30** |
| max_retries | `int` | The number of times to retry an endpoint call if it fails. <br> **Default: 0** |
| backoff_factor | `float` | A backoff factor to apply between attempts after the second try. <br> **Default: 2** |
| retry_statuses | `Array of int` | The http statuses on which retry is to be done. <br> **Default: [408, 413, 429, 500, 502, 503, 504, 521, 522, 524]** |
| retry_methods | `Array of string` | The http methods on which retry is to be done. <br> **Default: ["GET", "PUT"]** |
| proxy_settings | [`ProxySettings`](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/proxy-settings.md) | Optional proxy configuration to route HTTP requests through a proxy server. |
| logging_configuration | [`LoggingConfiguration`](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/logging-configuration.md) | The SDK logging configuration for API calls |
| client_credentials_auth_credentials | [`ClientCredentialsAuthCredentials`](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/auth/oauth-2-client-credentials-grant.md) | The credential object for OAuth 2 Client Credentials Grant |

The API client can be initialized as follows:

### Code-Based Client Initialization

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

### Environment-Based Client Initialization

```python
from dnapaymentspartnerreportingsettlementapis.dnapaymentspartnerreportingsettlementapis_client import DnapaymentspartnerreportingsettlementapisClient

# Specify the path to your .env file if it’s located outside the project’s root directory.
client = DnapaymentspartnerreportingsettlementapisClient.from_environment(dotenv_path='/path/to/.env')
```

See the [Environment-Based Client Initialization](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/environment-based-client-initialization.md) section for details.

## Environments

The SDK can be configured to use a different environment for making API calls. Available environments are:

### Fields

| Name | Description |
|  --- | --- |
| PRODUCTION | **Default** Test/Sandbox API server (Reporting & Settlement APIs) |
| ENVIRONMENT2 | Test/Sandbox OAuth2 authorization server |

## Authorization

This API uses the following authentication schemes.

* [`BearerAuth (OAuth 2 Client Credentials Grant)`](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/auth/oauth-2-client-credentials-grant.md)

## List of APIs

* [Ecommerce Transactions](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/controllers/ecommerce-transactions.md)
* [POS Transactions](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/controllers/pos-transactions.md)
* [Authentication](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/controllers/authentication.md)
* [Merchants](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/controllers/merchants.md)
* [Settlements](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/controllers/settlements.md)

## SDK Infrastructure

### Configuration

* [ProxySettings](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/proxy-settings.md)
* [Environment-Based Client Initialization](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/environment-based-client-initialization.md)
* [AbstractLogger](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/abstract-logger.md)
* [LoggingConfiguration](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/logging-configuration.md)
* [RequestLoggingConfiguration](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/request-logging-configuration.md)
* [ResponseLoggingConfiguration](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/response-logging-configuration.md)

### HTTP

* [HttpResponse](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/http-response.md)
* [HttpRequest](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/http-request.md)

### Utilities

* [ApiResponse](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/api-response.md)
* [ApiHelper](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/api-helper.md)
* [HttpDateTime](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/http-date-time.md)
* [RFC3339DateTime](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/rfc3339-date-time.md)
* [UnixDateTime](https://www.github.com/sdks-io/dna-apimatic-python-sdk/tree/5.0.0/doc/unix-date-time.md)

