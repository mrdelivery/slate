# Coupons

This is the coupons api documentation.

## List Coupons

Gets the full list of coupons in the system.

> Definition:

> GET http://qa.mrd.com:8888/coupons

> Example Request:

```shell
curl http://qa.mrd.com:8888/coupons
```

> Response:

```json
{
   "coupons" : [
   ],
   "offset": 0,
   "limit": 0,
   "total": 1
}
```