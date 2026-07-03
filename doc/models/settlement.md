
# Settlement

*This model accepts additional fields of type Any.*

## Structure

`Settlement`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `processed_date` | `date` | Optional | Date that the settlement process was started. |
| `settlement_date` | `date` | Optional | Date that the transaction was settled. |
| `merchant_id` | `str` | Optional | Unique ID for the merchant, allocated by DNA Payments. |
| `merchant_name` | `str` | Optional | Name of the merchant who processed the transaction. |
| `amount` | `float` | Optional | Original requested transaction amount. |
| `acquirer_fee` | `float` | Optional | Acquiring fee charged for processing the transaction. |
| `amount_to_merchant` | `float` | Optional | Amount settled to the merchant. |
| `currency` | `str` | Optional | Currency of the transaction, e.g. GBP. |
| `operation` | [`Operation`](../../doc/models/operation.md) | Optional | Confirmation of the operation performed. |
| `transaction_id` | `str` | Optional | Unique transaction ID. Null for non-transactional fees. |
| `transaction_date` | `datetime` | Optional | Date/time the transaction was processed. |
| `transaction_type` | [`TransactionType`](../../doc/models/transaction-type.md) | Optional | Type of transaction/fee recorded in the Settlement (and, by reference, POS Reporting) API. |
| `merchant_reference` | `str` | Optional | Unique order number allocated by the merchant. |
| `card_scheme` | `str` | Optional | Card scheme used in the transaction. |
| `card_type` | [`CardType`](../../doc/models/card-type.md) | Optional | Type of card used in the transaction. |
| `is_european_card` | `bool` | Optional | Whether the card used is issued in Europe (including the UK). |
| `is_corporate_card` | `bool` | Optional | Whether the card used is a corporate card. |
| `card_mask` | `str` | Optional | Masked PAN for the payment card used; contains the first six and last four digits. |
| `capture_method` | [`CaptureMethod`](../../doc/models/capture-method.md) | Optional | Capture method for the transaction. |
| `issuer_country` | `str` | Optional | Country in which the payment card was issued. ISO 3166-1 alpha-3. Null if it cannot be determined. |
| `merchant_custom_data` | `str` | Optional | Custom data provided by the integrated solution for the transaction. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from dnapaymentspartnerreportingsettlementapis.models.settlement import Settlement

settlement = Settlement(
    processed_date=dateutil.parser.parse('2016-03-13').date(),
    settlement_date=dateutil.parser.parse('2016-03-13').date(),
    merchant_id='merchantId8',
    merchant_name='merchantName2',
    amount=216.64,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

