
# Merchant V1

*This model accepts additional fields of type Any.*

## Structure

`MerchantV1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `str` | Optional | Unique ID for the merchant, allocated by DNA Payments. |
| `name` | `str` | Optional | Name of the merchant. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from dnapaymentspartnerreportingsettlementapis.models.merchant_v_1 import MerchantV1

merchant_v_1 = MerchantV1(
    id='id6',
    name='name6',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

