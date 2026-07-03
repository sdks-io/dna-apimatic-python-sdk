
# Ecommerce Transactions Response

*This model accepts additional fields of type Any.*

## Structure

`EcommerceTransactionsResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `total_count` | `int` | Optional | Total count of records for the requested time period. |
| `data` | [`List[EcommerceTransaction]`](../../doc/models/ecommerce-transaction.md) | Optional | - |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from dnapaymentspartnerreportingsettlementapis.models.ecommerce_transaction import EcommerceTransaction
from dnapaymentspartnerreportingsettlementapis.models.ecommerce_transactions_response import EcommerceTransactionsResponse

ecommerce_transactions_response = EcommerceTransactionsResponse(
    total_count=64,
    data=[
        EcommerceTransaction(
            id='id0',
            merchant_id='merchantId6',
            merchant_name='merchantName0',
            merchant_reference='merchantReference4',
            amount=43.32,
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        EcommerceTransaction(
            id='id0',
            merchant_id='merchantId6',
            merchant_name='merchantName0',
            merchant_reference='merchantReference4',
            amount=43.32,
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        EcommerceTransaction(
            id='id0',
            merchant_id='merchantId6',
            merchant_name='merchantName0',
            merchant_reference='merchantReference4',
            amount=43.32,
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

