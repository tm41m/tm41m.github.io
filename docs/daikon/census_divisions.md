---
layout: default
title: census-divisions/
parent: Daikon REST API
nav_order: 5
---

Census division is the general term for a Canadian geographic subregion (such as county, municipalité régionale de comté and regional district). They are typically established to facilitate the provision of public services (such as police or ambulance), but StatCan also utilizes these regions to help disseminate and organize statistical information.

<style>
td, th {
   border: none!important;
}
</style>

### GET /census-divisions/search ###
{: .d-inline-block }

Public
{: .label .label-green }

Returns basic attributes, such as name and type, of a given census division or all census divisions within a region. 

| Request Parameter      | Details |
| ----------- | ----------- |
| region_code      | (Optional) The two letter internationally standardized ISO-3166-2 region code. Returns all census divisions in Canada if `null`|
| name | (Optional) Census division name| 


| Response Key      | type | Definition |
| ----------- | ----------- |----------- |
| id      | string | The unique 4-digit census division id (first two digits correspond to region) |
| name      | string | Census division name |
| type      | string | Census division type |
| land_area     | numeric(32,2) | Land area of census division, in square kilometers (km<sup>2</sup>) |
| region_code   | string | The two letter internationally standardized ISO-3166-2 region code |

#### Example Requests ####
<br>
Specifying a region using the `region_code` will return all census divisions in that region.<br>
{: .d-inline-block }
GET
{: .label .label-blue }
`https://api.tm41m.com/census-divisions/search?region_code=ON`


##### Response: #####

```json
{
    "region_code": "ON",
    "id": "3501",
    "type": "UC",
    "name": "Prescott and Russell",
    "land_area": 2004.2668
}
```
The attributes of a single census division can be observed by specifying the `census_division_name`. Special characters such as spaces and accents can be passed unencoded to the request.<br><br>
`https://api.tm41m.com/census-divisions/search?region_code=QC&name=La Matapédia`
{: .d-inline-block }
GET
{: .label .label-blue }

##### Response: #####

```json
{
    "name": "La Matapédia",
    "id": "2407",
    "type": "MRC",
    "land_area": 5354.5318,
    "region_code": "QC"
}
```