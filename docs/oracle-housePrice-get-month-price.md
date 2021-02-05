# 获取某月房价数据

## 概述

预言机合约提供美国十大城市近一年房产价格数据。

预言机数据来源于百万级持续更新的数据库，由预言机喂价节点通过分布式数据模式将处理过的数据上报到数据聚合合约。

智能合约链接预言机可使用housePriceInterface接口，调用getMonth()方法，获取到距今为止第n个月的房价实际数据。

例如：假设现在是3月，month参数填写1，则获取到2月份数据。填写2，则获取到1月份数据。

```javascript
interface housePriceInterface {
    function getAll() external returns(uint[12] memory prices);
    function getMonth(uint month) external returns(uint);
}
```

## 代码示例

### solidity

```
pragma solidity ^0.6.7;

interface housePriceInterface {
    function getAll(uint city) external returns(uint[12] memory prices);
    function getMonth(uint city, uint month) external returns(uint);
}

contract PriceConsumer {

    housePriceInterface internal priceFeed;

    /**
     * Network: Kovan
     * Aggregator: housePrice
     * Address: 0xa367264751eE05a18EA46eAfD485DbCE253c0997
     */
    constructor() public {
        priceOracle = getAll(0xa367264751eE05a18EA46eAfD485DbCE253c0997);
    }

    /**
     * Returns all the price
     */
    function getLatestPrice() public view returns (uint price) {
        uint price = priceOracle.getMonth(1,1); // 假设希望得到New York的房价信息，city参数填1
        return;
    }
}
```

#### 参数对照表

| city | 对应城市      |
| ---- | ------------- |
| 1    | New York      |
| 2    | Los Angeles   |
| 3    | Chicago       |
| 4    | Houston       |
| 5    | Philadelphia  |
| 6    | Detroit       |
| 7    | San Francisco |
| 8    | Boston        |
| 9    | Pittsburgh    |
| 10   | Atlanta       |

#### 补充说明

预言机返回的price信息类型为uint类型。无法保存小数部分。因此预言机中保存的价格信息，默认保留3位小数位。

例：返回值为342455，则对应price为$342.455

### javascript

Dapp后端程序中，可以通过web3.js来链接Oracle合约，读取合约数据。

```javascript
const web3 = new Web3("https://kovan.infura.io/v3/<infura_project_id>");
const housePriceInterfaceABI = [{"inputs":[],"payable":false,"stateMutability":"nonpayable","type":"constructor"},{"anonymous":true,"inputs":[{"indexed":true,"internalType":"bytes4","name":"sig","type":"bytes4"},{"indexed":true,"internalType":"address","name":"usr","type":"address"},{"indexed":true,"internalType":"bytes32","name":"arg1","type":"bytes32"},{"indexed":true,"internalType":"bytes32","name":"arg2","type":"bytes32"},{"indexed":false,"internalType":"bytes","name":"data","type":"bytes"}],"name":"LogNote","type":"event"},{"constant":false,"inputs":[{"internalType":"address","name":"guy","type":"address"}],"name":"deny","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"peek","outputs":[{"internalType":"uint256","name":"","type":"uint256"},{"internalType":"bool","name":"","type":"bool"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"internalType":"uint256","name":"wut","type":"uint256"}],"name":"poke","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"read","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"internalType":"address","name":"guy","type":"address"}],"name":"rely","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[],"name":"void","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"internalType":"address","name":"","type":"address"}],"name":"wards","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"}];
const addr = "0xa367264751eE05a18EA46eAfD485DbCE253c0997";
const priceOracle = new web3.eth.Contract(housePriceInterfaceABI, addr);
priceOracle.methods.getMonth(1,1).call()
    .then((price) => {
        // Do something with roundData
        console.log("Latest Round Data", price)
    });
```

### python

```python
web3 = Web3(Web3.HTTPProvider('https://kovan.infura.io/v3/<infura_project_id>'))
abi = '[{"inputs":[],"payable":false,"stateMutability":"nonpayable","type":"constructor"},{"anonymous":true,"inputs":[{"indexed":true,"internalType":"bytes4","name":"sig","type":"bytes4"},{"indexed":true,"internalType":"address","name":"usr","type":"address"},{"indexed":true,"internalType":"bytes32","name":"arg1","type":"bytes32"},{"indexed":true,"internalType":"bytes32","name":"arg2","type":"bytes32"},{"indexed":false,"internalType":"bytes","name":"data","type":"bytes"}],"name":"LogNote","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"uint256","name":"city","type":"uint256"},{"indexed":true,"internalType":"uint256","name":"product","type":"uint256"},{"indexed":false,"internalType":"uint256","name":"rate","type":"uint256"},{"indexed":false,"internalType":"uint256","name":"apr","type":"uint256"}],"name":"SetOracle","type":"event"},{"constant":false,"inputs":[{"internalType":"address","name":"guy","type":"address"}],"name":"deny","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"internalType":"uint256","name":"","type":"uint256"},{"internalType":"uint256","name":"","type":"uint256"}],"name":"getPurchase","outputs":[{"internalType":"uint256","name":"rate","type":"uint256"},{"internalType":"uint256","name":"apr","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[{"internalType":"uint256","name":"","type":"uint256"},{"internalType":"uint256","name":"","type":"uint256"}],"name":"getRefinance","outputs":[{"internalType":"uint256","name":"rate","type":"uint256"},{"internalType":"uint256","name":"apr","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"internalType":"address","name":"guy","type":"address"}],"name":"rely","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"internalType":"uint256","name":"city","type":"uint256"},{"internalType":"uint256","name":"product","type":"uint256"},{"internalType":"uint256","name":"_rate","type":"uint256"},{"internalType":"uint256","name":"_apr","type":"uint256"}],"name":"setPurchase","outputs":[{"internalType":"bool","name":"","type":"bool"}],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"internalType":"uint256","name":"city","type":"uint256"},{"internalType":"uint256","name":"product","type":"uint256"},{"internalType":"uint256","name":"_rate","type":"uint256"},{"internalType":"uint256","name":"_apr","type":"uint256"}],"name":"setRefinance","outputs":[{"internalType":"bool","name":"","type":"bool"}],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"internalType":"address","name":"","type":"address"}],"name":"wards","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"}]'
addr = '0x2941b084601905f858730ca2cd5e690191d10336'
contract = web3.eth.contract(address=addr, abi=abi)
price = contract.functions.getMonth(1,1).call()
print(price)
```

