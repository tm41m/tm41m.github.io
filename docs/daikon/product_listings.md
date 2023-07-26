---
layout: default
title: product-listings/
parent: Daikon REST API
nav_order: 2
---

A listed product is a purchasable item that can be discovered at the retailer's store.

<style>
td, th {
   border: none!important;
}
</style>

### GET /product-listings/:id ###
{: .d-inline-block }

Private Beta
{: .label .label-purple }

Returns a single product listing.

| Request Parameter      | Details |
| ----------- | ----------- |
| :id      | The product listing UUID |


| Response Key      | type | Definition |
| ----------- | ----------- |----------- |
| id      | UUID |The product listing UUID |
| product_name      | string | The name of the product |
| product_id      | int | The product id |
| store_id      | int | The store id |
| price      | numeric(32,2) | The price of the listing at the moment it was captured (i.e. updated_at) |
| currency      | string | The three letter code for the price's currency |
| unit      | string | The unit of the listing e.g. ('/ 1kg', '/ lbs' etc.) |
| updated_at      | timestamp | The last time the product listing was updated |

#### Example Requests ####
`https://api.tm41m.io/v1/product-listings/:id/f295b713-1d6a-43fd-910d-fb35414bf58a`
{: .d-inline-block }
GET
{: .label .label-blue }

```json
{
    "id": "f295b713-1d6a-43fd-910d-fb35414bf58a",
    "product_name": "White Onion",
    "product_id": 1,
    "store_id": 34,
    "price": 5.94,
    "currency": "CAD",
    "unit": "/ 1kg",
    "updated_at": "2021-05-24 13:42:49.997292"
}
```
