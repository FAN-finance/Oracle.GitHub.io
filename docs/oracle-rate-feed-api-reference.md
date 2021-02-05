# API Reference

API reference for getRateInterface

## Function

| Name         | Description                    |
| ------------ | ------------------------------ |
| getPurchase  | 返回新购房产抵押贷款利率信息   |
| getRefinance | 返回再融资房产抵押贷款利率信息 |

### getPurchase

返回新购房产抵押贷款利率信息

```javascript
function getPurchase(uint city, uint product) public view returns(uint rate, uint apr)
```

Parameters

- city ：待查城市
- product ：待查产品

Return Values

- rate ：基准利率
- apr ： 平均利率

### getRefinance

返回再融资房产抵押贷款利率信息

```javascript
function getRefinance(uint city, uint product) public view returns(uint rate, uint apr)
```

Parameters

- city ：待查城市
- product ：待查产品

Return Values

- rate ：基准利率
- apr ： 平均利率

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

### product

| product                 | value |
| ----------------------- | ----- |
| 15 year fixed refinance | 1     |
| 15 year jumbo refinance | 2     |
| 10/1 ARM refinance      | 3     |