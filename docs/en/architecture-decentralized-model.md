# Distributed Data Mode

## Overview

The demand for data consumption is relatively clear, such as "expecting to get the price of a certain digital asset", or demand for oracles that are less frequently updated, such as "expecting to get the benchmark mortgage interest rate of New York City". In order to make the data in the oracle more timely, accurate, and less biased, we adopt the **distributed data model** architecture to resolve the problem of price feeding mechanism.

<img src="assets/architecture-decentralized.png" alt="Overview of the Architecture" width="600" />

This page utilizes the sample cases listed in the “Obtaining Latest Pricing” Chapter to analyze distributed data mode

### Price Aggregator

In the picture, Oracle Setter is the price aggregator contract. Each latest **digital asset quotation data** is composed of multiple **price feed nodes** by sending **data** to **price aggregator contract**, and by finishing contract processing, updates to**Oracle contract**.

<img src="assets/architecture-decentralized2.png" alt="Overview of the Architecture" width="600" />

### Sharing Data Resource

Each price source is established and funded by a user community that relies on precision, with the according price data updated to the smart contract in a timely manner. As more users rely on or provide price source data information, the quality of data becomes more accurate and timely. Every kind of price data information needs the joint maintenance of the community.

### Distributed Oracle of the Price-feeding Node Network

Each **price source** is updated by a decentralized oracle node network. The release of price data does not currently have any obvious benefits, but accurate price data is essential for community users to analyze, vote and decide to pass the proposal of including a certain digital asset. Therefore, a considerable number of public welfare nodes (price-feeding nodes) have emerged. All price-feeding nodes obtain the permission to publish quotation data after passing the review of the community's operating qualifications and maintenance capabilities. Each **price source** has a different number of price feed nodes. For example, the **price source** of OST has 9 price-feeding nodes.

In order to update, the **price aggregator contract** must receive a response from the minimum number of price feeds, for instance, 5/9. Otherwise, the latest quotation will not be processed and updated to **oracle contract**.

The **price aggregator contract** is responsible for processing the collected price information according to the **aggregation model**. Finally, the quote information with the smallest deviation is updated to the **oracle contract**.

### Aggregation Model

When the aggregator contract receives the quote data, it will mark the account address' information of the current round of quoted nodes. Each price-feeding node is only allowed to report data once in each round until the aggregator contract collects enough quote information for processing.

The price-feeding nodes are in a competitive relationship. The earlier the price feeds the node, its data can participate in this round of **data processing and update**.

For example: OST has 9 price-feeding nodes, as long as 5 of them submit the latest digital currency quotation to the **aggregator contract**, the **price update mechanism** will be triggered, and obviously unreasonable quotations will be removed, and update the latest quotation data to **oracle contract**.

## Overview of the Smart Contract

The use of predictive opportunities in the distributed data model involves the following three smart contracts:

### Searching Contract

A searching contract can be any smart contract that wants to obtain digital asset price information through the ** oracle contract**.

The searching contract only needs to simply reference the **oracle interface** and call the data acquisition method to obtain the latest digital asset price information.

```
interface getPriceInterface {
    function peek() public view returns (uint, bool);
    function read() public view returns (uint)
}

lastestPrice = getPriceInterface(addr).read();
```

### Oracle Contract

The oracle contract is used to store the data required by the data observer needed on the blockchain. Only the `aggregator contract` of the `authorized` can update the quote information. This process is defined as **"feeding price"**.

### Aggregation Contract

The aggregator is a smart contract that receives regular price updates from multiple oracles. The authorized price-feeding node can submit the latest digital asset price to this contract.

When the aggregator contract receives the quote data, it will mark the information of account address of the current round of quoted nodes.

Each price feeder node is only allowed to report data once in each round until the aggregator contract collects enough quote information for processing.

Could learn [Obtaining Lastest Pricing](../Obtaining Lastest Pricing/get-the-lastest-price.html) from instruction to learn how to quickly get the latest digital asset quotes in this tutorial.