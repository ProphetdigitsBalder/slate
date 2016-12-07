# Balance

## Search Balance Report

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/balance/search` |
| Method | `post` |
| Use | to get weekly balance report between start time and end time. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "start_time": 1469577600,
  "end_time": ""
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| start_date | timestamp | the start date of searching |
| end_date | timestamp | the end date of searching one year is max difference between start time and end time |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
  "reports": [{
    "id": 1,
    "start_time": 1469577600,
    "end_time": 1469587600
    }, {
    "id": 2,
    "start_time": 1469587600,
    "end_time": 1469597600
  }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **reports** | **array** |  |
| id | integer | report id |
| start_time | timestamp | the start date of report |
| end_time | timestamp | if today not last day of week then end time is now otherwise is the last day of week |

<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** the request does not include the necessary parameters |
|||**does not signin:** user does not signin |
|||**not select company yet:** user need change current company |
|||**company not exist:** currenct company not exist |
|||**not company member:** the user is not the company member |
|||**no permission:**cannot search balance report |


## Show Balance Report Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/balance/detail` |
| Method | `post` |
| Use | to get report detail. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "report_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| report_id | integer | report id |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
  "id": 1,
  "start_time": 1469577600,
  "end_time": 1469587600,
  "summary": [{
    "currency": "TWD",
    "previous_balance": 0,
    "new_balance": -28734.4,
    "adjustment": -0.4,
    "current_balance": -28734,
    "due_date": 1470587600,
    "payment_status": "Open"
  }],
  "detail": [{
    "order_date": 1469577800,
    "retailer": "CITIZEN",
    "brand": "HORAGE",
    "item": "Solor Wind",
    "variant": "L 33mm SS-B",
    "product": "HORA001PD",
    "currency": "TWD",
    "sell_price": 143672,
    "discount": 20,
    "payment_method": "credit_card",
    "deposit": 0,
    "vat": 0,
    "other_cost": 0,
    "shareable": 143672,
    "sharing": 40,
    "net_income": 57468.8,
    "balance": 57468.8
  },{
    "order_date": 1469577800,
    "retailer": "CITIZEN",
    "brand": "HORAGE",
    "item": "Solor Wind",
    "variant": "L 33mm SS-B",
    "product": "HORA001PD",
    "currency": "TWD",
    "sell_price": 143672,
    "discount": 20,
    "payment_method": "cash",
    "deposit": 0,
    "vat": 0,
    "other_cost": 0,
    "shareable": 143672,
    "sharing": 40,
    "net_income": 57468.8,
    "balance": -86203.2
  }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **reports** | **array** |  |
| id | integer | report id |
| start_time | timestamp | the start date of report |
| end_time | timestamp | if today not last day of week then end time is now otherwise is the last day of week |
| **summary** | **array** |  |
| currency | string | curency name |
| previous_balance | double | the balances of rounding in last report |
| new_balance | double | the total price of currency |
| adjustment | double | the balances of rounding in thisreport |
| correct_balance | double | a rounding price |
| due_date | timestamp | the due date of transferring money |
| payment_status | string | after due date, if company finished transfer money status will be "Paid" otherwise be "Expired" |
| **detail** | **array** |  |
| order_date | timestamp | date of product sold |
| retailer | string | product be sold by which company |
| brand | string | product be manufactured by which company |
| item | string | item name that product belongs |
| variant | string | variant name that product belongs |
| product | string | product number |
| currency | string | currency of product selling price |
| sell_price | double | selling price of product |
| discount | integer | discount of product |
| payment_method | string | payment method |
| deposit | double | product deposit |
| vat | integer | product vat |
| other_cost | double | other cost of product |
| shareable | double | shareable price |
| sharing | integer | sharing percent of option with brand  |
| net_income | double | net income of product |
| balance | double | the price by payment method to know that transfer to brandcloud or receive from brandcloud  |

<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** the request does not include the necessary parameters |
|||**does not signin:** user does not signin |
|||**not select company yet:** user need change current company |
|||**company not exist:** currenct company not exist |
|||**not company member:** the user is not the company member |
|||**no permission:**cannot search balance report |