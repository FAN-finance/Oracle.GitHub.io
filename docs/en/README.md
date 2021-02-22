# To Start

## Overview

FAN Oracle will bring more off-chain data to your smart contract.

The oracle is served as a transfer station that connects the internal and external data of the blockchain. We synchronize the external data of the blockchain to the smart contract of the block in a timely manner, and the "observers" who supply the demand can obtain it directly.

**Overall System Architecture Diagram**

<img src="assets/architecture2.png" alt="Overview of Architecture Diagram" width="600" />

As shown in the figure, the whole system is divided into four parts:

- Data Collection: as shown in the orange part. The continuous aggregation of digital asset price information, exchange rate information, and housing price information is the cornerstone of the oracle system.
- HTTP API: as shown in the green part. Provide external query services in the form of back-end interfaces. On the one hand, it supports the project to provide query services in the form of web pages, and on the other hand, it serves as a public interface to allow third parties to call and query.
- Price-feeding Node Program: as shown in the gray part. The node program transfers the data required by the **searching contract** to the chain through the oracle.
- Oracle: the blue part of the picture. The core components of the system provide off-chain data to smart contracts that require oracle services in two modes.

## On-chain Oracle service

- real-time quotation information of multiple digital assets

- top 10 Major American Cities' Real Estate Mortgage Rate

- pricings and Fluctuation of Top 10 Major American Cities' Real Estate

## Off-chain Data Searching Service and Data

- query service of all American Cities' Real Estate Mortgage Rate
- searching  API of all American Cities' Real Estate Mortgage Rate
- line charts of all American Cities' Real Estate Price Fluctuations
- searching  API of all American Cities' Real Estate Price Fluctuations