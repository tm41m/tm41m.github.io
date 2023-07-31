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

Private Beta
{: .label .label-purple }

Returns a set of product metrics given the `date` and `product_id`.

| Request Parameter      | Details |
| ----------- | ----------- |
| product_id      | The product id |
| date      | (Optional) The date to observe the metrics on. Default is the current calendar date|

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
`https://api.tm41m.io/v1/product-metrics/search?product_id=1&date=2023%2D06%2D11`
{: .d-inline-block }
GET
{: .label .label-blue }

##### Response: #####

```json
{
    "calendar_date": "2023-06-11",
    "product_id": 1,
    "currency": "CAD",
    "unit": "/ 1kg",
    "avg_price": 6.0424,
    "avg_price_chng": 0.0094,
    "product_listings": 1039,
    "product_listings_rtn": 876
}
```
