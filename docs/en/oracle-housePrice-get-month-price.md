# Obtaining Property Prices of Specific Months

## Overview

The oracle contract provides data on property prices of the top 10 American cities in the past year.

The data can be monthly as a unit, returning the housing price data for the past year at a time. It can also return the data of a certain month so far according to the month parameter.

The smart contract linking oracle machine can use the housePriceInterface interface to call the getMonth() method to obtain the actual house price data for the nth month so far.

```javascript
interface housePriceInterface {
    function getAll() external returns(uint[12] memory prices);
    function getMonth(uint month) external returns(uint);
}
```

## Sample Coding

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
        uint price = priceOracle.getMonth(1,1); // Suppose you want to get housing price information in New York, fill in the city parameter with 1
        return;
    }
}
```

#### Reference Parameters

| city | According City|
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

#### Supplemental Description

The pricing information type returned by the oracle is uint basis. Unable to save fractional part. Therefore, the pricing information saved in the oracle machine retains 3 decimals by default.

For example: The return value is 342455, and the corresponding price is $342.455

### javascript

In the Dapp back-end program, you can link the oracle contract through web3.js to read the contract data.

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

