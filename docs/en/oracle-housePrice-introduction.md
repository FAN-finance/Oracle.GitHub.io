# Introduction

## Overview

The oracle contract provides data on property prices of the top 10 American cities in the past year.

The data can be monthly as a unit, returning the housing price data for the past year at a time. It can also return the data of a certain month so far according to the month parameter.

- obtaining all pricing data
- obtaining all pricing data for specific month

## Applicable Cities

| No.  | Cities        |
| ---- | ------------- |
| 1    | New York      |
| 2    | Los Angeles   |
| 3    | Chicago       |
| 4    | Houston       |
| 5    | Philadelphia  |
| 6    | Detroit       |
| 7    | San Francisco |
| 8    | Boston        |
| 9    | Pittsburgh    |
| 10   | Atlanta       |

## Tech Support

- million-level database: continuously updating house priceing information in various districts of cities in the United States
- safe and stable price-feeding mechanism：[distributed data model]() architecture 
- Same as the algorithms in [HTTP API]() searching service：ensure that there is no deviation between the pricing information and the content of the oracle.