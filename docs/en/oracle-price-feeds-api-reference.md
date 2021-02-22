# Reference API

Reference API for getPriceInterface

## Function

| Name | Description                                                  |
| ---- | ------------------------------------------------------------ |
| peek | Returns the latest digital asset price, the returned bool value variable name has been correctly set price information |
| read | Returns the latest digital price, does not return the bool value, if the quotation has not been set, an error will be reported directly  |

### peek

Get the latest price and the basis for data reporting.

```
function peek() public view returns (uint, bool)
```

Return Values

- uint latest digital currency prices
- bool data has been configured and marked

### read

Read the latest price, if not set, directly rever off

```
function read() public view returns (uint)
```

Return Values

- uint latest digital currency prices