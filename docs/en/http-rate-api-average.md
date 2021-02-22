# Searching API - Top 10 Major Cities' Average Rate

## Overview

API returns to Top 10 American Major Cities' Real Estate Mortgage Rate

Request method：get

## API Address

#### https://api.fan.finance/api/getZillowInfo

## return value

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