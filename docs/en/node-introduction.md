# Introduction

## Overview

The off-chain node program is an important link in the oracle system. It is a bridge between off-chain data and on-chain data communication.

In order to better serve the smart contract on the blockchain, the node program provides the following functions through different operating modes:

- Responding to requests: monitor contract data request events, identify data needs, start job tasks to process data and store the data in the oracle. Corresponding to [request feedback mode]()
- Regular price-feeding: Regularly update data to the aggregator contract to ensure the timeliness of the oracle data. Corresponds to [distributed data mode]()

## Public API

- stable data source: million-level database [Mortgage Rate Query Interface]() [National Housing Price Query Interface]()
- Safe price-feeding mechanism: [distributed data mode]() architecture

