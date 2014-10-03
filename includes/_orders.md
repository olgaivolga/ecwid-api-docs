# Orders

## Search orders

> Request example

```http
GET /api/v3/4870020/orders?customer=johnsmith@example.com&paymentStatus=PAID,AWAITING_PAYMENT&token=1234567890qwqeertt HTTP/1.1
Host: app.ecwid.com
Content-Type: application/json;charset=utf-8
Cache-Control: no-cache
```

`GET https://app.ecwid.com/api/v3/{storeId}/orders?keywords={keywords}&totalFrom={totalFrom}&totalTo={totalTo}&createdFrom={createdFrom}&createdTo={createdTo}&updatedFrom={updatedFrom}&updatedTo={updatedTo}&couponId={couponId}&number={number}&vendorNumber={vendorNumber}&customer={customer}&paymentMethod={paymentMethod}&shippingMethod={shippingMethod}&paymentStatus={paymentStatus}&fulfillmentStatus={fulfillmentStatus}&offset={offset}&limit={limit}&token={token}`

Name | Type    | Description
---- | ------- | --------------
**storeId** |  number | Ecwid store ID
**token** |  string | oAuth token
offset | number | Offset from the beginning of the returned items list (for paging)
limit | number | Maximum number of returned items. Maximum allowed value: `100`. Default value: `10`
keywords |  string | Search term
couponId | number | The code of coupon applied to order
totalFrom |  number | Minimum product price
totalTo | number | Maximum product price
number | number | Order number
vendorNumber | string | Order number with prefix/suffix defined by admin
customer | string | Customer search term (searches by customer)
createdFrom | string | Order placemen date (lower bound) Format: YYYY-MM-DD
createdTo | string | Order placemen date (upper bound) Format: YYYY-MM-DD
paymentMethod | string | Payment method used by customer
shippingMethod | string | Shipping method chosen by customer
paymentStatus | string | Comma separated list of order payment statuses to search. Supported values: <ul><li>`AWAITING_PAYMENT`</li> <li>`PAID`</li> <li>`CANCELLED`</li> <li>`REFUNDED`</li> <li>`INCOMPLETE`</li></ul>
fulfillmentStatus | string | Comma separated list of order fulfilment statuses to search. Supported values: <ul><li>`AWAITING_PROCESSING`</li> <li>`PROCESSING`</li> <li>`SHIPPED`</li> <li>`DELIVERED`</li> <li>`WILL_NOT_DELIVER`</li> <li>`RETURNED`</li></ul>
updatedFrom | string | Order last update date (lower bound) Format: YYYY-MM-DD
updatedTo | string | Order last update date (upper bound) Format: YYYY-MM-DD

<aside class="notice">
If no filters are set in the URL, API will return all orders **except for incomplete orders**
</aside>

<aside class="notice">
Parameters in bold are mandatory
</aside>

### Response

> Response example (JSON)

```json
{
    "total": 1,
    "count": 1,
    "offset": 0,
    "limit": 100,
    "items": [
        {
            "vendorOrderNumber": "18",
            "id": 17684167,
            "subtotal": 29.95,
            "total": 37.39,
            "email": "johnsmith@example.com",
            "paymentMethod": "Purchase order",
            "tax": 1.79,
            "ticket": -385349778,
            "ipAddress": "83.217.8.241",
            "couponDiscount": 1.5,
            "paymentStatus": "PAID",
            "fulfillmentStatus": "AWAITING_PROCESSING",
            "orderNumber": 18,
            "refererUrl": "http://mysuperstore.ecwid.com/",
            "orderComments": "Test order comments",
            "hidden": false,
            "volumeDiscount": 0,
            "customerId": 15319410,
            "membershipBasedDiscount": 0,
            "totalAndMembershipBasedDiscount": 2.85,
            "discount": 2.85,
            "usdTotal": 37.39,
            "globalReferer": "",
            "createDate": "2014-09-20 19:59:43 +0400",
            "updateDate": "2014-09-21 00:00:12 +0400",
            "customerGroup": "Gold",
            "discountCoupon": {
                "name": "Coupon # 3",
                "code": "5PERCENTOFF",
                "discountType": "PERCENT",
                "status": "ACTIVE",
                "discount": 5,
                "launchDate": "2014-06-06 00:00:00 +0400",
                "usesLimit": "UNLIMITED",
                "repeatCustomerOnly": false,
                "creationDate": "2014-09-20 19:58:49 +0400",
                "orderCount": 0
            },
            "items": [
                {
                    "id": 40989227,
                    "productId": 37208342,
                    "categoryId": 9691094,
                    "price": 5.99,
                    "productPrice": 5.99,
                    "weight": 0.32,
                    "sku": "00004",
                    "quantity": 5,
                    "shortDescription": "Cherry\nThe word cherry refers to a fleshy fruit (drupe) that contains a single stony seed. The cherry belongs to the fa...",
                    "tax": 1.79,
                    "shipping": 10,
                    "quantityInStock": 1981,
                    "name": "Cherry",
                    "tangible": true,
                    "trackQuantity": true,
                    "fixedShippingRateOnly": false,
                    "imageId": 231131360,
                    "fixedShippingRate": 1,
                    "digital": true,
                    "productAvailable": true,
                    "couponApplied": false,
                    "selectedOptions": [
                        {
                            "name": "Size",
                            "value": "Big",
                            "type": "CHOICE"
                        },
                        {
                            "name": "Attach a file",
                            "type": "FILES",
                            "files": [
                                {
                                    "id": 5973037,
                                    "name": "makfruit_ava_sunnyflower_200_200.jpg",
                                    "size": 54492,
                                    "url": "https://app.ecwid.com/orderfile/4870020/5973037/54492/makfruit_ava_sunnyflower_200_200.jpg"
                                }
                            ]
                        },
                        {
                            "name": "Choose date",
                            "value": "2014-09-10",
                            "type": "DATE"
                        },
                        {
                            "name": "Any text",
                            "value": "Test text",
                            "type": "TEXT"
                        }
                    ],
                    "taxes": [
                        {
                            "name": "Tax X",
                            "value": 7,
                            "total": 1.79
                        }
                    ]
                }
            ],
            "billingPerson": {
                "name": "John Smith",
                "companyName": "Unreal Company",
                "street": "W 3d st",
                "city": "New York",
                "countryCode": "US",
                "postalCode": "10001",
                "stateOrProvinceCode": "NY",
                "phone": "+1234567890"
            },
            "shippingPerson": {
                "name": "John Smith",
                "companyName": "Unreal Company",
                "street": "W 3d st",
                "city": "New York",
                "countryCode": "US",
                "postalCode": "10001",
                "stateOrProvinceCode": "NY",
                "phone": "+1234567890"
            },
            "shippingOption": {
                "shippingMethodId": "12017-1411120444150",
                "shippingMethodName": "2nd day delivery",
                "shippingRate": 10,
                "estimatedTransitTime": "5"
            },
            "additionalInfo": {},
            "paymentParams": {
                "Company name": "Unreal Company",
                "Job position": "Manager",
                "PO number": "123abcd",
                "Buyer's full name": "John Smith"
            },
            "discountInfo": [
                {
                    "value": 10,
                    "type": "PERCENT",
                    "base": "ON_TOTAL_AND_MEMBERSHIP",
                    "orderTotal": 15
                }
            ]
        }
    ]
}
```

A JSON object of type 'SearchResult' with the following fields:

#### SearchResult
Field | Type | Description
----- | ---- | -----------
total | number | The total number of found items (might be more than the number of returned items)
count | number | The total number of the items returned in this batch
offset | number | Offset from the beginning of the returned items list (for paging)
limit | number | Maximum number of returned items. Maximum allowed value: `100`. Default value: `10`
items | Array\<*OrderEntry*\> | The items list

#### OrderEntry
Field | Type |  Description
------| -----| ------------
orderNumber | number | Unique order number without prefixes/suffixes, e.g. `34`
vendorNumber |  string | Order number with prefix and suffix defined by admin, e.g. `ABC34-q`
subtotal |  number | Order subtotal
total | number | Order total cost
email | string  | Customer email address
paymentMethod | string |  Payment method name
paymentModule | string | Payment processor name
tax | number | Tax total
ipAddress | string  | Customer IP
couponDiscount | number | Discount applied with a coupon
paymentStatus | string |    Payment status. Supported values: <ul><li>`AWAITING_PAYMENT`</li> <li>`PAID`</li> <li>`CANCELLED`</li> <li>`REFUNDED`</li> <li>`INCOMPLETE`</li></ul>
fulfillmentStatus | string |    Fulfilment status. Supported values: <ul><li>`AWAITING_PROCESSING`</li> <li>`PROCESSING`</li> <li>`SHIPPED`</li> <li>`DELIVERED`</li> <li>`WILL_NOT_DELIVER`</li> <li>`RETURNED`</li></ul>
refererUrl | string | URL of the page that the order was placed on
orderComments | string  | Order comments
volumeDiscount | number | Subtotal based discount sum
customerId | number  | Unique customer internal ID (if the order is placed by a registered user)
membershipBasedDiscount | number | Customer group based discount sum
totalAndMembershipBasedDiscount | number | The sum of discount based on subtotal AND customer group 
discount | number | The total sum of applied discounts
usdTotal | number | Order total in USD
globalReferer | string | URL that the customer came to the store from
createDate | date |  The date/time of order placement, e.g `2014-06-06 18:57:19 +0400`
updateDate | date |  The date/time of the last order change, e.g `2014-06-06 18:57:19 +0400`
customerGroup | string | The name of group (membership) the customer belongs to
discountCoupon | \<*DiscountCouponInfo*\> | Information about applied coupon
items | Array\<*OrderItem*\> | Order items
billingPerson | \<*PersonInfo*\> | Name and billing address of the customer
shippingPerson | \<*PersonInfo*\> | Name and address of the person entered in shipping information
shippingOption | \<*ShippingOptionInfo*\> | Information about selected shipping option
additionalInfo | Map\<*string,string*\> | Additional order information (if any)
paymentParams | Map\<string,string\> |  Additional payment parameters entered by customer on checkout, e.g. `PO number` in "Purchase order" payments
discountInfo | Array\<*DiscountInfo*\> | Information about applied discounts (coupons are not included)
trackingNumber |  string | Shipping tracking code
paymentMessage | string | Message from the payment processor if any
extTransactionId | string | Transaction ID / invoice number of the order in the payment system (e.g. PayPal transaction ID)
affiliateId |   string  | Affiliate ID
creditCardStatus | \<*CreditCardStatus*\> | The status of credit card payment

#### OrderItem
**Field** | **Type** |  **Description**
--------- | -----------| -----------
id | number | Order item ID
productId | number | Store product ID
categoryId |  number  | ID of the category this product belongs to. If the product belongs to many categories, categoryID will return the ID of the default product category. If the product doesn't belong to any category, `0` is returned
price | number | Price of ordered item in the cart
productPrice | number | Product price
weight |  number | Product weight
sku |   string | Product SKU
quantity |  number | Amount purchased
shortDescription | string | Product description truncated to 120 characters
tax | number | Tax amount applied to the item
shipping | number| Order item shipping cost 
quantityInStock | number | The number of products in stock in the store
name |  string | Product name
tangible | boolean | `true`/`false`: shows whether the item requires shipping
trackQuantity | boolean | `true`/`false`: shows whether the store admin set to track the quantity of this product and get low stock notifications
fixedShippingRateOnly | boolean | `true`/`false`: shows whether the fixed shipping rate is set for the product
imageId | number | Product image internal ID
fixedShippingRate | number| Fixed shipping rate for the product
digital | boolean | `true`/`false`: shows whether the item has downloadable files attached
productAvailable | boolean | `true`/`false`: shows whether the product is available in the store
couponApplied | boolean | `true`/`false`: shows whether a discount coupon is applied for this item
selectedOptions | Array\<*OrderItemOption*\> | Product options values selected by the customer
taxes |  Array\<*OrderItemTax*\> | Taxes applied to this order item
files | Array\<*OrderItemProductFile*\> | Files attached to the order item

#### OrderItemTax
**Field** | **Type** |  **Description**
--------- | -----------| -----------
name |  string | Tax name
value | number | Tax value in percent
total | number | Tax amount for the item

#### OrderItemOption
**Field** | **Type** |  **Description**
--------- | -----------| -----------
name |  string | Option name
type |  string | Option type. One of `SELECT`, `CHECKBOX`, `TEXT`, `DATE`, `FILE`.
value | string | Selected/entered value
files | Array\<*OrderItemOptionFile*\> | Attached files (if the option type is `FILE`)

#### OrderItemOptionFile
**Field** | **Type** |  **Description**
--------- | -----------| -----------
id | number | File ID
name |  string | File name
size |  number | File size in bytes
url |   string | File URL

#### PersonInfo
**Field** | **Type** |  **Description**
--------- | -----------| -----------
name |  string  | Full name
companyName |   string  | Company name
street |    string  | Address
city |  string  | City
countryCode | string  | Two-letter country code
postalCode | string  | Postal/ZIP code
stateOrProvinceCode |   string  | State code, e.g. `NY`
phone | string  | Phone number

#### DiscountCouponInfo
Field | Type  | Description
----- | ----- | -----------
name |  string | Coupon title in store control panel
code |  string | Coupon code
discountType | string | Discount type: `ABS`, `PERCENT` or `SHIPPING`
status | string | Discount coupon state: `ACTIVE`, `PAUSED`, `EXPIRED` or `USEDUP`
discount | number | Discount amount
launchDate | string | The date of coupon launch, e.g. `2014-06-06 08:00:00 +0400`
expirationDate | string | Coupon expiration date, e.g. `2014-06-06 08:00:00 +0400`
totalLimit | number| The minimum order subtotal the coupon applies to
usesLimit | string | Number of uses limitation: `UNLIMITED`, `ONCEPERCUSTOMER`, `SINGLE`
repeatCustomerOnly | boolean | Coupon usage limitation flag identifying whether the coupon works for all customers or only repeat customers
creationDate |  string | Coupon creation date
orderCount | number | Number of uses
catalogLimit |  \<*DiscountCouponCatalogLimit*\> | Products and categories the coupon can be applied to

#### DiscountCouponCatalogLimit
Field | Type | Description
----- | ---- | -----------
products | Array\<number\> | The list of product IDs the coupon can be applied to
categories | Array\<number\> | The list of category IDs the coupon can be applied to

#### ShippingOptionInfo
Field | Type | Description
----- | ---- | -----------
shippingMethodId | string | Shipping method internal ID
shippingCarrierName | string | Shipping carrier name, e.g. `USPS`
shippingMethodName | string | Shipping option name
shippingRate | number | Rate
estimatedTransitTime | number | Delivery time estimation

#### DiscountInfo
Field | Type | Description
----- | ---- | -----------
value | number | Discount value
type | string | Discount type: `ABS` or `PERCENT`
base | string | Discount base, one of `ON_TOTAL`, `ON_MEMBERSHIP`, `ON_TOTAL_AND_MEMBERSHIP`
order_total | number | Minimum order subtotal the discount applies to

#### CreditCardStatus
Field | Type | Description
----- | ---- | -----------
avsMessage | string  | Address verification status returned by the payment system.
cvvMessage | string  | Credit card verification status returned by the payment system.

### Errors

> Error response example

```http
HTTP/1.1 500 Server Error
Content-Type application/json; charset=utf-8
```

In case of error, Ecwid responds with an error HTTP status code and, optionally, JSON-formatted body containing error description

#### HTTP codes

HTTP Status | Meaning
------------|--------
400 | Request parameters are malformed
500 | Cannot retrieve the order info because of an error on the server

#### Error response body (optional)

Field | Type |  Description
--------- | ---------| -----------
errorMessage | string | Error message


## Get order details

> Request example

```http
GET /api/v3/4870020/orders/123456780?token=1234567890qwqeertt HTTP/1.1
Host: app.ecwid.com
Content-Type: application/json;charset=utf-8
Cache-Control: no-cache
```

`GET https://app.ecwid.com/api/v3/{storeId}/orders/{id}?token={token}`

Name | Type    | Description
---- | ------- | --------------
**storeId** |  number | Ecwid store ID
**token** |  string | oAuth token
**id** | number | Order internal ID

<aside class="notice">
Parameters in bold are mandatory
</aside>

### Response

> Response example (JSON)

```json
{
    "vendorOrderNumber": "18",
    "id": 17684167,
    "subtotal": 29.95,
    "total": 37.39,
    "email": "johnsmith@example.com",
    "paymentMethod": "Purchase order",
    "tax": 1.79,
    "ticket": -385349778,
    "ipAddress": "83.217.8.241",
    "couponDiscount": 1.5,
    "paymentStatus": "PAID",
    "fulfillmentStatus": "AWAITING_PROCESSING",
    "orderNumber": 18,
    "refererUrl": "http://mysuperstore.ecwid.com/",
    "orderComments": "Test order comments",
    "hidden": false,
    "volumeDiscount": 0,
    "customerId": 15319410,
    "membershipBasedDiscount": 0,
    "totalAndMembershipBasedDiscount": 2.85,
    "discount": 2.85,
    "usdTotal": 37.39,
    "globalReferer": "",
    "createDate": "2014-09-20 19:59:43 +0400",
    "updateDate": "2014-09-21 00:00:12 +0400",
    "customerGroup": "Gold",
    "discountCoupon": {
        "name": "Coupon # 3",
        "code": "5PERCENTOFF",
        "discountType": "PERCENT",
        "status": "ACTIVE",
        "discount": 5,
        "launchDate": "2014-06-06 00:00:00 +0400",
        "usesLimit": "UNLIMITED",
        "repeatCustomerOnly": false,
        "creationDate": "2014-09-20 19:58:49 +0400",
        "orderCount": 0
    },
    "items": [
        {
            "id": 40989227,
            "productId": 37208342,
            "categoryId": 9691094,
            "price": 5.99,
            "productPrice": 5.99,
            "weight": 0.32,
            "sku": "00004",
            "quantity": 5,
            "shortDescription": "Cherry\nThe word cherry refers to a fleshy fruit (drupe) that contains a single stony seed. The cherry belongs to the fa...",
            "tax": 1.79,
            "shipping": 10,
            "quantityInStock": 1981,
            "name": "Cherry",
            "tangible": true,
            "trackQuantity": true,
            "fixedShippingRateOnly": false,
            "imageId": 231131360,
            "fixedShippingRate": 1,
            "digital": true,
            "productAvailable": true,
            "couponApplied": false,
            "selectedOptions": [
                {
                    "name": "Size",
                    "value": "Big",
                    "type": "CHOICE"
                },
                {
                    "name": "Attach a file",
                    "type": "FILES",
                    "files": [
                        {
                            "id": 5973037,
                            "name": "makfruit_ava_sunnyflower_200_200.jpg",
                            "size": 54492,
                            "url": "https://app.ecwid.com/orderfile/4870020/5973037/54492/makfruit_ava_sunnyflower_200_200.jpg"
                        }
                    ]
                },
                {
                    "name": "Choose date",
                    "value": "2014-09-10",
                    "type": "DATE"
                },
                {
                    "name": "Any text",
                    "value": "Test text",
                    "type": "TEXT"
                }
            ],
            "taxes": [
                {
                    "name": "Tax X",
                    "value": 7,
                    "total": 1.79
                }
            ]
        }
    ],
    "billingPerson": {
        "name": "John Smith",
        "companyName": "Unreal Company",
        "street": "W 3d st",
        "city": "New York",
        "countryCode": "US",
        "postalCode": "10001",
        "stateOrProvinceCode": "NY",
        "phone": "+1234567890"
    },
    "shippingPerson": {
        "name": "John Smith",
        "companyName": "Unreal Company",
        "street": "W 3d st",
        "city": "New York",
        "countryCode": "US",
        "postalCode": "10001",
        "stateOrProvinceCode": "NY",
        "phone": "+1234567890"
    },
    "shippingOption": {
        "shippingMethodId": "12017-1411120444150",
        "shippingMethodName": "2nd day delivery",
        "shippingRate": 10,
        "estimatedTransitTime": "5"
    },
    "additionalInfo": {},
    "paymentParams": {
        "Company name": "Unreal Company",
        "Job position": "Manager",
        "PO number": "123abcd",
        "Buyer's full name": "John Smith"
    },
    "discountInfo": [
        {
            "value": 10,
            "type": "PERCENT",
            "base": "ON_TOTAL_AND_MEMBERSHIP",
            "orderTotal": 15
        }
    ]
}
```

A JSON object of type 'Order' with the following fields:

#### Order
Field | Type |  Description
------| -----| ------------
orderNumber | number | Unique order number without prefixes/suffixes, e.g. `34`
vendorNumber |  string | Order number with prefix and suffix defined by admin, e.g. `ABC34-q`
id | number | Order internal ID
subtotal |  number | Order subtotal
total | number | Order total cost
email | string  | Customer email address
paymentMethod | string |  Payment method name
paymentModule | string | Payment processor name
tax | number | Tax total
ipAddress | string  | Customer IP
couponDiscount | number | Discount applied with a coupon
paymentStatus | string |    Payment status. Supported values: <ul><li>`AWAITING_PAYMENT`</li> <li>`PAID`</li> <li>`CANCELLED`</li> <li>`REFUNDED`</li> <li>`INCOMPLETE`</li></ul>
fulfillmentStatus | string |    Fulfilment status. Supported values: <ul><li>`AWAITING_PROCESSING`</li> <li>`PROCESSING`</li> <li>`SHIPPED`</li> <li>`DELIVERED`</li> <li>`WILL_NOT_DELIVER`</li> <li>`RETURNED`</li></ul>
refererUrl | string | URL of the page that the order was placed on
orderComments | string  | Order comments
volumeDiscount | number | Subtotal based discount sum
customerId | number  | Unique customer internal ID (if the order is placed by a registered user)
membershipBasedDiscount | number | Customer group based discount sum
totalAndMembershipBasedDiscount | number | The sum of discount based on subtotal AND customer group 
discount | number | The total sum of applied discounts
usdTotal | number | Order total in USD
globalReferer | string | URL that the customer came to the store from
createDate | date |  The date/time of order placement, e.g `2014-06-06 18:57:19 +0400`
updateDate | date |  The date/time of the last order change, e.g `2014-06-06 18:57:19 +0400`
customerGroup | string | The name of group (membership) the customer belongs to
discountCoupon | \<*DiscountCouponInfo*\> | Information about applied coupon
items | Array\<*OrderItem*\> | Order items
billingPerson | \<*PersonInfo*\> | Name and billing address of the customer
shippingPerson | \<*PersonInfo*\> | Name and address of the person entered in shipping information
shippingOption | \<*ShippingOptionInfo*\> | Information about selected shipping option
additionalInfo | Map\<*string,string*\> | Additional order information (if any)
paymentParams | Map\<string,string\> |  Additional payment parameters entered by customer on checkout, e.g. `PO number` in "Purchase order" payments
discountInfo | Array\<*DiscountInfo*\> | Information about applied discounts (coupons are not included)
trackingNumber |  string | Shipping tracking code
paymentMessage | string | Message from the payment processor if any
extTransactionId | string | Transaction ID / invoice number of the order in the payment system (e.g. PayPal transaction ID)
affiliateId |   string  | Affiliate ID
creditCardStatus | \<*CreditCardStatus*\> | The status of credit card payment

#### OrderItem
**Field** | **Type** |  **Description**
--------- | -----------| -----------
id | number | Order item ID
productId | number | Store product ID
categoryId |  number  | ID of the category this product belongs to. If the product belongs to many categories, categoryID will return the ID of the default product category. If the product doesn't belong to any category, `0` is returned
price | number | Price of ordered item in the cart
productPrice | number | Product price
weight |  number | Product weight
sku |   string | Product SKU
quantity |  number | Amount purchased
shortDescription | string | Product description truncated to 120 characters
tax | number | Tax amount applied to the item
shipping | number| Order item shipping cost 
quantityInStock | number | The number of products in stock in the store
name |  string | Product name
tangible | boolean | `true`/`false`: shows whether the item requires shipping
trackQuantity | boolean | `true`/`false`: shows whether the store admin set to track the quantity of this product and get low stock notifications
fixedShippingRateOnly | boolean | `true`/`false`: shows whether the fixed shipping rate is set for the product
imageId | number | Product image internal ID
fixedShippingRate | number| Fixed shipping rate for the product
digital | boolean | `true`/`false`: shows whether the item has downloadable files attached
productAvailable | boolean | `true`/`false`: shows whether the product is available in the store
couponApplied | boolean | `true`/`false`: shows whether a discount coupon is applied for this item
selectedOptions | Array\<*OrderItemOption*\> | Product options values selected by the customer
taxes |  Array\<*OrderItemTax*\> | Taxes applied to this order item
files | Array\<*OrderItemProductFile*\> | Files attached to the order item

#### OrderItemTax
**Field** | **Type** |  **Description**
--------- | -----------| -----------
name |  string | Tax name
value | number | Tax value in percent
total | number | Tax amount for the item

#### OrderItemOption
**Field** | **Type** |  **Description**
--------- | -----------| -----------
name |  string | Option name
type |  string | Option type. One of `SELECT`, `CHECKBOX`, `TEXT`, `DATE`, `FILE`.
value | string | Selected/entered value
files | Array\<*OrderItemOptionFile*\> | Attached files (if the option type is `FILE`)

#### OrderItemOptionFile
**Field** | **Type** |  **Description**
--------- | -----------| -----------
id | number | File ID
name |  string | File name
size |  number | File size in bytes
url |   string | File URL

#### PersonInfo
**Field** | **Type** |  **Description**
--------- | -----------| -----------
name |  string  | Full name
companyName |   string  | Company name
street |    string  | Address
city |  string  | City
countryCode | string  | Two-letter country code
postalCode | string  | Postal/ZIP code
stateOrProvinceCode |   string  | State code, e.g. `NY`
phone | string  | Phone number

#### DiscountCouponInfo
Field | Type  | Description
----- | ----- | -----------
name |  string | Coupon title in store control panel
code |  string | Coupon code
discountType | string | Discount type: `ABS`, `PERCENT` or `SHIPPING`
status | string | Discount coupon state: `ACTIVE`, `PAUSED`, `EXPIRED` or `USEDUP`
discount | number | Discount amount
launchDate | string | The date of coupon launch, e.g. `2014-06-06 08:00:00 +0400`
expirationDate | string | Coupon expiration date, e.g. `2014-06-06 08:00:00 +0400`
totalLimit | number| The minimum order subtotal the coupon applies to
usesLimit | string | Number of uses limitation: `UNLIMITED`, `ONCEPERCUSTOMER`, `SINGLE`
repeatCustomerOnly | boolean | Coupon usage limitation flag identifying whether the coupon works for all customers or only repeat customers
creationDate |  string | Coupon creation date
orderCount | number | Number of uses
catalogLimit |  \<*DiscountCouponCatalogLimit*\> | Products and categories the coupon can be applied to

#### DiscountCouponCatalogLimit
Field | Type | Description
----- | ---- | -----------
products | Array\<number\> | The list of product IDs the coupon can be applied to
categories | Array\<number\> | The list of category IDs the coupon can be applied to

#### ShippingOptionInfo
Field | Type | Description
----- | ---- | -----------
shippingMethodId | string | Shipping method internal ID
shippingCarrierName | string | Shipping carrier name, e.g. `USPS`
shippingMethodName | string | Shipping option name
shippingRate | number | Rate
estimatedTransitTime | number | Delivery time estimation

#### DiscountInfo
Field | Type | Description
----- | ---- | -----------
value | number | Discount value
type | string | Discount type: `ABS` or `PERCENT`
base | string | Discount base, one of `ON_TOTAL`, `ON_MEMBERSHIP`, `ON_TOTAL_AND_MEMBERSHIP`
order_total | number | Minimum order subtotal the discount applies to

#### CreditCardStatus
Field | Type | Description
----- | ---- | -----------
avsMessage | string  | Address verification status returned by the payment system.
cvvMessage | string  | Credit card verification status returned by the payment system.

### Errors

> Error response example

```http
HTTP/1.1 404 Not Found
Content-Type application/json; charset=utf-8
```

In case of error, Ecwid responds with an error HTTP status code and, optionally, JSON-formatted body containing error description

#### HTTP codes

HTTP Status | Meaning
------------|--------
400 | Request parameters are malformed
404 | The order is not found
500 | Cannot retrieve the order info because of an error on the server

#### Error response body (optional)

Field | Type |  Description
--------- | ---------| -----------
errorMessage | string | Error message



## Update order

> Request example

```http
PUT /api/v3/4870020/orders/123456780?token=1234567890qwqeertt HTTP/1.1
Host: app.ecwid.com
Content-Type: application/json;charset=utf-8
Cache-Control: no-cache

{
        "subtotal": 35,
        "total": 45,
        "email": "newemail@example.com",
        "paymentMethod": "New payment method",
        "tax": 0,
        "paymentStatus": "CANCELLED",
        "fulfillmentStatus": "PROCESSING",
        "billingPerson": {
            "name": "Eugene K",
            "companyName": "Hedgehog and Bucket",
            "street": "My Street",
            "city": "San Diego",
            "countryCode": "US",
            "postalCode": "90002",
            "stateOrProvinceCode": "CA",
            "phone": "123141321"
        },
        "shippingPerson": {
            "name": "Eugene K",
            "companyName": "Hedgehog and Bucket",
            "street": "My Street",
            "city": "San Diego",
            "countryCode": "US",
            "postalCode": "90002",
            "stateOrProvinceCode": "CA",
            "phone": "123141321"
        },
        "shippingOption": {
            "shippingMethodName": "Fast Delivery",
            "shippingRate": 10
        },
        "items": [
            {
                "id": 41056225,
                "productId": 37208346,
                "price": 7.99,
                "productPrice": 7.99,
                "weight": 0.31,
                "sku": "00001",
                "quantity": 5,
                "shortDescription": "New description",
                "tax": 1.79,
                "shipping": 10,
                "quantityInStock": 1981,
                "name": "New name",
                "tangible": true,
                "fixedShippingRateOnly": false,
                "productAvailable": true,
                "selectedOptions": [
                    {
                        "name": "Size",
                        "value": "Big",
                        "type": "CHOICE"
                    },                  
                    {
                        "name": "Any text",
                        "value": "Test text",
                        "type": "TEXT"
                    }
                ],
                "taxes": [
                    {
                        "name": "Tax Y",
                        "value": 7,
                        "total": 4.79
                    }
                ]
            }
        ]
    }
```

`PUT https://app.ecwid.com/api/v3/{storeId}/orders/{id}?token={token}`

Name | Type    | Description
---- | ------- | --------------
**storeId** |  number | Ecwid store ID
**token** |  string | oAuth token
**id** | number | Order internal ID

### Request body

A JSON object of type 'Order' with the following fields:

#### Order
Field | Type |  Description
------| -----| ------------
subtotal |  number | Order subtotal
total | number | Order total cost
email | string  | Customer email address
paymentMethod | string |  Payment method name
paymentModule | string | Payment processor name
tax | number | Tax total
ipAddress | string  | Customer IP
couponDiscount | number | Discount applied with a coupon
paymentStatus | string |    Payment status. Supported values: <ul><li>`AWAITING_PAYMENT`</li> <li>`PAID`</li> <li>`CANCELLED`</li> <li>`REFUNDED`</li> <li>`INCOMPLETE`</li></ul>
fulfillmentStatus | string |    Fulfilment status. Supported values: <ul><li>`AWAITING_PROCESSING`</li> <li>`PROCESSING`</li> <li>`SHIPPED`</li> <li>`DELIVERED`</li> <li>`WILL_NOT_DELIVER`</li> <li>`RETURNED`</li></ul>
refererUrl | string | URL of the page that the order was placed on
orderComments | string  | Order comments
volumeDiscount | number | Subtotal based discount sum
customerId | number  | Unique customer internal ID (if the order is placed by a registered user)
membershipBasedDiscount | number | Customer group based discount sum
totalAndMembershipBasedDiscount | number | The sum of discount based on subtotal AND customer group 
discount | number | The total sum of applied discounts
usdTotal | number | Order total in USD
globalReferer | string | URL that the customer came to the store from
createDate | date |  The date/time of order placement, e.g `2014-06-06 18:57:19 +0400`
updateDate | date |  The date/time of the last order change, e.g `2014-06-06 18:57:19 +0400`
customerGroup | string | The name of group (membership) the customer belongs to
discountCoupon | \<*DiscountCouponInfo*\> | Information about applied coupon
items | Array\<*OrderItem*\> | Order items
billingPerson | \<*PersonInfo*\> | Name and billing address of the customer
shippingPerson | \<*PersonInfo*\> | Name and address of the person entered in shipping information
shippingOption | \<*ShippingOptionInfo*\> | Information about selected shipping option
additionalInfo | Map\<*string,string*\> | Additional order information (if any)
paymentParams | Map\<string,string\> |  Additional payment parameters entered by customer on checkout, e.g. `PO number` in "Purchase order" payments
discountInfo | Array\<*DiscountInfo*\> | Information about applied discounts (coupons are not included)
trackingNumber |  string | Shipping tracking code
paymentMessage | string | Message from the payment processor if any
extTransactionId | string | Transaction ID / invoice number of the order in the payment system (e.g. PayPal transaction ID)
affiliateId |   string  | Affiliate ID
creditCardStatus | \<*CreditCardStatus*\> | The status of credit card payment

#### OrderItem
**Field** | **Type** |  **Description**
--------- | -----------| -----------
**id** | number | Order item ID
**quantity** |  number | Amount purchased
**name** |  string | Product name
productId | number | Store product ID
categoryId |  number  | ID of the category this product belongs to. If the product belongs to many categories, categoryID will return the ID of the default product category. If the product doesn't belong to any category, `0` is returned
price | number | Price of ordered item in the cart
productPrice | number | Product price
weight |  number | Product weight
sku |   string | Product SKU
shortDescription | string | Product description truncated to 120 characters
tax | number | Tax amount applied to the item
shipping | number| Order item shipping cost 
quantityInStock | number | The number of products in stock in the store
tangible | boolean | `true`/`false`: shows whether the item requires shipping
trackQuantity | boolean | `true`/`false`: shows whether the store admin set to track the quantity of this product and get low stock notifications
fixedShippingRateOnly | boolean | `true`/`false`: shows whether the fixed shipping rate is set for the product
imageId | number | Product image internal ID
fixedShippingRate | number| Fixed shipping rate for the product
digital | boolean | `true`/`false`: shows whether the item has downloadable files attached
productAvailable | boolean | `true`/`false`: shows whether the product is available in the store
couponApplied | boolean | `true`/`false`: shows whether a discount coupon is applied for this item
selectedOptions | Array\<*OrderItemOption*\> | Product options values selected by the customer
taxes |  Array\<*OrderItemTax*\> | Taxes applied to this order item

#### OrderItemTax
**Field** | **Type** |  **Description**
--------- | -----------| -----------
name |  string | Tax name
value | number | Tax value in percent
total | number | Tax amount for the item

#### OrderItemOption
**Field** | **Type** |  **Description**
--------- | -----------| -----------
**name** |  string | Option name
**type** |  string | Option type. One of `SELECT`, `CHECKBOX`, `TEXT`, `DATE`, `FILE`.
value | string | Selected/entered value
files | Array\<*OrderItemOptionFile*\> | Attached files (if the option type is `FILE`)

#### PersonInfo
**Field** | **Type** |  **Description**
--------- | -----------| -----------
name |  string  | Full name
companyName |   string  | Company name
street |    string  | Address
city |  string  | City
countryCode | string  | Two-letter country code
postalCode | string  | Postal/ZIP code
stateOrProvinceCode |   string  | State code, e.g. `NY`
phone | string  | Phone number

#### DiscountCouponInfo
Field | Type  | Description
----- | ----- | -----------
name |  string | Coupon title in store control panel
code |  string | Coupon code
discountType | string | Discount type: `ABS`, `PERCENT` or `SHIPPING`
status | string | Discount coupon state: `ACTIVE`, `PAUSED`, `EXPIRED` or `USEDUP`
discount | number | Discount amount
launchDate | string | The date of coupon launch, e.g. `2014-06-06 08:00:00 +0400`
expirationDate | string | Coupon expiration date, e.g. `2014-06-06 08:00:00 +0400`
totalLimit | number| The minimum order subtotal the coupon applies to
usesLimit | string | Number of uses limitation: `UNLIMITED`, `ONCEPERCUSTOMER`, `SINGLE`
repeatCustomerOnly | boolean | Coupon usage limitation flag identifying whether the coupon works for all customers or only repeat customers
creationDate |  string | Coupon creation date
orderCount | number | Number of uses
catalogLimit |  \<*DiscountCouponCatalogLimit*\> | Products and categories the coupon can be applied to

#### DiscountCouponCatalogLimit
Field | Type | Description
----- | ---- | -----------
products | Array\<number\> | The list of product IDs the coupon can be applied to
categories | Array\<number\> | The list of category IDs the coupon can be applied to

#### ShippingOptionInfo
Field | Type | Description
----- | ---- | -----------
shippingMethodId | string | Shipping method internal ID
shippingCarrierName | string | Shipping carrier name, e.g. `USPS`
shippingMethodName | string | Shipping option name
shippingRate | number | Rate
estimatedTransitTime | number | Delivery time estimation

#### DiscountInfo
Field | Type | Description
----- | ---- | -----------
value | number | Discount value
type | string | Discount type: `ABS` or `PERCENT`
base | string | Discount base, one of `ON_TOTAL`, `ON_MEMBERSHIP`, `ON_TOTAL_AND_MEMBERSHIP`
order_total | number | Minimum order subtotal the discount applies to

#### CreditCardStatus
Field | Type | Description
----- | ---- | -----------
avsMessage | string  | Address verification status returned by the payment system.
cvvMessage | string  | Credit card verification status returned by the payment system.

### Response


> Response example (JSON)

```json
{
    "updateCount": 1,
    "success": true
}
```

A JSON object of type 'UpdateStatus' with the following fields:

#### UpdateStatus

Field | Type |  Description
-------------- | -------------- | --------------
updateCount | number | The number of updated orders (`1` or `0` depending on whether the update was successful)
success | boolean | `true` if the order has been updated, `false` otherwise

### Errors

> Error response example

```http
HTTP/1.1 400 Status QUEUED is deprecated, use AWAITING_PAYMENT instead
Content-Type application/json; charset=utf-8
```

In case of error, Ecwid responds with an error HTTP status code and, optionally, JSON-formatted body containing error description

#### HTTP codes

HTTP Status | Meaning
------------|--------
400 | Request parameters are invalid
404 | The order is not found
500 | Cannot update the order info because of an error on the server

#### Error response body (optional)

Field | Type |  Description
--------- | ---------| -----------
errorMessage | string | Error message


## Delete order

> Request example

```http
DELETE /api/v3/4870020/orders/39847403?token=123456789abcd HTTP/1.1
Host: app.ecwid.com
Content-Type: application/json;charset=utf-8
Cache-Control: no-cache
```

`DELETE https://app.ecwid.com/api/v3/{storeId}/orders/{id}?token={token}`

Name | Type    | Description
---- | ------- | -----------
**storeId** |  number | Ecwid store ID
**id** | number | Order internal ID
**token** |  string |  oAuth token

### Response

> Response example

```json
{
    "deleteCount": 1,
    "success": true
}
```

A JSON object of type 'DeleteStatus' with the following fields:

#### DeleteStatus

Field | Type |  Description
----- | ---- | --------------
deleteCount | number | The number of deleted orders (`1` or `0` depending on whether the request was successful)
success | boolean | `true` if the order has been deleted, `false` otherwise


### Errors

> Error response example

```http
HTTP/1.1 404 Not Found
Content-Type application/json; charset=utf-8
```

In case of error, Ecwid responds with an error HTTP status code and, optionally, JSON-formatted body containing error description.

#### HTTP codes

**HTTP Status** | **Response JSON** | Description
-------------- | -------------- | --------------
400 | Request parameters are malformed
404 | The order with given ID is not found
500 | The delete request failed because of an error on the server

#### Error response body (optional)

Field | Type |  Description
--------- | ---------| -----------
errorMessage | string | Error message



## Create order

> Request example

```http
POST /api/v3/4870020/orders?token=1234567890qwqeertt HTTP/1.1
Host: app.ecwid.com
Content-Type: application/json;charset=utf-8
Cache-Control: no-cache
{
        "subtotal": 30,
        "total": 40,
        "email": "example@example.com",
        "paymentMethod": "Phone order",
        "tax": 0,
        "paymentStatus": "PAID",
        "fulfillmentStatus": "AWAITING_PROCESSING",
        "items": [
            {
                "price": 15,
                "weight": 0.32,
                "sku": "00004",
                "quantity": 2,
                "name": "Cherry",
            }
        ],
        "billingPerson": {
            "name": "Eugene K",
            "companyName": "Hedgehog and Bucket",
            "street": "My Street",
            "city": "San Diego",
            "countryCode": "US",
            "postalCode": "90002",
            "stateOrProvinceCode": "CA",
            "phone": "123141321"
        },
        "shippingPerson": {
            "name": "Eugene K",
            "companyName": "Hedgehog and Bucket",
            "street": "My Street",
            "city": "San Diego",
            "countryCode": "US",
            "postalCode": "90002",
            "stateOrProvinceCode": "CA",
            "phone": "123141321"
        },
        "shippingOption": {
            "shippingMethodName": "Fast Delivery",
            "shippingRate": 10
        }
    }
```

`POST https://app.ecwid.com/api/v3/{storeId}/orders?token={token}`

Name | Type    | Description
---- | ------- | --------------
**storeId** |  number | Ecwid store ID
**token** |  string | oAuth token

### Request body

A JSON object of type 'Order' with the following fields:

#### Order
Field | Type |  Description
------| -----| ------------
subtotal |  number | Order subtotal
total | number | Order total cost
email | string  | Customer email address
paymentMethod | string |  Payment method name
paymentModule | string | Payment processor name
tax | number | Tax total
ipAddress | string  | Customer IP
couponDiscount | number | Discount applied with a coupon
paymentStatus | string |    Payment status. Supported values: <ul><li>`AWAITING_PAYMENT`</li> <li>`PAID`</li> <li>`CANCELLED`</li> <li>`REFUNDED`</li> <li>`INCOMPLETE`</li></ul>
fulfillmentStatus | string |    Fulfilment status. Supported values: <ul><li>`AWAITING_PROCESSING`</li> <li>`PROCESSING`</li> <li>`SHIPPED`</li> <li>`DELIVERED`</li> <li>`WILL_NOT_DELIVER`</li> <li>`RETURNED`</li></ul>
refererUrl | string | URL of the page that the order was placed on
orderComments | string  | Order comments
volumeDiscount | number | Subtotal based discount sum
customerId | number  | Unique customer internal ID (if the order is placed by a registered user)
membershipBasedDiscount | number | Customer group based discount sum
totalAndMembershipBasedDiscount | number | The sum of discount based on subtotal AND customer group 
discount | number | The total sum of applied discounts
usdTotal | number | Order total in USD
globalReferer | string | URL that the customer came to the store from
createDate | date |  The date/time of order placement, e.g `2014-06-06 18:57:19 +0400`
updateDate | date |  The date/time of the last order change, e.g `2014-06-06 18:57:19 +0400`
customerGroup | string | The name of group (membership) the customer belongs to
discountCoupon | \<*DiscountCouponInfo*\> | Information about applied coupon
items | Array\<*OrderItem*\> | Order items
billingPerson | \<*PersonInfo*\> | Name and billing address of the customer
shippingPerson | \<*PersonInfo*\> | Name and address of the person entered in shipping information
shippingOption | \<*ShippingOptionInfo*\> | Information about selected shipping option
additionalInfo | Map\<*string,string*\> | Additional order information (if any)
paymentParams | Map\<string,string\> |  Additional payment parameters entered by customer on checkout, e.g. `PO number` in "Purchase order" payments
discountInfo | Array\<*DiscountInfo*\> | Information about applied discounts (coupons are not included)
trackingNumber |  string | Shipping tracking code
paymentMessage | string | Message from the payment processor if any
extTransactionId | string | Transaction ID / invoice number of the order in the payment system (e.g. PayPal transaction ID)
affiliateId |   string  | Affiliate ID
creditCardStatus | \<*CreditCardStatus*\> | The status of credit card payment

#### OrderItem
**Field** | **Type** |  **Description**
--------- | -----------| -----------
**quantity** |  number | Amount purchased
**name** |  string | Product name
productId | number | Store product ID
categoryId |  number  | ID of the category this product belongs to. If the product belongs to many categories, categoryID will return the ID of the default product category. If the product doesn't belong to any category, `0` is returned
price | number | Price of ordered item in the cart
productPrice | number | Product price
weight |  number | Product weight
sku |   string | Product SKU
shortDescription | string | Product description truncated to 120 characters
tax | number | Tax amount applied to the item
shipping | number| Order item shipping cost 
quantityInStock | number | The number of products in stock in the store
tangible | boolean | `true`/`false`: shows whether the item requires shipping
trackQuantity | boolean | `true`/`false`: shows whether the store admin set to track the quantity of this product and get low stock notifications
fixedShippingRateOnly | boolean | `true`/`false`: shows whether the fixed shipping rate is set for the product
imageId | number | Product image internal ID
fixedShippingRate | number| Fixed shipping rate for the product
digital | boolean | `true`/`false`: shows whether the item has downloadable files attached
productAvailable | boolean | `true`/`false`: shows whether the product is available in the store
couponApplied | boolean | `true`/`false`: shows whether a discount coupon is applied for this item
selectedOptions | Array\<*OrderItemOption*\> | Product options values selected by the customer
taxes |  Array\<*OrderItemTax*\> | Taxes applied to this order item

#### OrderItemTax
**Field** | **Type** |  **Description**
--------- | -----------| -----------
name |  string | Tax name
value | number | Tax value in percent
total | number | Tax amount for the item

#### OrderItemOption
**Field** | **Type** |  **Description**
--------- | -----------| -----------
**name** |  string | Option name
**type** |  string | Option type. One of `SELECT`, `CHECKBOX`, `TEXT`, `DATE`, `FILE`.
value | string | Selected/entered value
files | Array\<*OrderItemOptionFile*\> | Attached files (if the option type is `FILE`)

#### PersonInfo
**Field** | **Type** |  **Description**
--------- | -----------| -----------
name |  string  | Full name
companyName |   string  | Company name
street |    string  | Address
city |  string  | City
countryCode | string  | Two-letter country code
postalCode | string  | Postal/ZIP code
stateOrProvinceCode |   string  | State code, e.g. `NY`
phone | string  | Phone number

#### DiscountCouponInfo
Field | Type  | Description
----- | ----- | -----------
name |  string | Coupon title in store control panel
code |  string | Coupon code
discountType | string | Discount type: `ABS`, `PERCENT` or `SHIPPING`
status | string | Discount coupon state: `ACTIVE`, `PAUSED`, `EXPIRED` or `USEDUP`
discount | number | Discount amount
launchDate | string | The date of coupon launch, e.g. `2014-06-06 08:00:00 +0400`
expirationDate | string | Coupon expiration date, e.g. `2014-06-06 08:00:00 +0400`
totalLimit | number| The minimum order subtotal the coupon applies to
usesLimit | string | Number of uses limitation: `UNLIMITED`, `ONCEPERCUSTOMER`, `SINGLE`
repeatCustomerOnly | boolean | Coupon usage limitation flag identifying whether the coupon works for all customers or only repeat customers
creationDate |  string | Coupon creation date
orderCount | number | Number of uses
catalogLimit |  \<*DiscountCouponCatalogLimit*\> | Products and categories the coupon can be applied to

#### DiscountCouponCatalogLimit
Field | Type | Description
----- | ---- | -----------
products | Array\<number\> | The list of product IDs the coupon can be applied to
categories | Array\<number\> | The list of category IDs the coupon can be applied to

#### ShippingOptionInfo
Field | Type | Description
----- | ---- | -----------
shippingMethodId | string | Shipping method internal ID
shippingCarrierName | string | Shipping carrier name, e.g. `USPS`
shippingMethodName | string | Shipping option name
shippingRate | number | Rate
estimatedTransitTime | number | Delivery time estimation

#### DiscountInfo
Field | Type | Description
----- | ---- | -----------
value | number | Discount value
type | string | Discount type: `ABS` or `PERCENT`
base | string | Discount base, one of `ON_TOTAL`, `ON_MEMBERSHIP`, `ON_TOTAL_AND_MEMBERSHIP`
order_total | number | Minimum order subtotal the discount applies to

#### CreditCardStatus
Field | Type | Description
----- | ---- | -----------
avsMessage | string  | Address verification status returned by the payment system.
cvvMessage | string  | Credit card verification status returned by the payment system.

### Response


> Response example (JSON)

```json
{
    "orderNumber": 17764093,
    "success": true
}
```

A JSON object of type 'CreateStatus' with the following fields:

#### CreateStatus

Field | Type |  Description
-------------- | -------------- | --------------
orderNumber | number | The ID(number) of created order in the store
success | boolean | `true` if the order has been created, `false` otherwise

### Errors

> Error response example

```http
HTTP/1.1 400 Field OrderItem.quantity is absent
Content-Type application/json; charset=utf-8
```

In case of error, Ecwid responds with an error HTTP status code and, optionally, JSON-formatted body containing error description

#### HTTP codes

HTTP Status | Meaning
------------|--------
400 | Request parameters are invalid
404 | The customer or any other linked object is not found in the store
500 | Cannot create an order because of an error on the server

#### Error response body (optional)

Field | Type |  Description
--------- | ---------| -----------
errorMessage | string | Error message


## Upload item option file

Using this method, you can attach a file to an order item (implying that the order item has a 'file upload' option). Request parameters specify which order, item and option should be updated. Request body is the file itself (binary data).

> Request example

```http
POST /api/v3/4870020/orders/1234657/items/987653/options/Attach+your+image?fileName=my_photo.jpg&token=123456789abcd HTTP/1.1
Host: app.ecwid.com
Content-Type: application/json
Cache-Control: no-cache

binary data
```

`POST https://app.ecwid.com/api/v3/{storeId}/orders/{orderNumber}/items/{itemId}/options/{optionName}?fileName={fileName}token={token}`

Name | Type    | Description
---- | ------- | -----------
**storeId** |  number | Ecwid store ID
**orderNumber** | number | Order number
**itemId** | number | Order item ID
**optionName** | string | Item product option name, e.g. `Upload your photo`
fileName |  string |  Uploaded file name
**token** |  string |  oAuth token

### Response

> Response example

```json
{
    "id": 6005003
}
```

A JSON object of type 'UploadStatus' with the following fields:

#### UploadStatus
Field | Type |  Description
--------- | ---------| -----------
id | number | Internal file ID

### Errors

> Error response example 

```http
HTTP/1.1 404 Not Found
Content-Type application/json; charset=utf-8
```

In case of error, Ecwid responds with an error HTTP status code and JSON-formatted body containing error description

#### HTTP codes

**HTTP Status** | Description
--------- | -----------| -----------
500 | Uploading of the file failed or there was an internal server error while processing a file
404 | Order, order item or item option is not found
413 | The file is too large
400 | Request parameters are malformed
402 | The functionality/method is not available on the merchant plan

#### Error response body (optional)

Field | Type |  Description
--------- | ---------| -----------
errorMessage | string | Error message


## Delete item option file

Using this method, you can remove a file attached to an order item by customer.

> Request example

```http
DELETE /api/v3/4870020/orders/1234657/items/987653/options/Attach+your+image/files/{fileId}&token=123456789abcd HTTP/1.1
Host: app.ecwid.com
Content-Type: application/json
Cache-Control: no-cache
```

`DELETE https://app.ecwid.com/api/v3/{storeId}/orders/{orderNumber}/items/{itemId}/options/{optionName}?fileName={fileName}token={token}`

Name | Type    | Description
---- | ------- | -----------
**storeId** |  number | Ecwid store ID
**orderNumber** | number | Order number
**itemId** | number | Order item ID
**optionName** | string | Item product option name, e.g. `Upload your photo`
**fileId** | number | Option file's internal ID
**token** |  string |  oAuth token

### Response

> Response example

```json
{
    "deleteCount": 1,
    "success": true
}
```

A JSON object of type 'DeleteStatus' with the following fields:

#### DeleteStatus
Field | Type |  Description
----- | ---- | --------------
deleteCount | number | The number of deleted files (`1` or `0` depending on whether the request was successful)
success | boolean | `true` if the file has been deleted, `false` otherwise

### Errors

> Error response example 

```http
HTTP/1.1 404 Not Found
Content-Type application/json; charset=utf-8
```

In case of error, Ecwid responds with an error HTTP status code and JSON-formatted body containing error description

#### HTTP codes

**HTTP Status** | Description
--------- | -----------| -----------
500 | Request failed -- there was an internal server error
404 | Order, order item or item option is not found
400 | Request parameters are malformed
402 | The functionality/method is not available on the merchant plan

#### Error response body (optional)

Field | Type |  Description
--------- | ---------| -----------
errorMessage | string | Error message

