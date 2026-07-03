
# Merchants V2 Response

*This model accepts additional fields of type Any.*

## Structure

`MerchantsV2Response`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `data` | [`List[MerchantV2]`](../../doc/models/merchant-v2.md) | Optional | - |
| `total_count` | `int` | Optional | - |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from dnapaymentspartnerreportingsettlementapis.models.merchant_v_2 import MerchantV2
from dnapaymentspartnerreportingsettlementapis.models.merchants_v_2_response import MerchantsV2Response

merchants_v_2_response = MerchantsV2Response(
    data=[
        MerchantV2(
            descriptor='descriptor2',
            id='id0',
            name='name0',
            is_active=False,
            reconciliation_id='reconciliationId2',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        MerchantV2(
            descriptor='descriptor2',
            id='id0',
            name='name0',
            is_active=False,
            reconciliation_id='reconciliationId2',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    total_count=178,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

