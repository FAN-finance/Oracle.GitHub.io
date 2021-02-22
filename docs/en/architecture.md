# Architecture

## Overview of Architecture

### Architecture

<img src="assets/architecture.png" alt="Overview of Architecture" style="zoom: 33%;" />

As shown above, the whole oracle system could be divided into four parts

- data source
- HTTP API
- node program
- oracle

### Distributed Data Mode

The demand for data consumption is relatively clear, such as "expecting to get the price of a certain digital asset", or demand for oracles that are less frequently updated, such as "expecting to get the benchmark mortgage interest rate of New York City". In order to make the data in the oracle more timely, accurate, and less biased, we adopt the **distributed data model** architecture to resolve the problem of price feeding mechanism.

The data is submitted to the "data aggregation contract" by multiple price feed node programs. When the 5/9 data aggregation conditions are met, the aggregation contract will eliminate the deviation of the data according to the **data aggregation model** algorithm and update it to the oracle data In contract.

Data consumers can directly read the data in the oracle through the **data request interface** (such as digital asset quotes, real estate mortgage interest rates, etc.).
[Distributed Data Mode]() describes how to aggregate data and how the consumer contract retrieves this data.

### Request Feedback Mode

The request for feedback is complicated for the request parameters, the result of the request is long-tailed data, and the resolution of using the distributed data mode to update the oracle regularly will undoubtedly waste huge gas expenses.

We adopted the **request feedback mode**. When the long-tail request arrives at the oracle, the oracle will issue a **data request** and send a **data request event**. The price-feeding node program will monitor the events emitted by the oracle, analyze the data requirements, start the workflow, and update the required data from the interface, database or other data sources to the **"data aggregation contract"**. The data aggregation contract will organize the data and update it to the oracle according to the **data aggregation model**. At the same time, according to the **callback contract address** and **callback function method** in the data request parameters, the data is returned to the **consumer contract**.

[Request Feedback Mode]() describes the on-chain architecture for requesting data from a single Oracle source.

## Distributed Data Model