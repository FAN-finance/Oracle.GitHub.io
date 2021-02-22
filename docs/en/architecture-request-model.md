# Request Feedback Mode

## Overview

For the complex request parameters and the request frequency long-tail type data, we adopted the **request feedback mode**.

When the long tail request arrives at the oracle, the oracle will issue a **data request** and send a **data request event**.

The price-feeding node program will listen to the events emitted by the oracle, analyze the data requirements, start the work process, and update the required data from the interface, database or other data sources to the **"aggregator contract"**.

**aggregator contract** will organize the data and update it to the oracle according to the **data aggregation model**. At the same time, according to the **callback contract address** and **callback function method** in the data request parameters, the data is returned to the **searching contract**.

## Client Contract

The client contract is a smart contract (parent contract) that can be inherited. The searching contract inherits the client contract to obtain the data in the oracle contract.

After the searching contract inherits the client contract, it can directly call the preset methods of the contract to initiate data requests to the oracle contract.

The request sent by the client includes the desired ** oracle contract address**, **request item**, and **callback function**, etc., all the data required for a successful cycle.

The request will be sent to the oracle contract.

## Oracle Contract

The oracle contract accepts the latest data updated by the aggregator contract.

The oracle also accepts requests from the client contract.

In the process of processing the request, a **data request event** will be emitted. After a **node program** under the chain listens to the event, it publishes the required data to the **aggregation contract**. The final data is stored in the **oracle contract**, and the **callback method** in the request is executed to continue to complete the established functions of the original DApp contract.

## Off-chain Oracle Nodes

Nodes have two main functions:

- monitor data request events
- price feed of aggregation contract

After the oracle node program monitors the **data request event**, it obtains the latest data from the database or a third-party interface service, and stores it in the oracle contract corresponding to the request after verification.

The node program can provide services for multiple data oracles at the same time.