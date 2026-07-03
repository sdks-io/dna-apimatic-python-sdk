
# Terminal

*This model accepts additional fields of type Any.*

## Structure

`Terminal`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `str` | Optional | Unique Terminal ID for the merchant, allocated by DNA Payments. |
| `mid` | `str` | Optional | MID allocated by DNA Payments. Available only for the pos terminal type. |
| `daily_settlement` | `bool` | Optional | If true, a separate payment is received each day. If false, a single payment is received on Monday for the entire weekend (Fri/Sat/Sun combined). |
| `settlement_period` | `int` | Optional | Number of days after which settlement is processed for this merchant. |
| `store_name` | `str` | Optional | Name of the merchant store provided during onboarding. |
| `mtype` | [`Type`](../../doc/models/type.md) | Optional | Type of terminal: ecom (Ecommerce TID) or pos (physical terminal). |
| `status` | [`Status`](../../doc/models/status.md) | Optional | open: all operations allowed. suspended/pending-closure: merchant-initiated operations prohibited, settlements/disputes still allowed. closed: no activity allowed. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from dnapaymentspartnerreportingsettlementapis.models.terminal import Terminal

terminal = Terminal(
    id='id2',
    mid='mid2',
    daily_settlement=False,
    settlement_period=6,
    store_name='storeName4',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

