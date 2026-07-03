
# Ecommerce Transaction

*This model accepts additional fields of type Any.*

## Structure

`EcommerceTransaction`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `str` | Optional | Unique transaction ID. |
| `merchant_id` | `str` | Optional | Unique ID for the merchant, allocated by DNA Payments. |
| `merchant_name` | `str` | Optional | Name of the merchant. |
| `merchant_reference` | `str` | Optional | Unique order number allocated by the merchant. |
| `amount` | `float` | Optional | Original requested transaction amount. |
| `currency` | `str` | Optional | Transaction currency code. ISO 4217 format, e.g. GBP. |
| `created_date` | `datetime` | Optional | Date/time the transaction was created on the DNA Platform. |
| `auth_date` | `datetime` | Optional | Date/time the transaction authorisation was attempted with the acquirer. |
| `confirm_date` | `datetime` | Optional | Date/time the transaction was confirmed on the DNA Platform. |
| `processed_date` | `datetime` | Optional | Date/time the transaction was processed (last action performed, e.g. charged/settled/refunded). |
| `processed_amount` | `float` | Optional | Charged/Settled/Refunded amount. |
| `mtype` | `str` | Optional | Transaction type. See the Ecommerce Reference documentation for the full list (not available at spec-generation time). |
| `status` | `str` | Optional | Status of the transaction. See the Ecommerce Reference documentation for the full list (not available at spec-generation time). |
| `payment_method` | `str` | Optional | Payment method used on the transaction. See the Ecommerce Reference documentation for the full list (not available at spec-generation time). |
| `card_type` | `str` | Optional | Type of card used in the transaction. |
| `card_scheme` | `str` | Optional | Card scheme used in the transaction, e.g. mastercard, visa. |
| `card_mask` | `str` | Optional | Masked PAN for the payment card used; contains the first six and last four digits. |
| `issuer` | `str` | Optional | Issuer of the payment card used in the transaction. |
| `issuer_country` | `str` | Optional | Country in which the payment card was issued. ISO 3166-1 alpha-3. |
| `response_code` | `str` | Optional | Response code returned by the acquirer during authorisation. |
| `auth_code` | `str` | Optional | Authorisation code issued by the acquirer/issuer for the transaction, when applicable. |
| `avs_result` | `str` | Optional | Result of the Address Verification System (AVS) check. |
| `avs_house_number_result` | `str` | Optional | Result of the AVS 'House Number' check. |
| `avs_postcode_result` | `str` | Optional | Result of the AVS 'Post Code' check. |
| `csc_result` | `str` | Optional | Result of the Cardholder Security Code (CSC) check. |
| `payer_authentication_result` | `str` | Optional | Result of the Payer Authentication enrollment/authentication checks, format Enrollment/Authentication e.g. Y/A. |
| `payer_ip` | `str` | Optional | IP address of the consumer. Subject to GDPR confirmation; may be removed. |
| `payer_name` | `str` | Optional | Consumer name. Subject to GDPR confirmation; may be removed. |
| `payer_email` | `str` | Optional | Email address of the consumer. Subject to GDPR confirmation; may be removed. |
| `payer_phone` | `str` | Optional | Phone number of the consumer. Subject to GDPR confirmation; may be removed. |
| `ip_country` | `str` | Optional | Country where the purchase was made. Subject to GDPR confirmation; may be removed. |
| `ip_city` | `str` | Optional | City where the purchase was made. Subject to GDPR confirmation; may be removed. |
| `ip_latitude` | `float` | Optional | Locational data – latitude. Subject to GDPR confirmation; may be removed. |
| `ip_longitude` | `float` | Optional | Locational data – longitude. Subject to GDPR confirmation; may be removed. |
| `merchant_custom_data` | `str` | Optional | Base64-encoded custom data supplied by the merchant with the transaction request. Max 1024 bytes. Not used for any processing, purely recorded. |
| `description` | `str` | Optional | Descriptive text passed in the Payment Request for the transaction. |
| `parent_transaction_id` | `str` | Optional | If the transaction is a full/partial refund, the transactionId of the original/linked sale. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from dnapaymentspartnerreportingsettlementapis.models.ecommerce_transaction import EcommerceTransaction

ecommerce_transaction = EcommerceTransaction(
    id='id0',
    merchant_id='merchantId6',
    merchant_name='merchantName0',
    merchant_reference='merchantReference4',
    amount=61.12,
    currency='GBP',
    mtype='retail',
    status='charged',
    payment_method='card',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

