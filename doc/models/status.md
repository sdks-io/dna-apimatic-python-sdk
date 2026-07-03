
# Status

open: all operations allowed. suspended/pending-closure: merchant-initiated operations prohibited, settlements/disputes still allowed. closed: no activity allowed.

## Enumeration

`Status`

## Fields

| Name |
|  --- |
| `OPEN` |
| `SUSPENDED` |
| `PENDINGCLOSURE` |
| `CLOSED` |

## Example

```python
from dnapaymentspartnerreportingsettlementapis.models.status import Status

status = Status.OPEN
```

