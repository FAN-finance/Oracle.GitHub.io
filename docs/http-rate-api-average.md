# 美国十大城市房产抵押贷款平均利率查询接口

## 概述

接口返回美国排名前十的城市房产抵押利率。

请求方式：get

## 接口地址

#### https://api.fan.finance/api/getZillowInfo

## 返回值

```json
{
    "code":0,
    "msg":"success",
    "data":[
        {
            "city":"Philadelphia",
            "product":[
                {
                    "name":"10/1 ARM refinance",
                    "interestRate":"3.305",
                    "APR":"3.231"
                },
                {
                    "name":"15 year fixed refinance",
                    "interestRate":"2.432",
                    "APR":"2.695"
                },
                {
                    "name":"15 year jumbo refinance",
                    "interestRate":"2.644",
                    "APR":"2.845"
                }
            ]
        }
    ]
}
```