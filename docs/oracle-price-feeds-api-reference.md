# API Reference

API reference for getPriceInterface

## Function

| Name | Description                                                  |
| ---- | ------------------------------------------------------------ |
| peek | 返回最新数字资产价格，返回的bool值变量表名已经正确设定价格信息 |
| read | 返回最新数字价格，不返回bool值，如尚未设定报价，则直接报错   |

### peek

获取最新价格，及数据上报依据

```
function peek() public view returns (uint, bool)
```

Return Values

- uint 最新数字货币价格
- bool 数据已经被配置好标记

### read

读取最新价格，如果未设置则直接rever掉

```
function read() public view returns (uint)
```

Return Values

- uint 最新数字货币价格