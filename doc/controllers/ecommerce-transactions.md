# Ecommerce Transactions

```python
ecommerce_transactions_api = client.ecommerce_transactions
```

## Class Name

`EcommerceTransactionsApi`

## Methods

* [Get Ecommerce Transactions](../../doc/controllers/ecommerce-transactions.md#get-ecommerce-transactions)
* [Get Ecommerce Transaction by Id](../../doc/controllers/ecommerce-transactions.md#get-ecommerce-transaction-by-id)


# Get Ecommerce Transactions

Query Ecommerce transactions processed by your merchants. Transactions are available for 365 days; a maximum span of 30 days can be specified per request via `from`/`to`.

```python
def get_ecommerce_transactions(self,
                              mfrom,
                              to,
                              page=1,
                              size=50,
                              merchant_id=None,
                              status=None,
                              processor=None,
                              search_by=None)
```

## Authentication

This endpoint requires [BearerAuth](../../doc/auth/oauth-2-client-credentials-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `mfrom` | `datetime` | Query, Required | Start date/time for transactions. Transactions are available for 365 days and a maximum of 30 days can be specified per request. ISO 8601 format. |
| `to` | `datetime` | Query, Required | End date/time for transactions. Transactions are available for 365 days and a maximum of 30 days can be specified per request. ISO 8601 format. |
| `page` | `int` | Query, Optional | Page number required.<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `size` | `int` | Query, Optional | Number of records to return.<br><br>**Default**: `50`<br><br>**Constraints**: `>= 1`, `<= 5000` |
| `merchant_id` | `str` | Query, Optional | Unique id(s) for the merchant, allocated by DNA Payments and returned in GET Merchants. Up to 10 IDs may be submitted, comma separated. Specifying an id will only return results for that merchant. |
| `status` | `str` | Query, Optional | Filter by transaction status. Multiple statuses may be supplied, comma separated. See the Ecommerce Reference documentation for the full list of statuses (not available at spec-generation time). |
| `processor` | [`Processor`](../../doc/models/processor.md) | Query, Optional | Filter transactions by the platform responsible for processing the transaction. |
| `search_by` | `str` | Query, Optional | Allows filtering of transactions by the field used to match the from/to date range (as documented, this parameter mirrors the processor filtering behaviour described in the source docs). |

## Response Type

**200**: Transactions returned successfully.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`EcommerceTransactionsResponse`](../../doc/models/ecommerce-transactions-response.md).

## Example Usage

```python
mfrom = dateutil.parser.parse('01/25/2021 15:29:56')

to = dateutil.parser.parse('01/25/2021 15:29:56')

page = 1

size = 50

merchant_id = '2864dd92-343a-4ce7-b1f9-9742e3c7f07d,9a8a7d6e-5011-4976-b6fa-37dd96de56c0'

status = 'refunded,rejected'

result = ecommerce_transactions_api.get_ecommerce_transactions(
    mfrom,
    to,
    page=page,
    size=size,
    merchant_id=merchant_id,
    status=status
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Example Response *(as JSON)*

```json
{
  "totalCount": 92,
  "data": [
    {
      "id": "1c0d2a11-911e-4d3a-b9f2-1977d874d7b1",
      "merchantId": "0724dd92-343a-6ce7-b1f9-9742e3c6f08k",
      "merchantName": "Test Merchant",
      "merchantReference": "1611822317082",
      "amount": 0.5,
      "currency": "GBP",
      "createdDate": "2021-01-28T10:09:16.863868Z",
      "authDate": "2021-01-28T10:09:45.485728Z",
      "confirmDate": "2021-01-28T10:09:45.485728Z",
      "processedDate": "2021-01-28T10:09:45.485727Z",
      "processedAmount": 0.5,
      "type": "retail",
      "status": "charged",
      "paymentMethod": "card",
      "cardScheme": "mastercard",
      "cardMask": "535522...7288",
      "issuer": "Monzo Bank Limited",
      "issuerCountry": "GBR",
      "responseCode": "00",
      "authCode": "1602300039",
      "avsResult": "",
      "avsHouseNumberResult": "",
      "avsPostcodeResult": "",
      "cscResult": "",
      "payerAuthenticationResult": "Y/Y",
      "payerIp": "",
      "payerName": "John Doe",
      "payerEmail": "",
      "payerPhone": null,
      "ipCountry": "United Kingdom",
      "ipCity": "",
      "ipLatitude": 50.4921,
      "ipLongitude": -0.1321,
      "merchantCustomData": "YmluYXJ5IGRhdGE=",
      "description": "Test Transaction",
      "parentTransactionId": null
    }
  ]
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request — request format is invalid. | [`ErrorException`](../../doc/models/error-exception.md) |
| 401 | Unauthorized — invalid authentication credentials have been supplied. | [`ErrorException`](../../doc/models/error-exception.md) |
| 403 | Forbidden — authorisation has failed due to insufficient permissions. | [`ErrorException`](../../doc/models/error-exception.md) |


# Get Ecommerce Transaction by Id

Query a single Ecommerce transaction processed by any of your merchants, using the transaction ID returned from a previous list query.

```python
def get_ecommerce_transaction_by_id(self,
                                   transaction_id)
```

## Authentication

This endpoint requires [BearerAuth](../../doc/auth/oauth-2-client-credentials-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `transaction_id` | `str` | Template, Required | Unique transaction ID, as returned by GET Transactions. |

## Response Type

**200**: Transaction returned successfully.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`EcommerceTransaction`](../../doc/models/ecommerce-transaction.md).

## Example Usage

```python
transaction_id = '6283b982-14f3-46c9-bcaf-c228e0050503'

result = ecommerce_transactions_api.get_ecommerce_transaction_by_id(transaction_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Example Response *(as JSON)*

```json
{
  "id": "6283b982-14f3-46c9-bcaf-c228e0050503",
  "merchantId": "2234bec9-299d-414f-b5bd-4cda29e96ffd",
  "merchantName": "Test Merchant",
  "merchantReference": "1619713419029",
  "amount": 25,
  "currency": "GBP",
  "createdDate": "2021-04-29T16:24:41.257552Z",
  "authDate": "2021-04-29T16:24:52.375995Z",
  "confirmDate": "2021-04-29T16:24:52.247515Z",
  "processedDate": "2021-04-29T16:24:52.247513Z",
  "processedAmount": 25,
  "type": "sale",
  "status": "charged",
  "paymentMethod": "card",
  "cardScheme": "mastercard",
  "cardMask": "528390...2672",
  "issuer": "AS LHV Pank",
  "issuerCountry": "EST",
  "responseCode": "00",
  "authCode": "1602071111",
  "avsResult": "",
  "avsHouseNumberResult": "Not Checked",
  "avsPostcodeResult": "Not Checked",
  "cscResult": "Not Set",
  "payerAuthenticationResult": "C/Y",
  "payerIp": "",
  "payerName": "CHALLENGE SD",
  "payerEmail": "",
  "payerPhone": "",
  "ipCountry": "",
  "ipCity": "",
  "ipLatitude": 0,
  "ipLongitude": 0,
  "description": "Car Service",
  "merchantCustomData": null,
  "parentTransactionId": null
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request — request format is invalid. | [`ErrorException`](../../doc/models/error-exception.md) |
| 401 | Unauthorized — invalid authentication credentials have been supplied. | [`ErrorException`](../../doc/models/error-exception.md) |
| 403 | Forbidden — authorisation has failed due to insufficient permissions. | [`ErrorException`](../../doc/models/error-exception.md) |
| 404 | Not Found — the requested resource does not exist. | [`ErrorException`](../../doc/models/error-exception.md) |

