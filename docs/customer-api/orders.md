# Orders

The orders API will allow you to:
* View an order.
* Create an order.
* Update an order.
* Place an order.

Orders are uniquely identified by an `order_id` and each order must have a unique `customer_order_no`.

## Endpoints

* Get an order
* Create or update an order
* Place an order

### Get an Order

`GET /apis/customer/orders/:order_id`

####  Request

```
GET /apis/customer/orders/1234
```

#### Response

```
Status: 200 OK
```
```JSON
{
    "order_id": 1234,
    "order_number": 606739,
    "customer_order_no": "MLA-API #12345",
    "order_state": "OPEN",
    "order_type": "WHOLESALE",
    "delivery_method": "DELIVER",
    "delivery_name": null,
    "delivery_company_name": "ML Accessories Limited",
    "delivery_address1": "Unit 4 Foster Avenue",
    "delivery_address2": "Woodside Park",
    "delivery_town": "Dunstable",
    "delivery_county": "Bedfordshire",
    "delivery_country_code": "GB",
    "delivery_postcode": "LU5 5TA",
    "delivery_telephone": "01582 88 77 60",
    "notes": null,
    "products": [
                 {
                     "product_code": "VFR8CW",
                     "type": "stock",
                     "quantity": 5,
                     "description": "PROKNIGHT LED 8w IP65 FIRE RATED 4000K",
                     "vat_code": "S",
                     "vat_rate": 0.2,
                     "unit_price": 23.4500,
                     "line_price": 117.25,
                     "vat": 23.45,
                     "unit_weight": 0.251,
                     "line_weight": 1.255
                 },
                 {
                     "product_code": "CA",
                     "type": "nonstock",
                     "quantity": 1,
                     "description": "Carriage Charge",
                     "vat_code": "S",
                     "vat_rate": 0.2,
                     "unit_price": 10.0000,
                     "line_price": 10.00,
                     "vat": 2.00,
                     "unit_weight": 0,
                     "line_weight": 0
                 }
                ],
    "carriage_tba": false,
    "total_vat": 25.45,
    "total_price": 127.25,
    "total_weight": 1.255,
    "created_at": "2017-02-27 12:00:00+00",
    "created_by": "John Doe",
    "placed_by": null,
    "deleted_by": null
}
```

### Create or Update an Order

`POST /apis/customer/orders`

#### Request

```
POST /apis/customer/orders
```

```JSON
         {
             "customer_order_no": "MLA-API #23456",
             "order_type": "WHOLESALE",
             "delivery_method": "DELIVER",
             "delivery_name": "",
             "delivery_company_name": "ML Accessories Limited",
             "delivery_address1": "Unit 4 Foster Avenue",
             "delivery_address2": "Woodside Park",
             "delivery_town": "Dunstable",
             "delivery_county": "Bedfordshire",
             "delivery_country_code": "GB",
             "delivery_postcode": "LU5 5TA",
             "delivery_telephone": "01582 88 77 60",
             "notes": "Deliver to office.",
             "products": [
                          {
                              "product_code": "VFR8CW",
                              "quantity": 10
                          },
                          {
                              "product_code": "VFR8BEZMW",
                              "quantity": 5
                          },
                          {
                              "product_code": "VFR8BEZCBR",
                              "quantity": 5
                          }
                         ]
         }
```
    
#### Response

```
Status: 200 OK or 201 Created
```

```JSON
{
    "order_id": 2345,
    "order_number": 606750,
    "customer_order_no": "MLA-API #23456",
    "order_state": "OPEN",
    "order_type": "WHOLESALE",
    "delivery_method": "DELIVER",
    "delivery_name": null,
    "delivery_company_name": "ML Accessories Limited",
    "delivery_address1": "Unit 4 Foster Avenue",
    "delivery_address2": "Woodside Park",
    "delivery_town": "Dunstable",
    "delivery_county": "Bedfordshire",
    "delivery_country_code": "GB",
    "delivery_postcode": "LU5 5TA",
    "delivery_telephone": null,
    "notes": "Deliver to office.",
    "products": [
                 {
                     "product_code": "VFR8CW",
                     "type": "stock",
                     "quantity": 10,
                     "description": "PROKNIGHT LED 8w IP65 FIRE RATED 4000K",
                     "vat_code": "S",
                     "vat_rate": 0.2,
                     "unit_price": 23.4500,
                     "line_price": 234.50,
                     "vat": 46.90,
                     "unit_weight": 0.251,
                     "line_weight": 2.51
                 },
                 {
                     "product_code": "VFR8BEZMW",
                     "type": "stock",
                     "quantity": 5,
                     "description": "MATT WHITE BEZEL 2 VFR/VFR8 FIXED DOWNLIGHTS",
                     "vat_code": "S",
                     "vat_rate": 0.2,
                     "unit_price": 1.2300,
                     "line_price": 6.15,
                     "vat": 1.23,
                     "unit_weight": 0.05,
                     "line_weight": 0.25
                 },
                 {
                     "product_code": "VFR8BEZCBR",
                     "type": "stock",
                     "quantity": 5,
                     "description": "BRUSHED CHROME BEZEL 2 VFR/VFR8 FIXED DOWNLIGHTS",
                     "vat_code": "S",
                     "vat_rate": 0.2,
                     "unit_price": 2.3400,
                     "line_price": 11.70,
                     "vat": 2.34,
                     "unit_weight": 0.05,
                     "line_weight": 0.25
                 }
                ],
    "carriage_tba": false,
    "total_vat": 50.47,
    "total_price": 252.35,
    "total_weight": 3.01,
    "created_at": "2017-02-27 14:35:50+00",
    "created_by": "John Doe",
    "placed_by": null,
    "deleted_by": null
}
```

### Place an Order

`PUT /apis/customer/orders/:order_id/place`

#### Request

```
PUT /apis/customer/orders/1234/place
```

#### Response

```
Status: 204 No Content
```