---
layout: default
title: statcan-food-prices/
parent: Daikon REST API
nav_order: 4
---

Food prices tracked by Statcan under table pid `1810024501` accesible directly [here](https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=1810024501).

<style>
td, th {
   border: none!important;
}
</style>

### GET /statcan-food-prices/search ###
{: .d-inline-block }

Public
{: .label .label-green }

Returns a set of monthly food prices by calendar month, amount, unit, and region.

| Request Parameter      | Details |
| ----------- | ----------- |
| product_name      | The name of the product |
| amount            | The amount of the product. Products can be measured with different units and/or amounts. See that this is the case with onions since they can be purchased in bulk by the bag.  |
| unit              | The unit measuring the amount e.g. `kg`, `mL` |
| region_code     | (Optional) The two letter internationally standardized ISO-3166-2 region code. Returns the global averages for Canada if `null`. | 
| start_date      | The starting datestamp, the first day of the month, to observe the metrics. |
| end_date        | (Optional) The ending datestamp, the first day of the month, to observe the metrics on. The default is the current date. | 

| Response Key      | type | Definition |
| ----------- | ----------- |----------- |
| calendar_date      | date | The date the prices are observed on. |
| time_grain         | string | The time aggregation grain i.e. `monthly` |
| price              | numeric(32,2) | The average price collected from transactional data at the point of sales. |
| previous_price     | numeric(32,2) | The average price from the previous period with the same time granularity. |
| price_chng         | numeric(32,4) | The change in average price when compared to the previous period's value. Note, this is not what the government recognizes as a [pure](https://www.statcan.gc.ca/en/subjects-start/prices_and_price_indexes/consumer_price_indexes/faq) price change. 
| md5_key | char(32) | The generated primary key

#### Example Requests ####
`https://api.tm41m.com/statcan-food-prices/search?product_name=onions&amount=1&unit=kg&start_date=2020-01-01&region_code=ON`
{: .d-inline-block }
GET
{: .label .label-blue }

##### Response: #####

```json
{
    "amount":"1.00",
    "calendar_date":"2020-03-01",
    "currency":"CAD",
    "md5_key":"7ba60642cbd2b4ace3fe54492ae5bb1e",
    "previous_price":"4.41",
    "price":"4.32",
    "price_chng":"-0.0204",
    "product_name":"onions",
    "region_code":"ON",
    "time_grain":"monthly",
    "unit":"kg"
}
```
