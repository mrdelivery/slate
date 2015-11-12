# Coupons

This is the coupons api documentation.

## List Coupons

> Definition

```
GET http://qa.mrd.com:8888/coupons
```

> Success Response [200 OK]

```json
{
   "coupons" : [
   ],
   "offset": 0,
   "limit": 0,
   "total": 1
}
```

Gets the full list of coupons in the system.


## Create Coupon

> Definition: 

```
POST http://qa.mrd.com:8888/coupons
```

> Request

```json
{
   "description": "Promotional Coupon", 
   "value_amount": 1000, 
   "usage_limit": 100, 
   "limit_type": "user", 
   "_expires_at": "2015-01-01 00:00:00"
}
```

> Success Response [201 Created]

```json
{
   "_uuid": "b67818fc878911e5af63feff819cdc9f",
   "_updated_at" : "2015-11-12 14:31",
   "_created_at" : "2015-11-12 14:31",
   "_valid_at": "2015-11-12 14:31",
   "_expires_at": "2015-01-01 00:00:00",

   "description": "Promotional Coupon",
   "code" : "FOOD27926130",
   "value_amount" : 1000,
   "authorization_count": 0,
   "usage_count": 0,
   "usage_limit": 100,
   "limit_type": "user"
}
```

Creates a new coupon.

### Coupon code generation and Luhn checksum generator

Coupon code is used as a prefix and a 8 length random string of alphanumeric characters is appended. The 8 values end with a luhn digit based on the first 7's ascii integer values appended to each other as strings.

### Arguments
Parameter | Description
--------- | -----------
description<br/>_string_<br/>_optional_|The description of the coupon
code<br/>_string_<br/>_optional_|The coupon code, autogenerates if none specified
percentage_amount<br/>_integer_<br/>_optional_|Set if the value of the coupon offsets an order value based on percentage of order
value_amount<br/>_integer_<br/>_optional_|Set if the value of the coupon offsets an order value based on the this value (in cents)
qualifying_amount<br/>_integer_<br/>_optional_|Amount in cents of the order needed in order for this coupon to be attached to this order
usage_limit<br/>_integer_<br/>_optional_|Limit the amount of times the coupon can be redeemed. Default: `-1 (unlimited)`
limit_type<br/>_string_<br/>_optional_|What kind of limit the coupon imposes. Possible values: `user`, `all`. Default: `all`
\_valid\_at<br/>_string_<br/>_optional_|When the coupon becomes valid from. Default: `current_date`.
\_expires\_at<br/>_string_<br/>_optional_|When the coupon expires

## Get Coupon Details

> Definition: 

```
GET http://qa.mrd.com:8888/coupons/{coupon_id}
```

> Success Response [200 OK]

```json
{
   "_uuid": "b67818fc878911e5af63feff819cdc9f",
   "_updated_at" : "2015-11-12 14:31",
   "_created_at" : "2015-11-12 14:31",
   "_valid_at": "2015-11-12 14:31",
   "_expires_at": "2015-01-01 00:00:00",

   "description": "Promotional Coupon",
   "code" : "FOOD27926130",
   "value_amount" : 1000,
   "authorization_count": 0,
   "usage_count": 0,
   "usage_limit": 100,
   "limit_type": "user"
}
```

Read the coupon details.

## Update Coupon

> Definition

```
PUT http://qa.mrd.com:8888/coupons/{coupon_id}
```

> Request

```json
{
   "description": "Promotional Coupon", 
   "value_amount": 1000, 
   "usage_limit": 100, 
   "limit_type": "user", 
   "_expires_at": "2015-01-01 00:00:00"
}
```

> Success Response [200 OK]

```json
{
   "_uuid": "b67818fc878911e5af63feff819cdc9f",
   "_updated_at" : "2015-11-12 14:31",
   "_created_at" : "2015-11-12 14:31",
   "_valid_at": "2015-11-12 14:31",
   "_expires_at": "2015-01-01 00:00:00",

   "description": "Promotional Coupon",
   "code" : "FOOD27926130",
   "value_amount" : 1000,
   "authorization_count": 0,
   "usage_count": 0,
   "usage_limit": 100,
   "limit_type": "user"
}
```

Updates the coupon. 

### Arguments
Parameter | Description
--------- | -----------
description<br/>_string_<br/>_optional_|The description of the coupon
code<br/>_string_<br/>_optional_|The coupon code, autogenerates if none specified
percentage_amount<br/>_integer_<br/>_optional_|Set if the value of the coupon offsets an order value based on percentage of order
value_amount<br/>_integer_<br/>_optional_|Set if the value of the coupon offsets an order value based on the this value (in cents)
qualifying_amount<br/>_integer_<br/>_optional_|Amount in cents of the order needed in order for this coupon to be attached to this order
usage_limit<br/>_integer_<br/>_optional_|Limit the amount of times the coupon can be redeemed. Default: `-1 (unlimited)`
limit_type<br/>_string_<br/>_optional_|What kind of limit the coupon imposes. Possible values: `user`, `all`. Default: `all`
\_valid\_at<br/>_string_<br/>_optional_|When the coupon becomes valid from. Default: `current_date`.
\_expires\_at<br/>_string_<br/>_optional_|When the coupon expires

## Delete Coupon

> Definition:

```
DELETE http://qa.mrd.com:8888/coupons/{coupon_id}
```

> Success Response [200 OK]

Expires the coupon.