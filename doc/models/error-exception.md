
# Error Exception

Generic error body returned for some failed requests.

*This model accepts additional fields of type Any.*

## Structure

`ErrorException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `code` | `int` | Optional | - |
| `message` | `str` | Optional | - |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
try:
    # make the API call
except ErrorException as e:
    print(e)
except ApiException as e:
    print(e)
```

