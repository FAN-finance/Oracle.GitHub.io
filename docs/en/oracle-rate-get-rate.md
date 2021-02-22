# Obtaining Real Estate Mortgage Rate

This page will show how to get the latest real estate mortgage rate information. Need to find the latest quotation by city and mortgage type information.

You can check the mortgage interest rates for recently purchased real estate and refinancing info data.

## Sample Coding

### solidity

```javascript

pragma solidity =0.5.12;

interface getRateInterface {
    function getPurchase(uint, uint) public view returns (uint, uint);
    function getRefinance(uint, uint) public view returns (uint, uint);
}

contract RateConsumer {

    getRateInterface internal rateFeed;

    /**
     * Network: Kovan
     * Aggregator: rate && apr
     * Address: 0x2941B084601905f858730Ca2CD5e690191d10336
     */
    constructor() public {
        rateFeed = getRateInterface(0x2941B084601905f858730Ca2CD5e690191d10336);
    }

    /**
     * Returns the Purchase rate
     */
    function getPurchaseRate(uint city, uint product) public view returns (uint, uint) {
        (uint rate, uint apr) = rateFeed.getPurchase(city, product);
        return rate, apr;
    }
    
    /**
     * Returns the Refinance rate
     */
    function getRefinanceRate(uint city, uint product) public view returns (uint, uint) {
        (uint rate, uint apr) = rateFeed.getRefinance(city, product);
        return rate, apr;
    }
}
```

### javascript

```javascript
var Web3 = require('web3');

var rateContractAddr = '0x2941b084601905f858730ca2cd5e690191d10336'; // kovan测试网络合约地址
var web3 = new Web3(new Web3.providers.HttpProvider("https://kovan.infura.io/v3/<infura_project_id>"));

var rateContract = new web3.eth.Contract([{"inputs":[],"payable":false,"stateMutability":"nonpayable","type":"constructor"},{"anonymous":true,"inputs":[{"indexed":true,"internalType":"bytes4","name":"sig","type":"bytes4"},{"indexed":true,"internalType":"address","name":"usr","type":"address"},{"indexed":true,"internalType":"bytes32","name":"arg1","type":"bytes32"},{"indexed":true,"internalType":"bytes32","name":"arg2","type":"bytes32"},{"indexed":false,"internalType":"bytes","name":"data","type":"bytes"}],"name":"LogNote","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"uint256","name":"city","type":"uint256"},{"indexed":true,"internalType":"uint256","name":"product","type":"uint256"},{"indexed":false,"internalType":"uint256","name":"rate","type":"uint256"},{"indexed":false,"internalType":"uint256","name":"apr","type":"uint256"}],"name":"SetOracle","type":"event"},{"constant":false,"inputs":[{"internalType":"address","name":"guy","type":"address"}],"name":"deny","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"internalType":"uint256","name":"","type":"uint256"},{"internalType":"uint256","name":"","type":"uint256"}],"name":"getPurchase","outputs":[{"internalType":"uint256","name":"rate","type":"uint256"},{"internalType":"uint256","name":"apr","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[{"internalType":"uint256","name":"","type":"uint256"},{"internalType":"uint256","name":"","type":"uint256"}],"name":"getRefinance","outputs":[{"internalType":"uint256","name":"rate","type":"uint256"},{"internalType":"uint256","name":"apr","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"internalType":"address","name":"guy","type":"address"}],"name":"rely","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"internalType":"uint256","name":"city","type":"uint256"},{"internalType":"uint256","name":"product","type":"uint256"},{"internalType":"uint256","name":"_rate","type":"uint256"},{"internalType":"uint256","name":"_apr","type":"uint256"}],"name":"setPurchase","outputs":[{"internalType":"bool","name":"","type":"bool"}],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"internalType":"uint256","name":"city","type":"uint256"},{"internalType":"uint256","name":"product","type":"uint256"},{"internalType":"uint256","name":"_rate","type":"uint256"},{"internalType":"uint256","name":"_apr","type":"uint256"}],"name":"setRefinance","outputs":[{"internalType":"bool","name":"","type":"bool"}],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"internalType":"address","name":"","type":"address"}],"name":"wards","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"}], rateContractAddr);

var gasLimit = 300000;

var city = 1;
var product = 1;

rateContract.methods.getRefinance(city, product).call({},(err,res)=>console.log)
```

### Python

```python
web3 = Web3(Web3.HTTPProvider('https://kovan.infura.io/v3/<infura_project_id>'))
abi = '[{"inputs":[],"payable":false,"stateMutability":"nonpayable","type":"constructor"},{"anonymous":true,"inputs":[{"indexed":true,"internalType":"bytes4","name":"sig","type":"bytes4"},{"indexed":true,"internalType":"address","name":"usr","type":"address"},{"indexed":true,"internalType":"bytes32","name":"arg1","type":"bytes32"},{"indexed":true,"internalType":"bytes32","name":"arg2","type":"bytes32"},{"indexed":false,"internalType":"bytes","name":"data","type":"bytes"}],"name":"LogNote","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"uint256","name":"city","type":"uint256"},{"indexed":true,"internalType":"uint256","name":"product","type":"uint256"},{"indexed":false,"internalType":"uint256","name":"rate","type":"uint256"},{"indexed":false,"internalType":"uint256","name":"apr","type":"uint256"}],"name":"SetOracle","type":"event"},{"constant":false,"inputs":[{"internalType":"address","name":"guy","type":"address"}],"name":"deny","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"internalType":"uint256","name":"","type":"uint256"},{"internalType":"uint256","name":"","type":"uint256"}],"name":"getPurchase","outputs":[{"internalType":"uint256","name":"rate","type":"uint256"},{"internalType":"uint256","name":"apr","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[{"internalType":"uint256","name":"","type":"uint256"},{"internalType":"uint256","name":"","type":"uint256"}],"name":"getRefinance","outputs":[{"internalType":"uint256","name":"rate","type":"uint256"},{"internalType":"uint256","name":"apr","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"internalType":"address","name":"guy","type":"address"}],"name":"rely","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"internalType":"uint256","name":"city","type":"uint256"},{"internalType":"uint256","name":"product","type":"uint256"},{"internalType":"uint256","name":"_rate","type":"uint256"},{"internalType":"uint256","name":"_apr","type":"uint256"}],"name":"setPurchase","outputs":[{"internalType":"bool","name":"","type":"bool"}],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"internalType":"uint256","name":"city","type":"uint256"},{"internalType":"uint256","name":"product","type":"uint256"},{"internalType":"uint256","name":"_rate","type":"uint256"},{"internalType":"uint256","name":"_apr","type":"uint256"}],"name":"setRefinance","outputs":[{"internalType":"bool","name":"","type":"bool"}],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"internalType":"address","name":"","type":"address"}],"name":"wards","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"}]'
addr = '0x2941b084601905f858730ca2cd5e690191d10336'
contract = web3.eth.contract(address=addr, abi=abi)
rate, apr = contract.functions.getRefinance().call()
print(rate, apr)
```

