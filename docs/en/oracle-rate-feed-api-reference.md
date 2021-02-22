# Reference API

Reference API for getRateInterface

## Function

| Name         | Description                    |
| ------------ | ------------------------------ |
| getPurchase  | Return to mortgage interest rate information for recently purchased properties   |
| getRefinance | Return to refinancing property mortgage interest rate information |

### getPurchase

Return to mortgage interest rate information for newly purchased properties

```javascript
function getPurchase(uint city, uint product) public view returns(uint rate, uint apr)
```

Parameters

- city ：searching cities
- product ：searching mortgage rate

Return Values

- rate ：benchmark rate
- apr ： average rate

### getRefinance

Return to refinancing property mortgage interest rate information

```javascript
function getRefinance(uint city, uint product) public view returns(uint rate, uint apr)
```

Parameters

- city ：searching cities
- product ：searching mortgage rate

Return Values

- rate ：benchmark rate
- apr ： average rate

## Params

### city

| city          | value |
| ------------- | ----- |
| New York      | 1     |
| Los Angeles   | 2     |
| Chicago       | 3     |
| Houston       | 4     |
| Philadelphia  | 5     |
| Detroit       | 6     |
| San Francisco | 7     |
| Boston        | 8     |
| Pittsburgh    | 9     |
| Atlanta       | 10    |

### mortgage type

| mortgage type           | value |
| ----------------------- | ----- |
| 15 year fixed refinance | 1     |
| 15 year jumbo refinance | 2     |
| 10/1 ARM refinance      | 3     |