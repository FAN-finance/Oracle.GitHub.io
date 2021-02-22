# Node Program —— Price-Feeding

## Overview

The price-feeding node program is mainly responsible for periodically reporting the latest data information to the **aggregator contract**, which is an important link in the oracle system.

The price-feeding node program belongs to the [distributed data mode]() in the application architecture. Multiple price-feeding node programs that have passed the community audit and are authorized to update the reliable data owned by the node to the chain in a star topology In the **data aggregator contract**, the closed loop of the oracle is finally completed.

Currently, data support services can be provided for the following oracle aggregator contracts:

- [Oracle of Digital Asset Pricings and Predictions]()
- [Oracle of Top 10 American Major Cities' Real Estate Mortgage Rate]()
- [Oracle of Top 10 American Major Cities' Real Estate Pricing Change]()

## Instalment

```shell
git clone http://62.234.169.68:3000/fan/rateOracle-node.git

cd rateOracle-node

npm install
```

## Application

Takee [Oracle of Top 10 American Major Cities' Real Estate Mortgage Rate]() as an example，the node program can update the mortgage interest rates of different years in the ten largest cities in the United States to the aggregator contract.

The program script uses node.js as the demonstration language.

```shell
node report.js
```

## Enable Self-built Resources

Database: storing the Top 10 American major cities' real Estate mortgage rate info data.

Major Parameters

| Parameter     | Type                                                        | False| Default |Note| 
| ------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| id *(主键)*   | bigint(20)                                                   | False |      |                                                              |
| Advertisers   | varchar(100)                                                 | False|      | advertisers                                                       |
| product_id    | smallint(20)                                                 | False|      | mortgage type id                                                       |
| product_name  | varchar(30)                                                  | False|      | mortgage type|
| product_num   | smallint(10)                                                 |False |      | mortgage type: 10,15,20,30,101,701,501,301                      |
| isFHA         | tinyint(10)                                                  | False | 0    |                                                              |
| loanType      | enum('purchase', 'refinance')                                | False |      | e.g.`purchase`, `refinance`                                  |
| propertyType  | enum('SingleFamily', 'MultiFamily2Units', 'Condo4OrFewerStories', 'Townhouse', 'MultiFamily3Units', 'MultiFamily4Units') | 否   |      | 例：`SingleFamily`, `MultiFamily2Units`, `Condo4OrFewerStories`, `Townhouse`, `MultiFamily3Units`, `MultiFamily4Units` |
| propertyUse   | enum('PrimaryResidence', 'SecondaryOrVacation', 'InvestmentOrRental') |False|      | 例：`PrimaryResidence`, `SecondaryOrVacation`, `InvestmentOrRental` |
| propertyValue | varchar(20)                                                  |False |      | e.g.`100000`, `200000`, `500000`, `1000000`, `2000000`       |
| zipCode       | varchar(20)                                                  |False |      | postcode                                                         |
| fico          | enum('740', '730', '710', '690', '670', '650', '630', '600') |False |      | e.g`740`, `730`, `710`, `690`, `670`, `650`, `630`, `600`   |
| rate          | varchar(20)                                                  |False |      |                                                              |
| apr           | varchar(20)                                                  | False|      |                                                              |



## Public Resource

- Data Index/API of ALl American Real Estate Mortgage Loan Rate
- Data Index/API of All American Real Estate Historical and Predicted Pricings

