
# Pos Transaction

*This model accepts additional fields of type Any.*

## Structure

`PosTransaction`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `merchant_id` | `str` | Optional | Unique ID for the merchant, allocated by DNA Payments. |
| `merchant_name` | `str` | Optional | Name of the merchant. |
| `transaction_date` | `datetime` | Optional | Date/time the transaction was created on the DNA Platform. |
| `amount` | `float` | Optional | Transaction amount. |
| `currency` | `str` | Optional | Transaction currency code. ISO 4217 format, e.g. GBP. |
| `status` | [`Status1`](../../doc/models/status-1.md) | Optional | success: successful transaction. failed: failed transaction. |
| `return_code` | `str` | Optional | Response code returned by the Acquirer during the authorisation process. |
| `return_code_description` | `str` | Optional | Description of the returnCode returned by the Acquirer. |
| `transaction_id` | `str` | Optional | Unique ID allocated to the transaction. |
| `terminal_id` | `str` | Optional | Unique Terminal ID for the merchant, allocated by DNA Payments. |
| `operation` | [`Operation`](../../doc/models/operation.md) | Optional | Confirmation of the operation performed. |
| `transaction_type` | [`TransactionType`](../../doc/models/transaction-type.md) | Optional | Type of transaction/fee recorded in the Settlement (and, by reference, POS Reporting) API. |
| `transaction_country` | `str` | Optional | Country where the transaction was processed. |
| `transaction_city` | `str` | Optional | City where the transaction was processed. |
| `card_scheme` | `str` | Optional | Card scheme used in the transaction, e.g. mastercard, visa. |
| `card_mask` | `str` | Optional | Masked PAN for the payment card used; contains the first six and last four digits. |
| `card_type` | `str` | Optional | Type of card used in the transaction. |
| `is_european_card` | `bool` | Optional | Whether the card used was issued in Europe (including the UK). |
| `is_corporate_card` | `bool` | Optional | Whether the card used is a corporate card. |
| `capture_method` | [`CaptureMethod`](../../doc/models/capture-method.md) | Optional | Capture method for the transaction. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from dnapaymentspartnerreportingsettlementapis.models.pos_transaction import PosTransaction

pos_transaction = PosTransaction(
    merchant_id='merchantId8',
    merchant_name='merchantName2',
    transaction_date=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
    amount=123.64,
    currency='GBP',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

