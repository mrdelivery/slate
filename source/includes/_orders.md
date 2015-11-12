# Customer App Orders

This is the order creation flow api.

## STEP 1: Create Order

> Definition

```
POST http://qa.mrd.com:8888/orders
```

> Request

```json
{
  "type": "collect",
  "customer": {
    "id": 42,
    "address" : {
      "street_name" : "lancaster road",
      "province" : "western cape",
      "town" : "cape town",
      "postal_code" : "7768",
      "suburb" : "kenilworth"
    }
  },
  "items": [
    {
            "description": "Breakfast Fruit Cup",
            "variant_name": "Large",
            "price": 35,
            "extras": [
                {
                    "price": 10,
                    "id": 1571,
                    "description": "Extra 1"
                },
                {
                    "price": 20,
                    "id": 1572,
                    "description": "Extra 2"
                }
            ],
            "variant_id": 50000,
            "quantity": 3
        },
        {
            "price": 32,
            "quantity": 2,
            "description": "Breakfast Cup",
            "variant_name": "Regular",
            "variant_id": 19477
        }
  ],
  "restaurant": {
    "id": 416
  },
  "totals": {
    "subtotal": 10,
    "delivery_fee": 25
  }
}
```

> Success Response [200 OK]

```json
{
    "status": "initiated",
    "customer": {
        "first_name": "Ray",
        "last_name": "Nseka",
        "id": 42,
        "address": {
            "town": "cape town",
            "suburb": "kenilworth",
            "street_name": "lancaster road",
            "province": "western cape",
            "postal_code": "7768"
        },
        "email": "nseka@dh.com",
        "phone_1": "0714352972"
    },
    "customer_vat": {
        "total": 0
    },
    "restaurant": {
        "name": "Jason's Test",
        "primary_phone": "0000000000",
        "amount_payable": 229.47,
        "address": {
            "town": "Cape Town",
            "province": "Western Cape",
            "street_number": "41",
            "street_name": "Hertzog Boulevard",
            "longitude": "18.427799",
            "suburb": "Foreshore",
            "postal_code": "8001",
            "latitude": "-33.918627",
            "id": 458
        },
        "commission": {
            "percentage": 10,
            "due": 25.9,
            "vat": 3.63,
            "due_including_vat": 29.53
        },
        "primary_email": "jason.sheldon@trintel.co.za",
        "suggested_preparation_time": 5,
        "assigned_hub": {
            "phone": "0878205406",
            "code": "HOH",
            "id": 50,
            "name": "Head Office - Test"
        },
        "id": 416
    },
    "items": [
        {
            "description": "Breakfast Fruit Cup",
            "variant_name": "Large",
            "price": 35,
            "extras": [
                {
                    "price": 10,
                    "id": 1571,
                    "description": "Extra 1"
                },
                {
                    "price": 20,
                    "id": 1572,
                    "description": "Extra 2"
                }
            ],
            "variant_id": 50000,
            "quantity": 3
        },
        {
            "price": 32,
            "quantity": 2,
            "description": "Breakfast Cup",
            "variant_name": "Regular",
            "variant_id": 19477
        }
    ],
    "totals": {
        "total": 284,
        "subtotal": 259,
        "delivery_fee": 25
    },
    "_created_at": "2015-11-12 12:11:25",
    "invoice_number": "DFD003636",
    "type": "collect",
    "id": 3636
}
```

> Error Response [400 BAD_REQUEST]

The creation of the order is done at the customer device level. By providing the following the order details from the customer device the server creates and populates the orders:

* Customer Id: Fills customer details 
* Restaurant Id: Restaurant details as well as commission totals
* Totals: Server side totalling is done in order to validate the totals shown to the customer during the cart phase

### Todo

* Return error if the restaurant is offline
* Return error if the `type` is invalid for this restaurant or courier hub

### Consumers

* CUSTOMER_APP

### Arguments
Parameter | Description
--------- | -----------
type<br/>_string_<br/>_required_|Whether or not this is a `collect` or `delivery` order.
customer<br/>_string_<br/>_required_|The customer object.
- customer[id]<br/>_string_<br/>_required_|The customer id.
- customer[address]<br/>_string_<br/>_required_|The customer's session address object.
- - customer[address][street_name]<br/>_string_<br/>_required_|The customer's session address street name.
- - customer[address][province]<br/>_string_<br/>_optional_|The customer's session address province.
- - customer[address][town]<br/>_string_<br/>_required_|The customer's session address town.
- - customer[address][postal_code]<br/>_string_<br/>_required_|The customer's session address postal code.
- - customer[address][suburb]<br/>_string_<br/>_required_|The customer's session address suburb.
- - customer[address][longitude]<br/>_string_<br/>_required_|The customer's session address longitude.
- - customer[address][latitude]<br/>_string_<br/>_required_|The customer's session address latitude.
restaurant<br/>_string_<br/>_required_|The restaurant object
- restaurant[id]<br/>_string_<br/>_required_|The restaurant id.
items[]<br/>_string_<br/>_required_|The order line items array.
- items[][description]<br/>_string_<br/>_required_|The order line items description.
- items[][variant_name]<br/>_string_<br/>_required_|The order line items variant description.
- items[][variant_id]<br/>_string_<br/>_required_|The order line items variant id.
- items[][price]<br/>_string_<br/>_required_|The order line items price of the variant chosen.
- items[][quantity]<br/>_string_<br/>_required_|The order line items quantity.
- items[][addons][]<br/>_string_<br/>_required_|The order line items addons array.
- - items[][addons][][id]<br/>_string_<br/>_required_|The order line items addons array.
- - items[][addons][][description]<br/>_string_<br/>_required_|The order line items addons array.
- items[][extras][]<br/>_string_<br/>_required_|The order line items extras array.
- - items[][extras][][id]<br/>_string_<br/>_required_|The order line items addons array.
- - items[][extras][][description]<br/>_string_<br/>_required_|The order line items addons array.
- - items[][extras][][price]<br/>_string_<br/>_required_|The order line items addons array.
- items[][options][]<br/>_string_<br/>_required_|The order line items options array.
- - items[][options][][id]<br/>_string_<br/>_required_|The order line items addons array.
- - items[][options][][description]<br/>_string_<br/>_required_|The order line items addons array.
totals<br/>_integer_<br/>_required_|The totals object.
- totals[subtotal]<br/>_integer_<br/>_required_|The subtotal of the order that was shown to the customer.
- totals[delivery\_fee]<br/>_integer_<br/>_optional_|The delivery fee of the order that was shown to the customer.

## STEP 1a: Coupon Authorization Against Order

> Definition

```
PUT http://qa.mrd.com:8888/orders/{order_id}
```

> Request

> Success Response [200 OK]

> Error Response [400 BAD_REQUEST]

The attachment of the coupon happens at the customer device level.

### Consumers

* CUSTOMER_APP

## STEP 2: Customer Detail Confirmation

> Definition

```
PUT http://qa.mrd.com:8888/orders/{order_id}
```

> Request

> Success Response [200 OK]

> Error Response [400 BAD_REQUEST]

The confirmation of customer details is done at the customer device level

### Consumers

* CUSTOMER_APP

## STEP 3: Customer/Customer Device Confirm Payment

> Definition

```
PUT http://qa.mrd.com:8888/orders/{order_id}
```

> Request

> Success Response [200 OK]

> Error Response [400 BAD_REQUEST]

The confirmation of the payment method is done at the customer device level. For cash the customer consciously selects the payment confirmation, for credit card the device notifies the server that the customer will automatically be made aware the payment went through.

### Consumers

* CUSTOMER_APP

## STEP 4a: Restaurant Acceptance

> Definition

```
PUT http://qa.mrd.com:8888/orders/{order_id}
```

> Request

> Success Response [200 OK]

> Error Response [400 BAD_REQUEST]

The restaurant device notifies the server that the order can be serviced.

### Consumers

* RESTAURANT_APP

## STEP 4b: Restaurant Rejection

> Definition

```
PUT http://qa.mrd.com:8888/orders/{order_id}
```

> Request

> Success Response [200 OK]

> Error Response [400 BAD_REQUEST]

The restaurant device notifies the server that the order can be serviced.

### Consumers

* RESTAURANT_APP

## STEP 5: Track Order

> Definition

```
GET http://qa.mrd.com:8888/orders/{order_id}
```

> Success Response [200 OK]

The customer device polls the server at intervals or triggered by push notification.

### Consumers

* CUSTOMER_APP

## STEP 6: Rating of Order

> Definition

```
PUT http://qa.mrd.com:8888/orders/{order_id}
```

> Request

> Success Response [200 OK]

The rating for the restaurant and driver is done on the order it is related to.

### Consumers

* CUSTOMER_APP