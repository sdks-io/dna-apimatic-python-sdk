# Settlements

Query settlement records for your merchants.

```python
settlements_api = client.settlements
```

## Class Name

`SettlementsApi`


# Get Settlements

Query settlements for your merchants. Settlement records are available for 365 days; a maximum span of 30 days can be specified per request via `from`/`to`.

```python
def get_settlements(self,
                   mfrom,
                   to,
                   page=1,
                   size=50,
                   search_by=None,
                   merchant_id=None,
                   transaction_id=None)
```

## Authentication

This endpoint requires [BearerAuth](../../doc/auth/oauth-2-client-credentials-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `mfrom` | `date` | Query, Required | Start date for settlements. Available for 365 days; a maximum of 30 days can be specified. |
| `to` | `date` | Query, Required | End date for settlements. Available for 365 days; a maximum of 30 days can be specified. |
| `page` | `int` | Query, Optional | Page number required.<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `size` | `int` | Query, Optional | Number of records to return.<br><br>**Default**: `50`<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `search_by` | [`SearchBy`](../../doc/models/search-by.md) | Query, Optional | Confirms which date is being used in the query. If not supplied, `processed-date` is used. |
| `merchant_id` | `str` | Query, Optional | Unique id(s) for the merchant, allocated by DNA Payments and returned in GET Merchants. Up to 10 IDs may be submitted, comma separated. Specifying an id will only return results for that merchant. |
| `transaction_id` | `str` | Query, Optional | Filter settlements by a specific transaction ID. |

## Response Type

**200**: Settlements returned successfully.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`SettlementsResponse`](../../doc/models/settlements-response.md).

## Example Usage

```python
mfrom = dateutil.parser.parse('2024-06-18').date()

to = dateutil.parser.parse('2024-06-19').date()

page = 1

size = 50

merchant_id = '2864dd92-343a-4ce7-b1f9-9742e3c7f07d,9a8a7d6e-5011-4976-b6fa-37dd96de56c0'

result = settlements_api.get_settlements(
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
  "totalCount": 3,
  "data": [
    {
      "processedDate": "2024-06-19",
      "settlementDate": "2024-06-20",
      "merchantId": "6a3848c5-1c2c-4903-b621-879db6277402",
      "merchantName": "Test Merchant",
      "amount": 0,
      "acquirerFee": -0.03,
      "amountToMerchant": -0.03,
      "currency": "GBP",
      "operation": "advice",
      "transactionId": null,
      "transactionDate": "2024-06-19T00:00:00Z",
      "transactionType": "declined-txn",
      "merchantReference": null,
      "cardScheme": "visa",
      "cardType": "debit",
      "isEuropeanCard": null,
      "isCorporateCard": false,
      "cardMask": null,
      "captureMethod": null,
      "issuerCountry": null,
      "merchantCustomData": null
    },
    {
      "processedDate": "2024-06-19",
      "settlementDate": "2024-06-20",
      "merchantId": "6a3848c5-1c2c-4903-b621-879db6277402",
      "merchantName": "Test Merchant",
      "amount": 3.6,
      "acquirerFee": -0.03972,
      "amountToMerchant": 3.56028,
      "currency": "GBP",
      "operation": "advice",
      "transactionId": "M138811RC46A",
      "transactionDate": "2024-06-19T21:59:55Z",
      "transactionType": "retail",
      "merchantReference": "M138811RC46A",
      "cardScheme": "visa",
      "cardType": "debit",
      "isEuropeanCard": true,
      "isCorporateCard": false,
      "cardMask": "475130...4321",
      "captureMethod": "pos-contactless",
      "issuerCountry": "GBR",
      "merchantCustomData": null
    },
    {
      "processedDate": "2024-06-18",
      "settlementDate": "2024-06-21",
      "merchantId": "6a3848c5-1c2c-4903-b621-879db6277402",
      "merchantName": "Test Merchant",
      "amount": 72.99,
      "acquirerFee": -2.263431,
      "amountToMerchant": 70.726569,
      "currency": "GBP",
      "operation": "advice",
      "transactionId": "3bc9ae58-9528-24a1-9336-c5cc5cf8d1c2",
      "transactionDate": "2024-06-18T17:48:54Z",
      "transactionType": "retail",
      "merchantReference": "114422",
      "cardScheme": null,
      "cardType": null,
      "isEuropeanCard": null,
      "isCorporateCard": null,
      "cardMask": null,
      "captureMethod": "ecom-klarna",
      "issuerCountry": null,
      "merchantCustomData": null
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

