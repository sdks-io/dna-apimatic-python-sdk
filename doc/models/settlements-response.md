
# Settlements Response

*This model accepts additional fields of type Any.*

## Structure

`SettlementsResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `total_count` | `int` | Optional | Total count of records for the requested time period. |
| `data` | [`List[Settlement]`](../../doc/models/settlement.md) | Optional | - |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from dnapaymentspartnerreportingsettlementapis.models.settlement import Settlement
from dnapaymentspartnerreportingsettlementapis.models.settlements_response import SettlementsResponse

settlements_response = SettlementsResponse(
    total_count=98,
    data=[
        Settlement(
            processed_date=dateutil.parser.parse('2016-03-13').date(),
            settlement_date=dateutil.parser.parse('2016-03-13').date(),
            merchant_id='merchantId6',
            merchant_name='merchantName0',
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

