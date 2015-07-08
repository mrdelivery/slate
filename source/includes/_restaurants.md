# Restaurants

This service deals with Restaurants and RestaurantGroups.

## List Restaurants

> Request: 

```shell
http://52.27.51.33:8888/restaurants?location=-33.9209039,18.4221764&include_delivery=true&include_collect=false
```

> Response:

```json
{
  "1": {
    "name": "Nandos",
    "description": "Sells overpriced chicken"
  },
  "2": {
    "name": "Steers",
    "description": "Sells overpriced horsemeat"
  },
  "3": {
    "name": "Ocean Basket",
    "description": "Sells farmed fish"
  },
  "4": {
    "name": "Another Nandos",
    "description": "Also sells overpriced chicken"
  },
  "5": {
    "name": "Another Steers",
    "description": "Also Sells overpriced horsemeat"
  }
}

```
### HTTP Request

`GET /restaurants?location=<lat,long>&include_delivery={true|false}&include_collect={true|false}`

### Query Parameters
Parameter | Type | Default | Required? | Description
--------- | -----| --------| --------- | -----------
location | Google Maps (decimal degrees) style coordinate | N/A | mandatory | The origin of the restaurant search radius
include_delivery | boolean | true | optional | If true, include restaurants we deliver to in the results.
include_collect | boolean | true | optional | If true, include restaurants that support collection from in the results.


## Get Single Restaurant

> Request: 

```shell
http://52.27.51.33:8888/restaurants/5
```
> Response:

```json
{
 "5": {
    "name": "Another Steers",
    "description": "Also Sells overpriced horsemeat"
  }
}
```
### HTTP Request

`GET http://example.com/restaurants/<id>`

### Query Parameters
Parameter | Type | Default | Required? | Description
--------- | -----| --------| --------- | -----------
id|numeric identifier|N/A|mandatory|The DB identifier of the entity to retrieve

## List Restaurant Groups

> Request: 

```shell
http://52.27.51.33:8888/restaurantgroups
```

> Response:

```json
{
  "1": {
    "name": "Nandos Chain",
    "members": [
      1,
      4
    ],
    "type": "Restaurant"
  },
  "2": {
    "name": "Steers Chain",
    "members": [
      2,
      5
    ],
    "type": "Restaurant"
  }
}

```
### HTTP Request

`GET /restaurantgroups`


## Get Single Restaurant Group

> Request: 

```shell
http://52.27.51.33:8888/restaurantgroups/5
```
> Response:

```json
 {
  "name": "Nandos Chain",
  "members": [
    1,
    4
  ],
  "type": "Restaurant"
}
```
### HTTP Request

`GET http://example.com/restaurantgroups/<id>`

### Query Parameters
Parameter | Type | Default | Required? | Description
--------- | -----| --------| --------- | -----------
id|numeric identifier|N/A|mandatory|The DB identifier of the entity to retrieve

