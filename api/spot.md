# Spot

<figure><img src="../.gitbook/assets/Spot (1).png" alt=""><figcaption></figcaption></figure>

## Spot

**Public**

**Security: None​**

Endpoints under **Public** section can be accessed freely without requiring any API-key or signatures.

{% swagger method="get" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/ping" summary="Test Connectivity" %}
{% swagger-description %}
This endpoint checks connectivity to the host
{% endswagger-description %}

{% swagger-response status="200: OK" description="connection Normal" %}
```javascript
{}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/time" summary="Check Server Time" %}
{% swagger-description %}
This endpoint checks connectivity to the server and retrieves server timestamp
{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "timezone": "GMT+08:00",
    "serverTime": 1595563624731
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/symbols" summary="Pairs List" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}


```
{
    "symbols": [
        {
            "quantityPrecision": 3,
            "symbol": "sccadai",
            "pricePrecision": 6,
            "baseAsset": "SCCA",
            "quoteAsset": "DAI"
        },
        {
            "quantityPrecision": 8,
            "symbol": "btcusdt",
            "pricePrecision": 2,
            "baseAsset": "BTC",
            "quoteAsset": "USDT"
        },
        {
            "quantityPrecision": 3,
            "symbol": "bchusdt",
            "pricePrecision": 2,
            "baseAsset": "BCH",
            "quoteAsset": "USDT"
        },
        {
            "quantityPrecision": 2,
            "symbol": "etcusdt",
            "pricePrecision": 2,
            "baseAsset": "ETC",
            "quoteAsset": "USDT"
        },
        {
            "quantityPrecision": 2,
            "symbol": "ltcbtc",
            "pricePrecision": 6,
            "baseAsset": "LTC",
            "quoteAsset": "BTC"
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

**Response:**

|                   |         |         |                                 |
| ----------------- | ------- | ------- | ------------------------------- |
| name              | type    | example | description                     |
| symbol            | string  | BTCUSDT | Name of the symbol              |
| baseAsset         | string  | BTC     | Underlying asset for the symbol |
| quoteAsset        | string  | USDT    | Quote asset for the symbol      |
| pricePrecision    | integer | 2       | Precision of the price          |
| QuantityPrecision | integer | 6       | Precision of the quantity       |

**Market**

**Security Type: None​**

**Market** section can be accessed freely without requiring any API-key or signatures.

{% swagger method="get" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/depth" summary="Depth" %}
{% swagger-description %}
market depth data
{% endswagger-description %}

{% swagger-parameter in="query" name="limit" type="integer" %}
Default 100; Max 100
{% endswagger-parameter %}

{% swagger-parameter in="query" name="symbol" type="string" %}
Symbol Name E.g. BTCUSDT
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "bids": [
    [
      "3.90000000",   // price
      "431.00000000"  // vol
    ],
    [
      "4.00000000",
      "431.00000000"
    ]
  ],
  "asks": [
    [
      "4.00000200",  // price
      "12.00000000"  // vol
    ],
    [
      "5.10000000",
      "28.00000000"
    ]
  ]
}
```
{% endswagger-response %}
{% endswagger %}

**Response:**

|      |      |                 |                                                                 |
| ---- | ---- | --------------- | --------------------------------------------------------------- |
| name | type | example         | description                                                     |
| time | long | `1595563624731` | Current timestamp (ms)                                          |
| bids | list | ;               | List of all bids, best bids first. See below for entry details. |
| asks | list | ;               | List of all asks, best asks first. See below for entry details. |

The fields bids and asks are lists of order book price level entries, sorted from best to worst.

|      |       |         |                                                   |
| ---- | ----- | ------- | ------------------------------------------------- |
| name | type  | example | description                                       |
| ' '  | float | 131.1   | price level                                       |
| ' '  | flot  | 2.3     | The total quantity of orders for this price level |

{% swagger method="get" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/ticker" summary="24hrs ticker" %}
{% swagger-description %}
24 hour price change statistics.
{% endswagger-description %}

{% swagger-parameter in="query" name="symbol" type="string" %}
Symbol Name. E.g. `BTCUSDT`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successfully retrieved ticker data  " %}
```javascript
{
    "high": "9279.0301",
    "vol": "1302",
    "last": "9200",
    "low": "9279.0301",
    "rose": "0",
    "time": 1595563624731
}
```
{% endswagger-response %}
{% endswagger %}

**Response:**

|      |       |                 |              |
| ---- | ----- | --------------- | ------------ |
| name | type  | `example`       | description  |
| time | long  | `1595563624731` | Open Time    |
| high | float | `9900`          | High Price   |
| low  | float | `8800.34`       | Low Price    |
| last | float | `8900`          | Last Price   |
| vol  | float | `4999`          | Tarde Volume |

{% swagger method="get" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/trades" summary="Recent Trades List" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" type="String" required="true" name="symbol" %}
Symbol Name. E.g. `BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="query" type="integer" name="limit" %}
default 100, maximum 1000
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}


```
{
    "list": [
        {
            "symbol": "BTCUSDT",
            "side": "SELL",
            "price": "42861.8",
            "qty": "0.004",
            "id": 88438312,
            "time": 1647954895340
        },
        {
            "symbol": "BTCUSDT",
            "side": "SELL",
            "price": "42863",
            "qty": "0.06",
            "id": 88438311,
            "time": 1647954895329
        },
        {
            "symbol": "BTCUSDT",
            "side": "BUY",
            "price": "42863.75",
            "qty": "0.132398",
            "id": 88438310,
            "time": 1647954895311
        },
        {
            "symbol": "BTCUSDT",
            "side": "SELL",
            "price": "42863.86",
            "qty": "0.132722",
            "id": 88438309,
            "time": 1647954894649
        },
        {
            "symbol": "BTCUSDT",
            "side": "SELL",
            "price": "42863.01",
            "qty": "0.128545",
            "id": 88438308,
            "time": 1647954893552
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

**Response:**

|       |        |                 |                        |
| ----- | ------ | --------------- | ---------------------- |
| name  | type   | example         | description            |
| price | float  | 0.055           | The price of the trade |
| time  | long   | `1537797044116` | Current timestamp (ms) |
| qty   | float  | 5               | The quantity traded    |
| side  | string | BUY/SELL        | Taker side             |

{% swagger method="get" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/klines" summary="Kline/candlestick data" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="symbol" type="string" %}
Symbol Name. E.g. `BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="interval" type="string" %}
\
Interval of the Kline. Possible values include: `1min`,`5min`,`15min`,`30min`,`60min`,`1day`,`1week`,`1month`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="integer" %}
Default 100; Max 300
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
[
    {
        "high": "6228.77",
        "vol": "111",
        "low": "6228.77",
        "idx": 1594640340,
        "close": "6228.77",
        "open": "6228.77"
    },
    {
        "high": "6228.77",
        "vol": "222",
        "low": "6228.77",
        "idx": 1587632160,
        "close": "6228.77",
        "open": "6228.77"
    },
    {
        "high": "6228.77",
        "vol": "333",
        "low": "6228.77",
        "idx": 1587632100,
        "close": "6228.77",
        "open": "6228.77"
    }
]
```
{% endswagger-response %}
{% endswagger %}

**Response:**

|       |       |               |             |
| ----- | ----- | ------------- | ----------- |
| 名称    | 类型    | 例子            | 描述          |
| idx   | long  | 1538728740000 | Open time   |
| open  | float | 36.00000      | open price  |
| close | float | 33.00000      | close price |
| high  | float | 36.00000      | high price  |
| low   | float | 30.00000      | low price   |
| vol   | float | 2456.111      | volume      |
|       |       |               |             |

**Trade**

**Security Type: TRADE​**

Endpoints under **Trade** require an API-key and a signature.​

{% swagger method="post" path="" baseUrl="  https://openapi.lyotrade.com/sapi/v1/order " summary="New Order" %}
{% swagger-description %}
**Rate Limit: 100times/2s**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="integer" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" type="string" %}
Symbol Name. E.g. `BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="volume" type="number" %}
Order vol. For MARKET BUY orders,  vol=amount.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="side" type="string" %}
Side of the order,`BUY/SELL`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
Type of the order, `LIMIT/MARKET`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type=" number" %}
Order price, REQUIRED for LIMIT orders
{% endswagger-parameter %}

{% swagger-parameter in="body" name="newClientOrderId" type="string" %}
Unique order ID generated by users to mark their orders
{% endswagger-parameter %}

{% swagger-parameter in="body" name="recvWindow" type="integer" %}
Time window
{% endswagger-parameter %}

{% swagger-response status="200: OK" description=" Successsfully post new order" %}
```javascript
{
    'symbol': 'LXTUSDT', 
    'orderId': '150695552109032492', 
    'clientOrderId': '157371322565051',
    'transactTime': '1573713225668', 
    'price': '0.005452', 
    'origQty': '110', 
    'executedQty': '0', 
    'status': 'NEW',
    'type': 'LIMIT', 
    'side': 'SELL'
}
```
{% endswagger-response %}
{% endswagger %}

**Response:**

<table><thead><tr><th></th><th></th><th width="207"></th><th></th></tr></thead><tbody><tr><td>name</td><td>type</td><td>example</td><td>description</td></tr><tr><td>orderId</td><td>long</td><td>150695552109032492</td><td>ID of the order</td></tr><tr><td>clientOrderId</td><td>string</td><td>213443</td><td>A unique ID of the order.</td></tr><tr><td>symbol</td><td>string</td><td>BTCUSDT</td><td>Symbol Name</td></tr><tr><td>transactTime</td><td>integer</td><td>1273774892913</td><td>Time the order is placed</td></tr><tr><td>price</td><td>float</td><td>4765.29</td><td>Price of the order</td></tr><tr><td>origQty</td><td>float</td><td>1.01</td><td>Quantity ordered</td></tr><tr><td>executedQty</td><td>float</td><td>1.01</td><td>Quantity of orders that has been executed</td></tr><tr><td>type</td><td>string</td><td>LIMIT</td><td>Order type LIMIT,MARKET</td></tr><tr><td>side</td><td>string</td><td>BUY</td><td>Order side：BUY, SELL</td></tr><tr><td>status</td><td>string</td><td>NEW</td><td>The state of the order.Possible values include NEW, PARTIALLY_FILLED, FILLED, CANCELED, and REJECTED.</td></tr></tbody></table>

{% swagger method="post" path="" baseUrl=" https://openapi.lyotrade.com/sapi/v1/order/test" summary="Test New Order" %}
{% swagger-description %}
Test new order creation and signature/recvWindow length. Creates and validates a new order but does not send the order into the matching engine.
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="integer" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="recWindow" type="integer" %}
Time window
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" type="string" %}
Symbol Name. E.g. `BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="volume" type="number" %}
Order vol. For MARKET BUY orders, vol=amount.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="side" type="string" %}
Side of the order, `BUY/SELL`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
Type of the order, `LIMIT/MARKET`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type="number" %}
Order price, REQUIRED for `LIMIT` orders
{% endswagger-parameter %}

{% swagger-parameter in="body" name="newClientOrderId" type="string" %}
Unique order ID generated by users to mark their orders
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/batchOrders" summary="Batch Orders" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string " %}
&#x20;Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS " type="integer " %}
imestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="orders" type="array  " %}
Batch order param
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" type="string  " %}
Symbol Name. E.g. `BTCUSDT`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "ids": [
        165964665990709251,
        165964665990709252,
        165964665990709253
    ]
}
```
{% endswagger-response %}
{% endswagger %}

**Request orders field:**

|           |        |              |                        |
| --------- | ------ | ------------ | ---------------------- |
| name      | type   | example      | description            |
| price     | folat  | 1000         | Price of the order     |
| volume    | folat  | 20.1         | Vol of the order       |
| side      | string | BUY/SELL     | Side of the order      |
| batchType | string | LIMIT/MARKET | atch type of the order |

{% swagger method="get" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/order" summary="Query Order" %}
{% swagger-description %}
**Rate Limit:20 times/2s**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="query" name="orderId " type="string " %}
Order ID
{% endswagger-parameter %}

{% swagger-parameter in="query" name="newClientOrderId " type="string " %}
Client Order Id, Unique order ID generated by users to mark their orders. E.g. 354444heihieddada
{% endswagger-parameter %}

{% swagger-parameter in="query" name="symbol" type="string " %}
Symbol Name. E.g. `BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS " type="integer" %}
timestamp
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    'orderId': '499890200602846976', 
    'clientOrderId': '157432755564968', 
    'symbol': 'BHTUSDT', 
    'price': '0.01', 
    'origQty': '50', 
    'executedQty': '0', 
    'avgPrice': '0', 
    'status': 'NEW', 
    'type': 'LIMIT', 
    'side': 'BUY', 
    'transactTime': '1574327555669'
}
```
{% endswagger-response %}
{% endswagger %}

**Response:**

|               |        |                    |                                                                                                        |
| ------------- | ------ | ------------------ | ------------------------------------------------------------------------------------------------------ |
| **n**ame      | type   | example            | description                                                                                            |
| orderId       | long   | 150695552109032492 | ID of the order                                                                                        |
| clientOrderId | string | 213443             | Unique ID of the order.                                                                                |
| symbol        | string | BTCUSDT            | Name of the symbol                                                                                     |
| price         | float  | 4765.29            | Price of the order                                                                                     |
| origQty       | float  | 1.01               | Quantity ordered                                                                                       |
| executedQty   | float  | 1.01               | Quantity of orders that has been executed                                                              |
| avgPrice      | float  | 4754.24            | Average price of filled orders.                                                                        |
| type          | string | LIMIT              | The order typeLIMIT,MARKET                                                                             |
| side          | string | BUY                | The order sideBUY,SELL                                                                                 |
| status        | string | NEW                | The state of the order.Possible values include NEW, PARTIALLY\_FILLED, FILLED, CANCELED, and REJECTED. |

{% swagger method="post" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/cancel" summary="Cancel Order" %}
{% swagger-description %}
**Rate Limit: 100time/2s**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN " type="string" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY " type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS " type="integer" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="orderId" type="string" %}
Order ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="newClientOrderId" type="string" %}
Client Order Id, Unique order ID generated by users to mark their orders. E.g. 354444heihieddada
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" type="string" %}
Symbol Name. E.g. `BTCUSDT`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="撤销订单成功" %}
```javascript
{
    'symbol': 'BHTUSDT', 
    'clientOrderId': '0', 
    'orderId': '499890200602846976', 
    'status': 'CANCELED'
}
```
{% endswagger-response %}
{% endswagger %}

**Response:**

|               |        |                    |                                                                                                        |
| ------------- | ------ | ------------------ | ------------------------------------------------------------------------------------------------------ |
| name          | type   | example            | description                                                                                            |
| orderId       | long   | 150695552109032492 | ID of the order                                                                                        |
| clientOrderId | string | 213443             | Unique ID of the order.                                                                                |
| symbol        | string | BHTUSDT            | Name of the symbol                                                                                     |
| status        | string | NEW                | The state of the order.Possible values include NEW, PARTIALLY\_FILLED, FILLED, CANCELED, and REJECTED. |

{% swagger method="post" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/batchCancel" summary="Batch cancel orders" %}
{% swagger-description %}
**Rate Limit: 50times/2s A batch contains at most 10 orders**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS " type="integer" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" type="string" name="symbol" %}
Symbol Name. E.g. `BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="body" type="array" name="orderId" %}
Order ID collection `[123,456]`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "success": [
        165964665990709251,
        165964665990709252,
        165964665990709253
    ],
    "failed": [ //cancel fails because the order does not exist or the order state has expired
        165964665990709250  
    ]
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/openOrders" summary="Current Open Orders" %}
{% swagger-description %}
**Rate Limit: 20times/2s**
{% endswagger-description %}

{% swagger-parameter in="query" name="symbol" type="string" %}
Symbol Name. E.g. `BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="integer" %}
Default 100; Max 1000
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="integer" %}
timestamp
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
[
    {
        'orderId': '499902955766523648', 
        'symbol': 'BHTUSDT', 
        'price': '0.01', 
        'origQty': '50', 
        'executedQty': '0', 
        'avgPrice': '0', 
        'status': 'NEW', 
        'type': 'LIMIT', 
        'side': 'BUY', 
        'time': '1574329076202'
        },...
]
```
{% endswagger-response %}
{% endswagger %}



**Response:**

|               |        |                    |                                                                                                        |
| ------------- | ------ | ------------------ | ------------------------------------------------------------------------------------------------------ |
| name          | type   | example            | description                                                                                            |
| orderId       | long   | 150695552109032492 | ID of the order                                                                                        |
| clientOrderId | string | 213443             | Unique ID of the order.                                                                                |
| symbol        | string | BTCUSDT            | Name of the symbol                                                                                     |
| price         | float  | 4765.29            | Price of the order                                                                                     |
| origQty       | float  | 1.01               | Quantity ordered                                                                                       |
| executedQty   | float  | 1.01               | Quantity of orders that has been executed                                                              |
| avgPrice      | float  | 4754.24            | Average price of filled orders.                                                                        |
| type          | string | LIMIT              | The order typeLIMIT,MARKET                                                                             |
| side          | string | BUY                | The order side BUY,SELL                                                                                |
| status        | string | NEW                | The state of the order.Possible values include NEW, PARTIALLY\_FILLED, FILLED, CANCELED, and REJECTED. |

{% swagger method="get" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/myTrades" summary="Trades" %}
{% swagger-description %}
**Rate Limit:20 times/2s**
{% endswagger-description %}

{% swagger-parameter in="query" name="symbol" type="string" %}
Symbol Name. E.g. `BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="string" %}
Default 100; Max1000
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fromId" type="integer" %}
Trade Id to fetch from
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="integer" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
[
  {
    "symbol": "ETHBTC",
    "id": 100211,
    "bidId": 150695552109032492,
    "askId": 150695552109032493,
    "price": "4.00000100",
    "qty": "12.00000000",
    "time": 1499865549590,
    "isBuyer": true,
    "isMaker": false,
    "feeCoin": "ETH",
    "fee":"0.001"
  },...
]
```
{% endswagger-response %}
{% endswagger %}

**Response:**

|         |         |                    |                           |
| ------- | ------- | ------------------ | ------------------------- |
| name    | type    | example            | description               |
| symbol  | string  | ETHBTC             | Symbol Name               |
| id      | integer | 28457              | Trade ID                  |
| bidId   | long    | 150695552109032492 | Bid Order ID              |
| askId   | long    | 150695552109032493 | Ask Order ID              |
| price   | integer | 4.01               | Price of the trade        |
| qty     | float   | 12                 | Quantiry of the trade     |
| time    | number  | 1499865549590      | timestamp of the trade    |
| isBuyer | bool    | true               | true= Buyer false= Seller |
| isMaker | bool    | false              | true=Maker false=Taker    |
| feeCoin | string  | ETH                | Trading fee coin          |
| fee     | number  | 0.001              | Trading fee               |

**Account**

**Security Type: USER\_DATA​**

Endpoints under Account require an API-key and a signature.​

{% swagger method="get" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/account" summary="Account Information" %}
{% swagger-description %}
**Rate Limit:"20times/2s**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="integer" %}
timestamp
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successfully retrieved account information" %}
```javascript
{
    'balances': 
        [
            {
                'asset': 'BTC', 
                'free': '0', 
                'locked': '0'
                }, 
            {
                'asset': 'ETH', 
                'free': '0', 
                'locked': '0'
                },...
        ]
}
```
{% endswagger-response %}
{% endswagger %}

**Response:**

|          |      |                      |
| -------- | ---- | -------------------- |
| 名称       | 类型   | 描述                   |
| balances | \[ ] | Show balance details |

balances field:

|        |        |         |                                 |
| ------ | ------ | ------- | ------------------------------- |
| name   | type   | example | description                     |
| asset  | string | USDT    | Name of the asset               |
| free   | float  | 1000.30 | Amount available for use        |
| locked | float  | 400     | Amount locked (for open orders) |
