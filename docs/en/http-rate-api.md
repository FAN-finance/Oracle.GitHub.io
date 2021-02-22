# Data Index/API of ALl American Real Estate Mortgage Loan Rate

## Overview

In addition to querying through the web site, the real estate mortgage interest rate information can also be queried through HTTP API.

Request method：get

## API address

#### https://api.fan.finance/api/getRate

```html
<!-- 全URL -->

https://api.fan.finance/api/getRate?limit=10&page=1&loanType=purchase&propertyValue=100000&propertyType=SingleFamily&propertyUse=PrimaryResidence&cashOutAmount=0&zipCode=90210&loanAmount=80,000&fico=740&points=all&product_name=30&firstTimeHomebuyer=false
```

## Parameter Details

| No   | key           | type    | description                                                  |
| ---- | ------------- | ------- | ------------------------------------------------------------ |
| 1    | limit         | number  | Page Type                                                    |
| 2    | page          | number  | Page                                                         |
| 3    | loanType      | string  | Mortgage Type                                                |
| 4    | propertyValue | number  | e.g.`100000`, `200000`, `500000`, `1000000`, `2000000`       |
| 5    | propertyType  | enum    | e.g. `SingleFamily`, `MultiFamily2Units`, `Condo4OrFewerStories`, `Townhouse`, `MultiFamily3Units`, `MultiFamily4Units` |
| 6    | propertyUse   | enum    | e.g. `PrimaryResidence`, `SecondaryOrVacation`, `InvestmentOrRental` |
| 8    | zipCode       | varchar | Postcode                                                        |
| 9    | loanAmount    | enum    | e.g. `purchase`, `refinance`                                  |
| 10   | creditScore   | enum    | e.g.`740`, `730`, `710`, `690`, `670`, `650`, `630`, `600`   |

## return value

```json
{
    "code":0,
    "msg":"success",
    "data":{
        "page":"1",
        "limit":"10",
        "total":"5",
        "content":[
            "{"id":"6d0e2c46-608e-4afe-9209-311d45dfa1c3","advertiser":{"city":"","description":"","email":"","features":[],"hoursOfOperation":"","id":0,"isFeatured":false,"isFuse":false,"logo":{},"name":"LincolnWay Community Bank","nmlsLicense":"","note":{"isHyperLinkable":false,"text":""},"phone":"","reviews":{"averageRating":0,"count":0},"score":0,"seoName":"","specials":[],"state":"","stateLicense":"","surveyInstitutionId":0},"apr":2.856,"date":"2021-01-06T08:29:31.626Z","estimatedPayment":326.59,"fees":[{"description":"Upfront Fees","amount":1085,"HUDLine":0,"required":false}],"fiveYearCost":10392.34,"isPaid":false,"lockDays":30,"source":"mortgage-portal","product":{"term":360,"size":"conforming","isInterestOnly":false,"type":"fixed","name":"30 year fixed","isFHA":false,"id":166,"purpose":"purchase","pointsBand":"Zero","isVA":false,"fixedMonths":360,"points":0},"rate":2.75,"armDetails":null,"type":"editorial","upFrontCosts":1085,"displayTargets":["desktopRateTable","mobileRateTable"],"tags":[],"phone":"","isFeatured":false}",
            "{"id":"aaba55c0-6b7d-4f9a-8c23-cde709be9328","advertiser":{"city":"","description":"","email":"","features":[],"hoursOfOperation":"","id":0,"isFeatured":false,"isFuse":false,"logo":{},"name":"Schools First FCU","nmlsLicense":"","note":{"isHyperLinkable":false,"text":""},"phone":"","reviews":{"averageRating":0,"count":0},"score":0,"seoName":"","specials":[],"state":"","stateLicense":"","surveyInstitutionId":0},"apr":2.972,"date":"2021-01-06T08:29:31.626Z","estimatedPayment":331.91,"fees":[{"description":"Upfront Fees","amount":995,"HUDLine":0,"required":false}],"fiveYearCost":10876.79,"isPaid":false,"lockDays":30,"source":"mortgage-portal","product":{"term":360,"size":"conforming","isInterestOnly":false,"type":"fixed","name":"30 year fixed","isFHA":false,"id":166,"purpose":"purchase","pointsBand":"Zero","isVA":false,"fixedMonths":360,"points":0},"rate":2.875,"armDetails":null,"type":"editorial","upFrontCosts":995,"displayTargets":["desktopRateTable","mobileRateTable"],"tags":[],"phone":"","isFeatured":false}",
            "{"id":"ae3f736d-ef41-41f9-a044-c126610f3272","advertiser":{"city":"","description":"","email":"","features":[],"hoursOfOperation":"","id":0,"isFeatured":false,"isFuse":false,"logo":{},"name":"Star One Credit Union","nmlsLicense":"","note":{"isHyperLinkable":false,"text":""},"phone":"","reviews":{"averageRating":0,"count":0},"score":0,"seoName":"","specials":[],"state":"","stateLicense":"","surveyInstitutionId":0},"apr":2.635,"date":"2021-01-06T08:29:31.626Z","estimatedPayment":321.32,"fees":[{"description":"Upfront Fees","amount":105,"HUDLine":0,"required":false}],"fiveYearCost":9908.72,"isPaid":false,"lockDays":30,"source":"mortgage-portal","product":{"term":360,"size":"conforming","isInterestOnly":false,"type":"fixed","name":"30 year fixed","isFHA":false,"id":166,"purpose":"purchase","pointsBand":"Zero","isVA":false,"fixedMonths":360,"points":0},"rate":2.625,"armDetails":null,"type":"editorial","upFrontCosts":105,"displayTargets":["desktopRateTable","mobileRateTable"],"tags":[],"phone":"","isFeatured":false}",
            "{"id":"059ff0dd-4c1c-4792-ac55-81e84d3a5efd","advertiser":{"city":"","description":"","email":"","features":[],"hoursOfOperation":"","id":0,"isFeatured":false,"isFuse":false,"logo":{},"name":"BBVA","nmlsLicense":"","note":{"isHyperLinkable":false,"text":""},"phone":"","reviews":{"averageRating":0,"count":0},"score":0,"seoName":"","specials":[],"state":"","stateLicense":"","surveyInstitutionId":0},"apr":2.83,"date":"2021-01-06T08:29:31.626Z","estimatedPayment":321.32,"fees":[{"description":"Discount Points","amount":1000,"HUDLine":841,"required":true}],"fiveYearCost":10908.72,"isPaid":false,"lockDays":30,"source":"mortgage-portal","product":{"term":360,"size":"conforming","isInterestOnly":false,"type":"fixed","name":"30 year fixed","isFHA":false,"id":168,"purpose":"purchase","pointsBand":"OneToTwo","isVA":false,"fixedMonths":360,"points":1.25},"rate":2.625,"armDetails":null,"type":"editorial","upFrontCosts":1000,"displayTargets":["desktopRateTable","mobileRateTable"],"tags":[],"phone":"","isFeatured":false}",
            "{"id":"f997fa81-7341-4504-b85a-0ea3eda660f6","advertiser":{"city":"","description":"","email":"","features":[],"hoursOfOperation":"","id":0,"isFeatured":false,"isFuse":false,"logo":{},"name":"First Citizens Bank","nmlsLicense":"","note":{"isHyperLinkable":false,"text":""},"phone":"","reviews":{"averageRating":0,"count":0},"score":0,"seoName":"","specials":[],"state":"","stateLicense":"","surveyInstitutionId":0},"apr":2.706,"date":"2021-01-06T08:29:31.626Z","estimatedPayment":321.32,"fees":[{"description":"Upfront Fees","amount":842,"HUDLine":0,"required":false}],"fiveYearCost":9908.72,"isPaid":false,"lockDays":30,"source":"mortgage-portal","product":{"term":360,"size":"conforming","isInterestOnly":false,"type":"fixed","name":"30 year fixed","isFHA":false,"id":166,"purpose":"purchase","pointsBand":"Zero","isVA":false,"fixedMonths":360,"points":0},"rate":2.625,"armDetails":null,"type":"editorial","upFrontCosts":842,"displayTargets":["desktopRateTable","mobileRateTable"],"tags":[],"phone":"","isFeatured":false}"
        ]
    }
}
```