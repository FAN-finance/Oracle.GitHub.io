# Overview of the Architecture

The oracle provides off-chain data for smart contracts on-chain through two architectural models.

### Distributed Data Mode

<img src="assets/architecture-decentralized.png" alt="Overview of the Architecture" width="600" />

The demand for data consumption is relatively clear, such as "expecting to get the price of a certain digital asset", or demand for oracles that are less frequently updated, such as "expecting to get the benchmark mortgage interest rate of New York City". In order to make the data in the oracle more timely, accurate, and less biased, we adopt the **distributed data model** architecture to resolve the problem of price feeding mechanism.

The data is submitted to the "aggregation contract" by multiple price feed node programs. When the 5/9 data aggregation conditions are met, the aggregation contract will eliminate the deviation of the data according to the **data aggregation model** algorithm and update it to the oracle data In contract.

Data consumers can directly read the data in the oracle through the **data request interface** (such as digital asset quotes, real estate mortgage interest rates, etc.).

[Distributed Data Mode]() describes how to aggregate data and how the consumer contract retrieves this data.

### Request Feedback Mode

<img src="assets/architecture-request.png" alt="Overview of the Architecture" width="600" />

In view of the complex request parameters and long-tail type data of the request result, the scheme of using the distributed data mode to update the oracle regularly will undoubtedly waste huge gas costs.

We adopted **request feedback mode**. When the long-tail request reaches the oracle, the oracle will send a **data request** and send a **data request event**. The price-feeding node program will monitor the events emitted by the oracle, analyze the data requirements, start the workflow, and update the required data from the interface, database or other data sources to the **"data aggregation contract"**. The data aggregation contract will organize the data and update it to the oracle according to the **data aggregation model**. At the same time, according to the **callback contract address** and **callback function method** in the data request parameters, the data is returned to **searching contract**.

[Request Feedback Mode]() describes the on-chain architecture for requesting data from a single Oracle source.
