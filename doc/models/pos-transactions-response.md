
# Pos Transactions Response

*This model accepts additional fields of type Any.*

## Structure

`PosTransactionsResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `total_amount` | `float` | Optional | Total amount for the requested time period. |
| `total_count` | `int` | Optional | Total count of records for the requested time period. |
| `data` | [`List[PosTransaction]`](../../doc/models/pos-transaction.md) | Optional | - |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from dnapaymentspartnerreportingsettlementapis.models.pos_transaction import PosTransaction
from dnapaymentspartnerreportingsettlementapis.models.pos_transactions_response import PosTransactionsResponse

pos_transactions_response = PosTransactionsResponse(
    total_amount=4.92,
    total_count=118,
    data=[
        PosTransaction(
            merchant_id='merchantId6',
            merchant_name='merchantName0',
            transaction_date=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
            amount=43.32,
            currency='currency0',
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

