# POS Transactions

```python
pos_transactions_api = client.pos_transactions
```

## Class Name

`PosTransactionsApi`

## Methods

* [Get Pos Transactions](../../doc/controllers/pos-transactions.md#get-pos-transactions)
* [Get Pos Transaction by Id](../../doc/controllers/pos-transactions.md#get-pos-transaction-by-id)


# Get Pos Transactions

Query all POS transactions processed by your merchants. Transactions are available for 365 days; a maximum span of 30 days can be specified per request via `from`/`to`.

```python
def get_pos_transactions(self,
                        mfrom,
                        to,
                        page=1,
                        size=50,
                        merchant_id=None,
                        status=None)
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
| `status` | [`Status2`](../../doc/models/status-2.md) | Query, Optional | Filter POS results by transaction status. |

## Response Type

**200**: POS transactions returned successfully.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`PosTransactionsResponse`](../../doc/models/pos-transactions-response.md).

## Example Usage

```python
mfrom = dateutil.parser.parse('01/25/2021 15:29:56')

to = dateutil.parser.parse('01/25/2021 15:29:56')

page = 1

size = 50

merchant_id = '2864dd92-343a-4ce7-b1f9-9742e3c7f07d,9a8a7d6e-5011-4976-b6fa-37dd96de56c0'

result = pos_transactions_api.get_pos_transactions(
    mfrom,
    to,
    page=page,
    size=size,
    merchant_id=merchant_id
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Example Response *(as JSON)*

```json
{
  "totalAmount": 39.87,
  "totalCount": 2,
  "data": [
    {
      "merchantId": "fd9991e8-802a-46f7-9d23-7981a852de17",
      "merchantName": "TEST LIMITED",
      "transactionDate": "2021-03-13T23:10:21Z",
      "amount": 29,
      "currency": "GBP",
      "status": "success",
      "returnCode": "0",
      "returnCodeDescription": "Successfully completed",
      "transactionId": "M139811RG4CN",
      "terminalId": "03100423",
      "operation": "advice",
      "transactionType": "retail",
      "transactionCountry": "GBR",
      "transactionCity": "Maidstone",
      "cardScheme": "mastercard",
      "cardMask": "522499...9909",
      "cardType": "credit",
      "isEuropeanCard": true,
      "isCorporateCard": false,
      "captureMethod": "pos-contactless"
    },
    {
      "merchantId": "fd9991e8-802a-46f7-9d23-7981a852de17",
      "merchantName": "TEST LIMITED",
      "transactionDate": "2021-03-13T22:39:12Z",
      "amount": 10.87,
      "currency": "GBP",
      "status": "success",
      "returnCode": "0",
      "returnCodeDescription": "Successfully completed",
      "transactionId": "M138811RG1PK",
      "terminalId": "03000024",
      "operation": "advice",
      "transactionType": "retail",
      "transactionCountry": "GBR",
      "transactionCity": "Maidstone",
      "cardScheme": "visa",
      "cardMask": "420000...0000",
      "cardType": "credit",
      "isEuropeanCard": true,
      "isCorporateCard": false,
      "captureMethod": "pos-contactless"
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
| 404 | Not Found — the requested resource does not exist. | [`ErrorException`](../../doc/models/error-exception.md) |
| 422 | Unprocessable Entity — the API cannot complete the requested action. | [`ErrorException`](../../doc/models/error-exception.md) |
| 500 | Internal Server Error — an internal error has occurred, please try again later. | [`ErrorException`](../../doc/models/error-exception.md) |
| 503 | Service Unavailable — API is temporarily offline for maintenance, please try again later. | [`ErrorException`](../../doc/models/error-exception.md) |


# Get Pos Transaction by Id

Query a single POS transaction processed by any of your merchants, using the transaction ID returned from a previous list query.

```python
def get_pos_transaction_by_id(self,
                             transaction_id)
```

## Authentication

This endpoint requires [BearerAuth](../../doc/auth/oauth-2-client-credentials-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `transaction_id` | `str` | Template, Required | Unique transaction ID, as returned by GET POS Transactions. |

## Response Type

**200**: POS transaction returned successfully.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`PosTransaction`](../../doc/models/pos-transaction.md).

## Example Usage

```python
transaction_id = '1c0d2a11-911e-4d3a-b9f2-1977d874d7b1'

result = pos_transactions_api.get_pos_transaction_by_id(transaction_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Example Response *(as JSON)*

```json
{
  "merchantId": "fd9991e8-802a-46f7-9d23-7981a852de17",
  "merchantName": "TEST LIMITED",
  "transactionDate": "2021-03-13T22:39:12Z",
  "amount": 10.87,
  "currency": "GBP",
  "status": "success",
  "returnCode": "0",
  "returnCodeDescription": "Successfully completed",
  "transactionId": "M138811RG1PK",
  "terminalId": "03000024",
  "operation": "advice",
  "transactionType": "retail",
  "transactionCountry": "GBR",
  "transactionCity": "Maidstone",
  "cardScheme": "visa",
  "cardMask": "420000...0000",
  "cardType": "credit",
  "isEuropeanCard": true,
  "isCorporateCard": false,
  "captureMethod": "pos-contactless"
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request — request format is invalid. | [`ErrorException`](../../doc/models/error-exception.md) |
| 401 | Unauthorized — invalid authentication credentials have been supplied. | [`ErrorException`](../../doc/models/error-exception.md) |
| 403 | Forbidden — authorisation has failed due to insufficient permissions. | [`ErrorException`](../../doc/models/error-exception.md) |
| 404 | Not Found — the requested resource does not exist. | [`ErrorException`](../../doc/models/error-exception.md) |
| 422 | Unprocessable Entity — the API cannot complete the requested action. | [`ErrorException`](../../doc/models/error-exception.md) |
| 500 | Internal Server Error — an internal error has occurred, please try again later. | [`ErrorException`](../../doc/models/error-exception.md) |
| 503 | Service Unavailable — API is temporarily offline for maintenance, please try again later. | [`ErrorException`](../../doc/models/error-exception.md) |

