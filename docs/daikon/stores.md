---
layout: default
title: stores/
parent: Daikon REST API
nav_order: 1
---

A store is an establishment with a region code (i.e. zip code, postal code) mapping to a retailer. 

<style>
td, th {
   border: none!important;
}
</style>

### GET /stores/:id ###
{: .d-inline-block }

Private Beta
{: .label .label-purple }

Returns a single store.

| Request Parameter      | Details |
| ----------- | ----------- |
| :id      | The store UUID |


| Response Key      | type | Definition |
| ----------- | ----------- |----------- |
| id      | UUID |The store UUID |
| retailer_name      | string | The name of the retailer |
| parent_retailer_name      | string | The name of the parent retailer |
| store_address      | json| A `json` with elements pertaining to the store's location |
| updated_at      | timestamp | The last time the store was updated |

#### Example Requests ####
`https://api.tm41m.com/stores/:id/f295b713-1d6a-43fd-910d-fc35414bf58a`
{: .d-inline-block }
GET
{: .label .label-blue }

##### Response: #####

```json
{
    "id": "f295b713-1d6a-43fd-910d-fc35414bf58a",
    "retailer_name": "Save-On-Foods",
    "parent_retailer_name": "Pattison Food Group",
    "store_address": {
        "geo": {
            "postalCode": "V3A 4E4",
            "addressRegion": "British Columbia",
            "streetAddress": "20151 Fraser Hwy",
            "addressCountry": "Canada",
            "addressLocality": "Langley"
        }
    },
    "updated_at": "2023-07-07 03:10:40.820377"
}
```
