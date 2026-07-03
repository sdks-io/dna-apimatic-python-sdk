
# Merchant V2

*This model accepts additional fields of type Any.*

## Structure

`MerchantV2`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `descriptor` | `str` | Optional | Merchant descriptor as it appears on the consumer's bank statement for DNA Acquiring. |
| `id` | `str` | Optional | Unique ID for the merchant, allocated by DNA Payments. |
| `name` | `str` | Optional | Name of the merchant. |
| `is_active` | `bool` | Optional | Whether the merchant is active. |
| `reconciliation_id` | `str` | Optional | Unique ID allocated by DNA Payments to the merchant account; appears on the merchant bank statement when payments/settlements are made. |
| `terminals` | [`List[Terminal]`](../../doc/models/terminal.md) | Optional | List of all Terminal IDs configured for the merchant. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from dnapaymentspartnerreportingsettlementapis.models.merchant_v_2 import MerchantV2

merchant_v_2 = MerchantV2(
    descriptor='descriptor4',
    id='id2',
    name='name2',
    is_active=False,
    reconciliation_id='reconciliationId4',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

