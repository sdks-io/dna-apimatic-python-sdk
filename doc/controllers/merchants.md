# Merchants

Look up merchant IDs and terminal configuration.

```python
merchants_api = client.merchants
```

## Class Name

`MerchantsApi`

## Methods

* [Get Merchants V1](../../doc/controllers/merchants.md#get-merchants-v1)
* [Get Merchants V2](../../doc/controllers/merchants.md#get-merchants-v2)


# Get Merchants V1

**This endpoint is deprecated.**

Returns the merchants available to the authenticated partner. **Deprecated** — use V2 (`/v2/partners/merchants`) instead.

```python
def get_merchants_v_1(self)
```

## Authentication

This endpoint requires [BearerAuth](../../doc/auth/oauth-2-client-credentials-grant.md)

## Response Type

**200**: Merchants returned successfully.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`List[MerchantV1]`](../../doc/models/merchant-v1.md).

## Example Usage

```python
result = merchants_api.get_merchants_v_1()

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Example Response *(as JSON)*

```json
[
  {
    "id": "53f2e71f-4399-493f-8acf-14d362425ax1",
    "name": "Merchant Number One"
  }
]
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request — request format is invalid. | [`ErrorException`](../../doc/models/error-exception.md) |
| 401 | Unauthorized — invalid authentication credentials have been supplied. | [`ErrorException`](../../doc/models/error-exception.md) |
| 403 | Forbidden — authorisation has failed due to insufficient permissions. | [`ErrorException`](../../doc/models/error-exception.md) |


# Get Merchants V2

Returns the merchants available to the authenticated partner, including terminal configuration for each merchant. Supports pagination and filtering by processor.

```python
def get_merchants_v_2(self,
                     processor=None,
                     page=1,
                     size=1000)
```

## Authentication

This endpoint requires [BearerAuth](../../doc/auth/oauth-2-client-credentials-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `processor` | [`Processor`](../../doc/models/processor.md) | Query, Optional | Filter merchants by the processor used for transactions. |
| `page` | `int` | Query, Optional | Specifies which set of records to retrieve.<br><br>**Default**: `1`<br><br>**Constraints**: `>= 1` |
| `size` | `int` | Query, Optional | Specifies how many records per page will be returned.<br><br>**Default**: `1000`<br><br>**Constraints**: `>= 1`, `<= 5000` |

## Response Type

**200**: Merchants returned successfully.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`MerchantsV2Response`](../../doc/models/merchants-v2-response.md).

## Example Usage

```python
page = 1

size = 1000

result = merchants_api.get_merchants_v_2(
    page=page,
    size=size
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Example Response *(as JSON)*

```json
{
  "data": [
    {
      "descriptor": "MELCHESTER UNITED",
      "id": "711db2d-f055-4d2b-ab5c-728772aa0887",
      "isActive": true,
      "name": "MELCHESTER UNITED FC",
      "terminals": [
        {
          "id": "7a2e086d-32c3-4917-5bf9-3a7d1a211126",
          "dailySettlement": false,
          "settlementPeriod": 1,
          "storeName": "MELCHESTER UNITED FC",
          "type": "ecom",
          "status": "open"
        }
      ]
    },
    {
      "descriptor": "TPFC POS",
      "id": "79112a4e-558e-4b7e-89cd-67e0e1e4v59b",
      "isActive": true,
      "name": "TOWN POOLE FC - POS",
      "reconciliationId": "443318",
      "terminals": [
        {
          "id": "03001235",
          "dailySettlement": true,
          "mid": "1602034564",
          "settlementPeriod": 1,
          "storeName": "TOWN POOLE FC",
          "type": "pos",
          "status": "open"
        }
      ]
    },
    {
      "descriptor": "ABC - YCCC",
      "id": "3d2a6951-6e52-4be1-97db-b8cd7c12c93f",
      "isActive": true,
      "name": "ABC - Yeovil City Cricket Club - ECOM",
      "reconciliationId": "493764",
      "terminals": [
        {
          "id": "ffa7423a-5f18-423b-9c35-35e05d446213",
          "dailySettlement": false,
          "settlementPeriod": 1,
          "storeName": "ABC - YCCC",
          "type": "ecom",
          "status": "closed"
        }
      ]
    }
  ],
  "totalCount": 3
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request — request format is invalid. | [`ErrorException`](../../doc/models/error-exception.md) |
| 401 | Unauthorized — invalid authentication credentials have been supplied. | [`ErrorException`](../../doc/models/error-exception.md) |
| 403 | Forbidden — authorisation has failed due to insufficient permissions. | [`ErrorException`](../../doc/models/error-exception.md) |

