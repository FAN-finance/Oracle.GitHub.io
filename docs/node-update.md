# 节点程序——喂价程序

## 概述

喂价节点程序主要负责周期性给**聚合器合约**上报最新数据信息，是预言机体系中的重要环节。

喂价节点程序在应用体系结构中属于 [分布式数据模式]() ，多个通过社区审核且获得授权的喂价节点程序，以星型拓扑结构的方式将本节点拥有的可靠数据更新至链上**数据聚合器合约**中，最终完成预言机的闭环。

目前可为以下预言机的聚合器合约提供数据支持服务：

- [数字资产价格预言机]()
- [美国十大城市房产抵押贷款利率预言机]()
- [美国十大城市房价变化数据预言机]()

## 安装

```shell
git clone http://62.234.169.68:3000/fan/rateOracle-node.git

cd rateOracle-node

npm install
```

## 使用

以 [美国十大城市房产抵押贷款利率预言机]() 为例，节点程序可以将美国十大城市中，不同年限的抵押利率更新至聚合器合约。

程序脚本以node.js为演示语言

```shell
node report.js
```

## 可自建资源

数据库：保存美国十大城市抵押贷款利率数据

关键字段：

| 字段          | 类型                                                         | 空   | 默认 | 注释                                                         |
| ------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| id *(主键)*   | bigint(20)                                                   | 否   |      |                                                              |
| Advertisers   | varchar(100)                                                 | 否   |      | 广告主                                                       |
| product_id    | smallint(20)                                                 | 否   |      | 产品id                                                       |
| product_name  | varchar(30)                                                  | 否   |      | 产品名                                                       |
| product_num   | smallint(10)                                                 | 否   |      | 产品搜索名：10,15,20,30,101,701,501,301                      |
| isFHA         | tinyint(10)                                                  | 否   | 0    |                                                              |
| loanType      | enum('purchase', 'refinance')                                | 否   |      | 例：`purchase`, `refinance`                                  |
| propertyType  | enum('SingleFamily', 'MultiFamily2Units', 'Condo4OrFewerStories', 'Townhouse', 'MultiFamily3Units', 'MultiFamily4Units') | 否   |      | 例：`SingleFamily`, `MultiFamily2Units`, `Condo4OrFewerStories`, `Townhouse`, `MultiFamily3Units`, `MultiFamily4Units` |
| propertyUse   | enum('PrimaryResidence', 'SecondaryOrVacation', 'InvestmentOrRental') | 否   |      | 例：`PrimaryResidence`, `SecondaryOrVacation`, `InvestmentOrRental` |
| propertyValue | varchar(20)                                                  | 否   |      | 例：`100000`, `200000`, `500000`, `1000000`, `2000000`       |
| zipCode       | varchar(20)                                                  | 否   |      | 邮编                                                         |
| fico          | enum('740', '730', '710', '690', '670', '650', '630', '600') | 否   |      | 例：`740`, `730`, `710`, `690`, `670`, `650`, `630`, `600`   |
| rate          | varchar(20)                                                  | 否   |      |                                                              |
| apr           | varchar(20)                                                  | 否   |      |                                                              |



## 公共资源

- 全美房产抵押贷款利率数据查询接口
- 全美房价变化历史及预期数据查询接口

