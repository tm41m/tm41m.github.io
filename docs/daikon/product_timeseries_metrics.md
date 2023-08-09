---
layout: default
title: product-metrics/
parent: Daikon REST API
nav_order: 3
---

The set of product metrics aggregated from listings.

<style>
td, th {
   border: none!important;
}
</style>

### GET /product-metrics/search ###
{: .d-inline-block }

Public
{: .label .label-green }

Returns a set of product metrics given the `product_id`, `region_code`, `start_date` and `end_date`.

| Request Parameter      | Details |
| ----------- | ----------- |
| product_id      | The product id |
| region_code     | (Optional) The two letter internationally standardized ISO-3166-2 region code. Returns the global averages for Canada if `null`. | 
| start_date      | The starting datestamp to observe the metrics on. |
| end_date        | (Optional) The ending datestamp to observe the metrics on. The default is the current date. | 

| Response Key      | type | Definition |
| ----------- | ----------- |----------- |
| calendar_date      | date |The date the metric is observed on. |
| product_id      | int | The product id |
| currency      | string | The three letter code for the price's currency |
| unit      | string | The unit of the listing e.g. (`'/ 1kg'`, `'/ lbs'` etc.) |
| avg_price      | numeric(32,4) | The average price given all the sampled product listings on the date observed |
| avg_price_chng      | numeric(32,4) | The average price change from the previous period where the sample is observed iff it has price information in both periods |
| product_listings      | int | The number of product listings on the date observed |
| product_listings_rtn | int | The number of product listings retained from the previous period i.e. the listing was extracted both in the previous period and the current one |

#### Example Requests ####
`https://api.tm41m.com/product-metrics/search?product_id=1&region_code=ON&start_date=2023%2D06%2D11&end_date=2023%2D06%2D11`
{: .d-inline-block }
GET
{: .label .label-blue }

##### Response: #####

```json
{
    "calendar_date": "2023-06-11",
    "product_id": 1,
    "region_code": "ON",
    "currency": "CAD",
    "unit": "/ 1kg",
    "avg_price": 6.0424,
    "avg_price_chng": 0.0094,
    "product_listings": 1039,
    "product_listings_rtn": 876
}
```
