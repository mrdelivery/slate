# Customer App Orders

This is the order creation flow api.

## STEP 1: Create Order

> Definition

```
POST http://qa.mrd.com:8888/orders
```

> Request

> Success Response [200 OK]

> Error Response [400 BAD_REQUEST]

The creation of the order is done at the customer device level.

### Consumers

* CUSTOMER_APP

## STEP 1a: Coupon Authorization Against Order

> Definition

```
PUT http://qa.mrd.com:8888/orders/{order_id}
```

> HTTP Request

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

> HTTP Request

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

> HTTP Request

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

> HTTP Request

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

> HTTP Request

> Success Response [200 OK]

> Error Response [400 BAD_REQUEST]

The restaurant device notifies the server that the order can be serviced.

### Consumers

* RESTAURANT_APP

## STEP 5: Track Order

> Definition

```
PUT http://qa.mrd.com:8888/orders/{order_id}
```

> HTTP Request

> Success Response [200 OK]

> Error Response [400 BAD_REQUEST]

The customer device polls the server at intervals or triggered by push notification.

### Consumers

* CUSTOMER_APP