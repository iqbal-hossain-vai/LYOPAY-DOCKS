# Contract

<figure><img src="../.gitbook/assets/Contract (1).png" alt=""><figcaption></figcaption></figure>

## Contract

### Public

### Security: None

Endpoints under **Public** section can be accessed freely without requiring any API-key or signatures

{% swagger method="get" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/ping" summary="Test Connectivity" %}
{% swagger-description %}
&#x20;This endpoint checks connectivity to the host
{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/time" summary="Check Server Time" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "serverTime":1607702400000,
    "timezone":Chinese standard time
}
```
{% endswagger-response %}
{% endswagger %}

**Response**

|            |        |                     |                   |
| ---------- | ------ | ------------------- | ----------------- |
| name       |  type  | example             | description       |
| serverTime |   long | 1607702400000       | server timestamp  |
| timezone   | string | China standard time |  server time zone |

{% swagger method="get" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/contracts" summary="" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
[
    {
        "symbol": "H-HT-USDT",
        "pricePrecision": 8,
        "side": 1,
        "maxMarketVolume": 100000,
        "multiplier": 6,
        "minOrderVolume": 1,
        "maxMarketMoney": 10000000,
        "type": "H",
        "maxLimitVolume": 1000000,
        "maxValidOrder": 20,
        "multiplierCoin": "HT",
        "minOrderMoney": 0.001,
        "maxLimitMoney": 1000000,
        "status": 1
    }
]
```
{% endswagger-response %}
{% endswagger %}

#### **Response:** <a href="#response-2" id="response-2"></a>

|                 |        |              |                                                                                   |
| --------------- | ------ | ------------ | --------------------------------------------------------------------------------- |
| symbol          | number | `E-BTC-USDT` | Contract Name                                                                     |
| status          | string | 1            | status（0：cannot trade，1：can trade                                                 |
| type            | number | S            | contract type, E: perpetual contract, S: test contract, others are mixed contract |
| side            | number | 1            | Contract direction(backwards：0，1：forward)                                         |
| multiplier      | string | 0.5          | Contract face value                                                               |
| multiplierCoin  | number | BTC          | Contract face value unit                                                          |
| pricePrecision  | number | 4            | Precision of the price                                                            |
| minOrderMoney   | number | 10           | Minimum order volume                                                              |
| minOrderVolume  | number | 10           | Minimum order value                                                               |
| maxMarketVolume | number | 100000       | Market price order maximum volume                                                 |
| maxMarketMoney  | number | 100000       | Market price order maximum value                                                  |
| macLimitVolume  | number | 100000       | Limit price order maximum volume                                                  |
| maxValidOrder   | number | 100000       | Maximum valid order quantity                                                      |

## Market <a href="#hang-qing-xiang-guan" id="hang-qing-xiang-guan"></a>

### Security: None​ <a href="#an-quan-lei-xing-none-1" id="an-quan-lei-xing-none-1"></a>

Market section can be accessed freely without requiring any API-key or signatures.

{% swagger method="get" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/depth" summary="Depth" %}
{% swagger-description %}
Market Depth Data
{% endswagger-description %}

{% swagger-parameter in="query" name="Limit" type="Integer" required="true" %}
Default 100, Max 100
{% endswagger-parameter %}

{% swagger-parameter in="query" name="Contract Name" type="String" required="true" %}
Contract Name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "bids": [
    [
      "3.90000000",   // price
      "431.00000000"  // quantity
    ],
    [
      "4.00000000",
      "431.00000000"
    ]
  ],
  "asks": [
    [
      "4.00000200",  // price
      "12.00000000"  // quantity
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

#### Response: <a href="#response-2" id="response-2"></a>

|      |      |               |                          |
| ---- | ---- | ------------- | ------------------------ |
| name | type | example       | description              |
| time | long | 1595563624731 | Current Timestamp  (ms)  |
| bids | list | Look below    | Order book purchase info |
| asks | list | Look below    | Order book selling info  |

The fields bids and asks are lists of order book price level entries, sorted from best to worst.

|      |       |         |                                           |
| ---- | ----- | ------- | ----------------------------------------- |
| name | type  | example | description                               |
| ' '  | float | 131.1   | price level                               |
| ' '  | float | 2.3     | Total order quantity for this price level |

{% swagger method="get" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/ticker" summary="24 hrs ticker" %}
{% swagger-description %}
24 hr price change statistics
{% endswagger-description %}

{% swagger-parameter in="query" name="contract name" type="string" %}
Contract  name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successfully obtain ticker info" %}
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

**Response**

|      |        |                 |                 |
| ---- | ------ | --------------- | --------------- |
| name | type   | `example`       | description     |
| time | long   | `1595563624731` | Open time       |
| high | float  | 9900            | Higher price    |
| low  | float  | 8800.34         | Lower price     |
| last | float  | 8900            | Newest price    |
| vol  | float  | 4999            | Trade volume    |
| rose | string | +0.5            | Price variation |

{% swagger method="get" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/index" summary="Get index//marked price" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="Contact name" type="string" %}


Contract name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="string" %}
Default 100, Max 100
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "markPrice": 581.5,
    "indexPrice": 646.3933333333333,
    "lastFundingRate": 0.001,
    "contractName": "E-ETH-USDT",
    "time": 1608273554063
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/klines" summary="" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="ContractName" type="string" %}
Contract name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-parameter in="query" name="interval" type="string" %}
K-line interval, identifies the sent value as: `1min`,`5min`,`15min`,`30min`,`1h`,`1day`,`1week`,`1month`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="integer" %}
Default 100, Max 300
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

#### **Response:**

|       |       |               |                      |
| ----- | ----- | ------------- | -------------------- |
| name  | type  | example       | description          |
| idx   | long  | 1538728740000 | Start timestamp (ms） |
| open  | float | 36.00000      | Open price           |
| close | float | 33.00000      | `Closing price`      |
| high  | float | 36.00000      | `Max price`          |
| low   | float | 30.00000      | `Min price`          |
| vol   | float | 2456.111      | Trade volume         |

## Trading <a href="#jiao-yi-xiang-guan" id="jiao-yi-xiang-guan"></a>

### Security: TRADE​ <a href="#an-quan-lei-xing-trade" id="an-quan-lei-xing-trade"></a>

All interfaces under the transaction require signature and API-key verification​​

{% swagger method="post" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/order" summary="Order creation" %}
{% swagger-description %}
Creation of single new orders
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-TS" type="string" %}
Time stamp
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Signature
{% endswagger-parameter %}

{% swagger-parameter in="body" name="volume" type="number" %}
order quantity
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type="number" %}
Order price
{% endswagger-parameter %}

{% swagger-parameter in="body" name="contractName" type="string" %}
Contract name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
Order type, `LIMIT/MARKET`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="side" type="string" %}
trade direction, `BUY/SELL`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="open" type="string" %}
Open balancing direction, `OPEN/CLOSE`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="positionType" type="number" %}
\
Hold-up position, `1 full position, 2 restrictive position`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="clientOrderId" type="string" %}
Client order identity, a string with length less than 32 bit
{% endswagger-parameter %}

{% swagger-parameter in="body" name="timeInForce" type="string" %}
IOC, FOK, POST\_ONLY
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "orderId": 256609229205684228
}
```
{% endswagger-response %}
{% endswagger %}

**Response:**

|         |        |                    |             |
| ------- | ------ | ------------------ | ----------- |
| name    | type   | example            | description |
| orderId | String | 256609229205684228 | Order ID    |

{% swagger method="post" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/conditionOrder" summary="Condition order creation" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-TS" type="string" %}
Time stamp
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Signature
{% endswagger-parameter %}

{% swagger-parameter in="body" name="volume" type="number" %}
Order quantity
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type="number" %}
Order price
{% endswagger-parameter %}

{% swagger-parameter in="body" name="contractName" type="string" %}
Contract name E.g. `E-BTC-USDT`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
Order type, `LIMIT/MARKET`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="side" type="string" %}
trade direction, `BUY/SELL`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="open" type="string" %}
Open balancing direction, `OPEN/CLOSE`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="positionTyper" type="string" %}
Hold-up position, `1 full position, 2 restrictive position`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="triggerPrice" type="string" %}
trigger price
{% endswagger-parameter %}

{% swagger-parameter in="body" name="triggerType" type="string" %}
\
trigger type `3UP/4DOWN`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
     "orderId": 256609229205684228
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="https://openapi.lyotrade.com/sapi/v1/cancel" summary="Cancel order" %}
{% swagger-description %}
Speed limit rules: 20 times/ 2 seconds
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Signature
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="integer" %}
Time stamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="contractName" type="string" %}
Contract name E.g. `E-BTC-USDT`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="orderId" type="string" %}
Order ID
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "orderId": 256609229205684228
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/order" summary="Order details" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="contractName" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
[
    {
       "side": "BUY",
       "executedQty": 0,
       "orderId": 259396989397942275,
       "price": 10000.0000000000000000,
       "origQty": 1.0000000000000000,
       "avgPrice": 0E-8,
       "transactTime": "1607702400000",
       "action": "OPEN",
       "contractName": "E-BTC-USDT",
       "type": "LIMIT",
       "status": "INIT"
    }
]

```
{% endswagger-response %}
{% endswagger %}

#### Response:

|              |        |                      |                                                                                                                                                                                       |
| ------------ | ------ | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name         | type   | example              | description                                                                                                                                                                           |
| orderId      | long   | `150695552109032492` | Order ID（system generated                                                                                                                                                             |
| contractName | string | E-BTC-USDT           | Contract name                                                                                                                                                                         |
| price        | float  | 10.5                 | Order price                                                                                                                                                                           |
| origQty      | float  | 10.5                 | Order quantity                                                                                                                                                                        |
| executedQty  | float  | 20                   | Order quantity                                                                                                                                                                        |
| avgPrice     | float  | 10.5                 | Average transaction price                                                                                                                                                             |
| symbol       | string | BHTUSDT              | Coin pair name                                                                                                                                                                        |
| status       | string | NEW                  | Order status. Possible values are：`NEW`(new order，not filled)、`PARTIALLY_FILLED`（partially filled）、`FILLED`（fully filled）、`CANCELLED`（already cancelled）and`REJECTED`（order rejected） |
| side         | string | NEW                  | Order direction. Possible values can only be：BUY（buy long）and SELL（sell short）                                                                                                        |
| action       | string | OPEN                 | OPEN / CLOSE                                                                                                                                                                          |
| transactTime | long   | 1607702400000        | Order creation time                                                                                                                                                                   |
|              |        |                      |                                                                                                                                                                                       |

{% swagger method="get" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/openOrders" summary="" %}
{% swagger-description %}
**Speed limit rules:**\
**Obtain open contract, the user's current order**
{% endswagger-description %}

{% swagger-parameter in="query" name="contractname" type="string" %}
Contract name `E-BTC-USDT`
{% endswagger-parameter %}

{% swagger-parameter in="header" type="string" name="X-CH-SIGN" %}
signature
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="string" %}
time stamp
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
[
    {
       "side": "BUY",
       "executedQty": 0,
       "orderId": 259396989397942275,
       "price": 10000.0000000000000000,
       "origQty": 1.0000000000000000,
       "avgPrice": 0E-8,
       "transactTime": "1607702400000",
       "action": "OPEN",
       "contractName": "E-BTC-USDT",
       "type": "LIMIT",
       "status": "INIT"
    }
]
```
{% endswagger-response %}
{% endswagger %}

#### **Response:**

|              |        |                      |                                                                                                                                                                                       |
| ------------ | ------ | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name         | type   | example              | description                                                                                                                                                                           |
| orderId      | long   | `150695552109032492` | Order ID（system generated）                                                                                                                                                            |
| contractName | string | `E-BTC-USDT`         | Contract name                                                                                                                                                                         |
| price        | float  | 4765.29              | Order price                                                                                                                                                                           |
| origQty      | float  | 1.01                 | Order quantity                                                                                                                                                                        |
| executedQty  | float  | 1.01                 | Filled orders quantity                                                                                                                                                                |
| avgPrice     | float  | 4754.24              | Filled orders average price                                                                                                                                                           |
| type         | string | LIMIT                | Order type. Possible values can only be:`LIMIT`(limit price) and`MARKET`（market price）                                                                                                |
| side         | string | BUY                  | Order direction. Possible values can only be：`BUY`（buy long）and `SELL`（sell short）                                                                                                    |
| status       | string | NEW                  | Order status. Possible values are：`NEW`(new order，not filled)、`PARTIALLY_FILLED`（partially filled）、`FILLED`（fully filled）、`CANCELLED`（already cancelled）and`REJECTED`（order rejected） |
| action       | string | OPEN                 | OPEN / CLOSE                                                                                                                                                                          |
| transactTime | long   | 1607702400000        | Order creation time,                                                                                                                                                                  |

{% swagger method="post" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/orderHistorical" summary="order history" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
signature
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="string" %}
time stamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="contractName" type="string" %}
Contract name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-parameter in="body" name="limit" type="string" %}
Lines per page, default 100, max 1000
{% endswagger-parameter %}

{% swagger-parameter in="body" name="fromId" type="long" %}
Start retrieving from this Id
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
[
    {
        "side":"BUY",
        "clientId":"0",
        "ctimeMs":1632903411000,
        "positionType":2,
        "orderId":777293886968070157,
        "avgPrice":41000,
        "openOrClose":"OPEN",
        "leverageLevel":26,
        "type":4,
        "closeTakerFeeRate":0.00065,
        "volume":2,
        "openMakerFeeRate":0.00025,
        "dealVolume":1,
        "price":41000,
        "closeMakerFeeRate":0.00025,
        "contractId":1,
        "ctime":"2021-09-29T16:16:51",
        "contractName":"E-BTC-USDT",
        "openTakerFeeRate":0.00065,
        "dealMoney":4.1,
        "status":4
    }
]
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/profitHistorical" summary="" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
signature
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="string" %}
&#x20;time stamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="contractName" type="string" %}
Contract name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-parameter in="body" name="limit" type="string" %}
Lines per page, default 100, max 1000
{% endswagger-parameter %}

{% swagger-parameter in="body" name="fromId" type="long" %}
Start retrieving from this Id
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
[
    {
        "side":"SELL",
        "positionType":2,
        "tradeFee":-5.23575,
        "realizedAmount":0,
        "leverageLevel":26,
        "openPrice":44500,
        "settleProfit":0,
        "mtime":1632882739000,
        "shareAmount":0,
        "openEndPrice":44500,
        "closeProfit":-45,
        "volume":900,
        "contractId":1,
        "historyRealizedAmount":-50.23575,
        "ctime":1632882691000,
        "id":8764,
        "capitalFee":0
    }
]
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/myTrades" summary="order record" %}
{% swagger-description %}
Speed limit rules: 20 times/ 2s
{% endswagger-description %}

{% swagger-parameter in="query" name="contractName" type="string" %}
Contract name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="string" %}
Lines per page, default 100, max 1000
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fromId" type="long" %}
Start retrieving from this tradeId
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
signature
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="string" %}
time stamp
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
    "fee":"0.001"
  },...
]
```
{% endswagger-response %}
{% endswagger %}

#### **Response:** <a href="#response-9" id="response-9"></a>

|              |         |                    |                                                     |
| ------------ | ------- | ------------------ | --------------------------------------------------- |
| name         | type    | example            | description                                         |
| symbol       | string  | ETHBTC             | Coin name(trade pair)                               |
| tradeId      | number  | 28457              | Trade ID                                            |
| bidid        | long    | 150695552109032492 | Buyer order ID                                      |
| askId        | long    | 150695552109032493 | Seller order ID                                     |
| bidUserId    | integer | 10024              | Buyer user ID                                       |
| askUserId    | integer | 10025              | Seller user ID                                      |
| price        | float   | 4.01               | Filled price                                        |
| qty          | float   | 12                 | Trade quantity                                      |
| amount       | float   | 5.38               | Filled amount                                       |
| time         | number  | 1499865549590      | Trade time stamp                                    |
| fee          | number  | 0.001              | Trading fees                                        |
| side         | string  | buy                | Current order direction BUY purchase, SELL  selling |
| contractName | string  | E-BTC-USDT         | Contract name                                       |
| isMaker      | boolean | true               | is it maker?                                        |
| isBuyer      | boolean | true               | is it buyer?                                        |

## Account <a href="#zhang-hu" id="zhang-hu"></a>

### Security: USER\_DATA​ <a href="#an-quan-lei-xing-userdata" id="an-quan-lei-xing-userdata"></a>

All interfaces under the account require signature and API-key verification​​

{% swagger method="get" path="" baseUrl="https://futuresopenapi.lyotrade.com/fapi/v1/account" summary="Account info" %}
{% swagger-description %}
Speed limit rules: 20 times/2s
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Signature
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="string" %}
time stamp
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "account": [
        {
            "marginCoin": "USDT",
            "accountNormal": 999.5606,
            "accountLock": 23799.5017,
            "partPositionNormal": 9110.7294,
            "totalPositionNormal": 0,
            "achievedAmount": 4156.5072,
            "unrealizedAmount": 650.6385,
            "totalMarginRate": 0,
            "totalEquity": 99964804.560,
            "partEquity": 13917.8753,
            "totalCost": 0,
            "sumMarginRate": 873.4608,
            "positionVos": [
                {
                    "contractId": 1,
                    "contractName": "E-BTC-USDT",
                    "contractSymbol": "BTC-USDT",
                    "positions": [
                        {
                            "id": 13603,
                            "uid": 10023,
                            "contractId": 1,
                            "positionType": 2,
                            "side": "BUY",
                            "volume": 69642.0,
                            "openPrice": 11840.2394,
                            "avgPrice": 11840.3095,
                            "closePrice": 12155.3005,
                            "leverageLevel": 24,
                            "holdAmount": 7014.2111,
                            "closeVolume": 40502.0,
                            "pendingCloseVolume": 0,
                            "realizedAmount": 8115.9125,
                            "historyRealizedAmount": 1865.3985,
                            "tradeFee": -432.0072,
                            "capitalFee": 2891.2281,
                            "closeProfit": 8117.6903,
                            "shareAmount": 0.1112,
                            "freezeLock": 0,
                            "status": 1,
                            "ctime": "2020-12-11T17:42:10",
                            "mtime": "2020-12-18T20:35:43",
                            "brokerId": 21,
                            "marginRate": 0.2097,
                            "reducePrice": 9740.8083,
                            "returnRate": 0.3086,
                            "unRealizedAmount": 2164.5289,
                            "openRealizedAmount": 2165.0173,
                            "positionBalance": 82458.2839,
                            "settleProfit": 0.4883,
                            "indexPrice": 12151.1175,
                            "keepRate": 0.005,
                            "maxFeeRate": 0.0025
                        }
                    ]
                }
            ]
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

#### Response: <a href="#response-10" id="response-10"></a>

|         |      |                    |
| ------- | ---- | ------------------ |
| name    | type | description        |
| account | \[]  | Balance collection |

account field:

<table><thead><tr><th width="226"></th><th></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>name</td><td>type</td><td>example</td><td>description</td></tr><tr><td>marginCoin</td><td>string</td><td>USDT</td><td>Margin coin</td></tr><tr><td>accountNormal</td><td>float</td><td>10.05</td><td>Balance account</td></tr><tr><td>accountLock</td><td>float</td><td>10.07</td><td>Margin frozen account</td></tr><tr><td>partPositionNormal</td><td>float</td><td>10.07</td><td>Restricted position margin balance</td></tr><tr><td>totalPositionNormal</td><td>float</td><td>10.07</td><td>Full position initial margin</td></tr><tr><td>achievedAmount</td><td>float</td><td>10.07</td><td>Profit and losses occurred </td></tr><tr><td>unrealizedAmount</td><td>float</td><td>10.05</td><td>Unfilled profit and losses</td></tr><tr><td>totalMarginRate</td><td>float</td><td>10.05</td><td>Full position margin rate</td></tr><tr><td>totalEquity</td><td>float</td><td>10.07</td><td>Full position equity</td></tr><tr><td>partEquity</td><td>float</td><td>10.07</td><td>Restricted position equity</td></tr><tr><td>totalCost</td><td>float</td><td>10.07</td><td>Full position costs</td></tr><tr><td>sumMarginRate</td><td>float</td><td>10.07</td><td>All accounts margin rate</td></tr><tr><td>positionVos</td><td>[]</td><td></td><td>Position contract record</td></tr></tbody></table>

`positionVos` field:

|                |         |            |                    |
| -------------- | ------- | ---------- | ------------------ |
| name           | type    | example    | description        |
| contractId     | integer | 2          | Contract id        |
| contractName   | string  | E-BTC-USDT | Contract name      |
| contractSymbol | string  | BTC-USDT   | Contract coin pair |
| positions      | \[]     |            | Position details   |

`positions` field:

|                       |         |         |                                                                           |
| --------------------- | ------- | ------- | ------------------------------------------------------------------------- |
| name                  | type    | example | description                                                               |
| id                    | integer | 2       | Position id                                                               |
| uid                   | integer | 10023   | User ID                                                                   |
| positionType          | integer | 1       | Hold position type(1 full，2 restrictive)                                  |
| side                  | string  | SELL    | Hold position direction SELL sell long, BUY buy short                     |
| volume                | float   | 1.05    | Hold quantity                                                             |
| openPrice             | float   | 1.05    | Open position price                                                       |
| avgPrice              | float   | 1.05    | Hold average price                                                        |
| closePrice            | float   | 1.05    | Balancing average price                                                   |
| leverageLevel         | float   | 1.05    | Leverage multiple                                                         |
| holdAmount            | float   | 1.05    | Hold position margin                                                      |
| closeVolume           | float   | 1.05    | Balanced quantity                                                         |
| pendingCloseVolume    | float   | 1.05    | The number of pending closing orders                                      |
| realizedAmount        | float   | 1.05    | Profit and losses occurred                                                |
| historyRealizedAmount | float   | 1.05    | Historic accumulated profit and losses                                    |
| tradeFee              | float   | 1.05    | Trading fees                                                              |
| capitalFee            | float   | 1.05    | Capital costs                                                             |
| closeProfit           | float   | 1.05    | Balancing profit and loss                                                 |
| shareAmount           | float   | 1.05    | Amount to share                                                           |
| freezeLock            | integer | 0       | Position freeze status: 0 normal, 1 liquidation freeze, 2 delivery freeze |
| status                | integer | 0       | Position effectiveness，0 ineffective 1 effective                          |
| ctime                 | time    |         | Creation time                                                             |
| mtime                 | time    |         | Update time                                                               |
| brokerid              | integer | 1023    | Client id                                                                 |
| lockTime              | time    |         | liquidation lock time                                                     |
| marginRate            | float   | 1.05    | Margin rate                                                               |
| reducePrice           | float   | 1.05    | Price reduction                                                           |
| returnRate            | float   | 1.05    | Return rate (profit rate)                                                 |
| unRealizedAmount      | float   | 1.05    | Unfilled profit and losses                                                |
| openRealizedAmount    | float   | 1.05    | Open position unfilled  profit and losses                                 |
| positionBalance       | float   | 1.05    | Position value                                                            |
| indexPrice            | float   | 1.05    | Newest marked price                                                       |
| keepRate              | float   | 1.05    | Scaled minimum kept margin rate                                           |
| maxFeeRate            | float   | 1.05    | Balancing maximum fees rate                                               |
|                       |         |         |                                                                           |

