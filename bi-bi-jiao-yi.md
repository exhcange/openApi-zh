# 币币交易

## 公共

### 安全类型: None

## 测试连接

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/ping`

测试REST API的连通性

{% tabs %}
{% tab title="200: OK " %}
```javascript
}
```
{% endtab %}
{% endtabs %}

## 服务器时间

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/time`

获取服务器时间

{% tabs %}
{% tab title="200: OK " %}
```javascript
{
    "timezone": "GMT+08:00",
    "serverTime": 1595563624731
}
```
{% endtab %}
{% endtabs %}

## 币对列表&#x20;

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/symbols`

市场支持的币对集合esponse:

名称类型例子描述timelong`1595563624731`当前时间(Unix Timestamp, 毫秒ms)bidslist如下订单薄买盘信息askslist如下订单薄卖盘信息bids和asks所对应的信息代表了订单薄的所有价格以及价格对应的数量的信息, 由最优价格从上倒下排列名称类型例子描述' 'float`131.1`价格' 'float`2.3`当前价格对应的数量GEThttps://openapi.xxx.com/sapi/v1/ticker\\

{% tabs %}
{% tab title="200: OK " %}
```javascript
{
    "symbols": [
        {
            "quantityPrecision": 3,
            "symbol": "sccadai",
            "pricePrecision": 6,
            "baseAsset": "SCCA",
            "quoteAsset": "DAI",
            "limitAmountMin":100,
            "limitPriceMin":123.45,
            "limitVolumeMin":10
        },
        {
            "quantityPrecision": 8,
            "symbol": "btcusdt",
            "pricePrecision": 2,
            "baseAsset": "BTC",
            "quoteAsset": "USDT",
            "limitAmountMin":100,
            "limitPriceMin":123.45,
            "limitVolumeMin":10
        },
        {
            "quantityPrecision": 3,
            "symbol": "bchusdt",
            "pricePrecision": 2,
            "baseAsset": "BCH",
            "quoteAsset": "USDT",
            "limitAmountMin":100,
            "limitPriceMin":123.45,
            "limitVolumeMin":10
        },
        {
            "quantityPrecision": 2,
            "symbol": "etcusdt",
            "pricePrecision": 2,
            "baseAsset": "ETC",
            "quoteAsset": "USDT",
            "limitAmountMin":100,
            "limitPriceMin":123.45,
            "limitVolumeMin":10
        },
        {
            "quantityPrecision": 2,
            "symbol": "ltcbtc",
            "pricePrecision": 6,
            "baseAsset": "LTC",
            "quoteAsset": "BTC",
            "limitAmountMin":100,
            "limitPriceMin":123.45,
            "limitVolumeMin":10
        }
    ]
}
```
{% endtab %}
{% endtabs %}

**权重(IP/UID): 1**

#### Response: <a href="#bi-dui-lie-biao" id="bi-dui-lie-biao"></a>

| 名称                | 类型         | 例子        | 描述             |
| ----------------- | ---------- | --------- | -------------- |
| symbol            | string     | `BTCUSDT` | 币对名称           |
| baseAsset         | string     | `BTC`     | base货币         |
| quoteAsset        | string     | `USDT`    | 计价货币           |
| pricePrecision    | integer    | `2`       | 价格精度           |
| quantityPrecision | integer    | `6`       | 数量精度           |
| limitAmountMin    | BigDecimal | 100       | 限价单最小下单金额quote |
| limitPriceMin     | BigDecimal | 100       | 限价单最小价格        |
| limitVolumeMin    | BigDecimal | 100       | 限价单最小下单数量base  |

## 行情

### 安全类型: None

## 订单薄

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/depth`

市场订单薄深度信息

#### Query Parameters

| Name                                     | Type    | Description       |
| ---------------------------------------- | ------- | ----------------- |
| limit                                    | integer | 默认100; 最大100      |
| symbol<mark style="color:red;">\*</mark> | String  | 币对名称 E.g. BTCUSDT |

{% tabs %}
{% tab title="200: OK  成功获取深度信息" %}
```javascript
{
  "bids": [
    [
      "3.90000000",   // 价格
      "431.00000000"  // 数量
    ],
    [
      "4.00000000",
      "431.00000000"
    ]
  ],
  "asks": [
    [
      "4.00000200",  // 价格
      "12.00000000"  // 数量
    ],
    [
      "5.10000000",
      "28.00000000"
    ]
  ]
}
```
{% endtab %}
{% endtabs %}

**权重(IP/UID): 5**

#### Response: <a href="#bi-dui-lie-biao" id="bi-dui-lie-biao"></a>

| time | long | `1595563624731` | 当前时间(Unix Timestamp, 毫秒ms) |
| ---- | ---- | --------------- | -------------------------- |
| bids | list | 如下              | 订单薄买盘信息                    |
| asks | list | 如下              | 订单薄卖盘信息                    |

bids和asks所对应的信息代表了订单薄的所有价格以及价格对应的数量的信息, 由最优价格从上倒下排列

| ' ' | float | `131.1` | 价格        |
| --- | ----- | ------- | --------- |
| ' ' | float | `2.3`   | 当前价格对应的数量 |

## &#x20;行情ticker

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/ticker`

24小时价格变化数据

#### Query Parameters

| Name                                     | Type   | Description                                                    |
| ---------------------------------------- | ------ | -------------------------------------------------------------- |
| symbol<mark style="color:red;">\*</mark> | String | <p>币对名称 E.g.</p><p><code>BTCUSDT</code></p><p>Responses200</p> |

{% tabs %}
{% tab title="200: OK  成功获取ticker信息" %}
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
{% endtab %}
{% endtabs %}

**权重(IP/UID): 5**

#### Response:

| time | long  | `1595563624731` | 时间戳 |   |
| ---- | ----- | --------------- | --- | - |
| high | float | `9900`          | 最高价 |   |
| low  | float | `8800.34`       | 最低价 |   |
| open | float | `8700`          | 开盘价 |   |
| last | float | `8900`          | 最新价 |   |
| vol  | float | `4999`          | 交易量 |   |
| rose | float | 0               | 涨幅  |   |

## 最近成交

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/trades`

#### Query Parameters

| Name                                     | Type   | Description                                 |
| ---------------------------------------- | ------ | ------------------------------------------- |
| symbol<mark style="color:red;">\*</mark> | String | <p>币对名称 E.g.</p><p><code>BTCUSDT</code></p> |
| limit                                    | String | `默认100:最大1000`                              |

{% tabs %}
{% tab title="200: OK 成功" %}
```javascript
{
    "list":[
        {
            "price":"3.00000100",
            "qty":"11.00000000",
            "time":1499865549590,
            "side":"BUY"
        }
    ]
}
```
{% endtab %}
{% endtabs %}

**权重(IP/UID): 5**

#### Response:

| price | float  | `0.055`         | 交易价格             |   |
| ----- | ------ | --------------- | ---------------- | - |
| time  | long   | `1537797044116` | 当前Unix时间戳，毫秒(ms) |   |
| qty   | float  | `5`             | 数量（张数）           |   |
| side  | string | `BUY/SELL`      | 主动单方向            |   |

## K线/蜡烛图数据

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/klines`

#### Query Parameters

| Name                                       | Type   | Description                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------ | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| symbol<mark style="color:red;">\*</mark>   |        | <p>币对名称 E.g.</p><p><code>BTCUSDT</code></p>                                                                                                                                                                                                                                                                                     |
| interval<mark style="color:red;">\*</mark> | String | <p>k线图区间, 可识别发送的值为：</p><p><code>1min</code></p><p>,</p><p><code>5min</code></p><p>,</p><p><code>15min</code></p><p>,</p><p><code>30min</code></p><p>,</p><p><code>60min</code></p><p>,</p><p><code>1day</code></p><p>,</p><p><code>1week</code></p><p>,</p><p><code>1month</code></p><p>（min=分钟，h=小时,day=天，week=星期，month=月）</p> |
| startTime                                  | long   | 起始时间点                                                                                                                                                                                                                                                                                                                           |
| endTime                                    | long   | 截止时间点                                                                                                                                                                                                                                                                                                                           |

{% tabs %}
{% tab title="200: OK 成功" %}
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
{% endtab %}
{% endtabs %}

**权重(IP/UID): 1**

#### Response:

| `idx` | long  | `1538728740000` | 开始时间戳，毫秒（ms）   |   |
| ----- | ----- | --------------- | -------------- | - |
| open  | float | `36.00000`      | 开盘价            |   |
| close | float | `33.00000`      | 收盘价            |   |
| high  | float | `36.00000`      | 最高价            |   |
| low   | float | `30.00000`      | 最低价            |   |
| vol   | float | `2456.111`      | <p>成交量<br></p> |   |

## 交易

### 安全类型: TRADE

交易下方的接口都需要签名和API-Key验证

## &#x20;创建新订单

<mark style="color:green;">`POST`</mark> `https://openapi.xxx.xx/sapi/v1/order`

#### Query Parameters

| Name        | Type    | Description |
| ----------- | ------- | ----------- |
| X-CH-SIGN   | string  | 签名          |
| X-CH-APIKEY | string  | 您的API-Key   |
| X-CH-TS     | integer | 时间戳         |

#### Request Body

| Name                                     | Type    | Description                                           |
| ---------------------------------------- | ------- | ----------------------------------------------------- |
| symbol                                   | String  | <p>币对名称 E.g.</p><p><code>BTCUSDT</code></p>           |
| symbolName                               | String  | 币种显示名称, symbol和symbolName二选一填写                        |
| volume<mark style="color:red;">\*</mark> | number  | 订单数量                                                  |
| side<mark style="color:red;">\*</mark>   | String  | <p>订单方向,</p><p><code>BUY/SELL</code></p>              |
| type<mark style="color:red;">\*</mark>   | String  | <p>订单类型,</p><p><code>LIMIT/MARKET</code></p>          |
| price                                    | number  | <p>订单价格, 对于</p><p><code>LIMIT</code></p><p>订单必须发送</p> |
| newClientOrderId                         | String  | 客户端订单标识                                               |
| recvwindow                               | integer | 时间窗口                                                  |

{% tabs %}
{% tab title="200: OK " %}
<pre class="language-javascript"><code class="lang-javascript">{
    'symbol': 'LXTUSDT', 
    'orderId': '150695552109032492', //Long类型的订单号
    'clientOrderId': '157371322565051',
    'transactTime': '1573713225668', 
    'price': '0.005452', 
    'origQty': '110', 
    'executedQty': '0', 
    'status': 'NEW',
    'type': 'LIMIT', 
    'side': 'SELL',
<strong>    "orderIdString": "1642655717519015937" //字符串类型的订单号,推荐使用这个
</strong>
}
</code></pre>
{% endtab %}
{% endtabs %}

**权重(IP/UID): 5**

#### Response:

| orderId       | long    | `150695552109032492`   | 订单ID（系统生成）                                |   |
| ------------- | ------- | ---------------------- | ----------------------------------------- | - |
| orderIdString | string  | "`150695552109032492"` | 字符串类型的订单ID(推荐使用)                          |   |
| clientOrderId | string  | `213443`               | 订单ID（自己发送的）                               |   |
| symbol        | string  | `BTCUSDT`              | 币对名称                                      |   |
| transactTime  | integer | `1273774892913`        | 订单创建时间                                    |   |
| price         | float   | `4765.29`              | 订单价格                                      |   |
| origQty       | float   | `1.01`                 | 订单数量                                      |   |
| executedQty   | float   | `1.01`                 | 已经成交订单数量                                  |   |
| type          | string  | `LIMIT`                | 订单类型`LIMIT`(限价)`MARKET`（市价）               |   |
| side          | string  | `BUY`                  | 订单方向。可能出现的值只能为：`BUY`（买入做多） 和 `SELL`（卖出做空） |   |
| status        | string  | `0`                    | 0 = 新订单                                   |   |

## &#x20;创建测试订单

<mark style="color:green;">`POST`</mark> `https://openapi.xxx.xx/sapi/v1/order/test`

创建和验证新订单, 但不会送入撮合引擎

#### Headers

| Name        | Type   | Description |
| ----------- | ------ | ----------- |
| X-CH-SIGN   | String | 签名          |
| X-CH-APIKEY | String | 您的API-key   |
| X-CH-TS     | String | 时间戳         |

#### Request Body

| Name                                     | Type    | Description                                           |
| ---------------------------------------- | ------- | ----------------------------------------------------- |
| recvwindow                               | integer | 时间窗口                                                  |
| symbol<mark style="color:red;">\*</mark> | String  | <p>币对名称 E.g.</p><p><code>BTCUSDT</code></p>           |
| volume<mark style="color:red;">\*</mark> | number  | 订单数量                                                  |
| side<mark style="color:red;">\*</mark>   | String  | <p>订单方向,</p><p><code>BUY/SELL</code></p>              |
| type<mark style="color:red;">\*</mark>   | String  | <p>订单类型,</p><p><code>LIMIT/MARKET</code></p>          |
| price<mark style="color:red;">\*</mark>  | number  | <p>订单价格, 对于</p><p><code>LIMIT</code></p><p>订单必须发送</p> |
| newClientorderId                         | String  | 客户端订单标识                                               |

{% tabs %}
{% tab title="200: OK " %}
```javascript
{
    // Response
}
```
{% endtab %}
{% endtabs %}

**权重(IP/UID): 1**

***

***

## &#x20;批量下单

<mark style="color:green;">`POST`</mark> `https://openapi.xxx.xx/sapi/v1/batchOrders`

#### Headers

| Name        | Type   | Description |
| ----------- | ------ | ----------- |
| X-CH-SIGN   | String | 签名          |
| X-CH-APIKEY | String | 您的API-key   |
| X-CH-TS     | String | 时间戳         |

#### Request Body

| Name                                     | Type   | Description                                 |
| ---------------------------------------- | ------ | ------------------------------------------- |
| symbol<mark style="color:red;">\*</mark> | String | <p>币对名称 E.g.</p><p><code>BTCUSDT</code></p> |
| symbolName                               | String | 币种显示名称, symbol和symbolName二选一填写              |
| orders                                   | number | 批量订单信息 最多10条                                |

{% tabs %}
{% tab title="200: OK " %}
```javascript
{
    "idsString": [ //字符串类型的订单id(推荐使用)
        "165964665990709251",
        "165964665990709252",
        "165964665990709253"
    ],
    "ids": [
        165964665990709251,
        165964665990709252,
        165964665990709253
    ]
}
```
{% endtab %}
{% endtabs %}

**权重(IP/UID): 10**

#### Resquest `orders` field:

| 名称        | 类型     | 例子             | 描述 |
| --------- | ------ | -------------- | -- |
| price     | folat  | 1000           | 价格 |
| volume    | folat  | 20.1           | 数量 |
| side      | String | BUY/SELL       | 方向 |
| batchType | String | `LIMIT/MARKET` | 类型 |

#### Resquest: <a href="#resquest-orders-field" id="resquest-orders-field"></a>

| idsString | String  | “3213213” | String类型的订单号集合 |   |
| --------- | ------- | --------- | -------------- | - |
| ids       | integer | 2100      | 订单号集合          |   |

## &#x20;订单查询

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/order`

#### Query Parameters

| Name                                      | Type   | Description                                              |
| ----------------------------------------- | ------ | -------------------------------------------------------- |
| orderId<mark style="color:red;">\*</mark> | String | 订单id                                                     |
| newClientOrderId                          | String | 客户端订单标识                                                  |
| symbol<mark style="color:red;">\*</mark>  | String | <p>币对名称 E.g.</p><p><code>BTCUSDT</code></p><p>Header</p> |
| symbol                                    | String | 币种显示名称, symbol和symbolName二选一填写                           |

#### Headers

| Name        | Type   | Description |
| ----------- | ------ | ----------- |
| X-CH-SIGN   | String | 签名          |
| X-CH-APIKEY | String | 您的API-key   |
| X-CH-TS     | String | 时间戳         |

{% tabs %}
{% tab title="200: OK " %}
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
{% endtab %}
{% endtabs %}

**权重(IP/UID): 1**

#### **Response:**

| orderId       | long    | `150695552109032492` | 订单ID（系统生成）                                                                                                 |   |
| ------------- | ------- | -------------------- | ---------------------------------------------------------------------------------------------------------- | - |
| clientOrderId | string  | `213443`             | 订单ID（自己发送的）                                                                                                |   |
| symbol        | string  | `BTCUSDT`            | 币对名称                                                                                                       |   |
| transactTime  | integer | `1273774892913`      | 订单创建时间                                                                                                     |   |
| price         | float   | `4765.29`            | 订单价格                                                                                                       |   |
| origQty       | float   | `1.01`               | 订单数量                                                                                                       |   |
| executedQty   | float   | `1.01`               | 已经成交订单数量                                                                                                   |   |
| avgPrice      | float   | `4754.24`            | 订单已经成交的平均价格                                                                                                |   |
| side          | string  | `BUY`                | 订单方向。可能出现的值只能为：`BUY`（买入做多） 和 `SELL`（卖出做空）                                                                  |   |
| status        | string  | `NEW`                | 订单状态。可能出现的值为：`NEW`(新订单，无成交)、`PARTIALLY_FILLED`（部分成交）、`FILLED`（全部成交）、`CANCELED`（已取消）和`REJECTED`（订单被拒绝）.POST |   |
| transactTime  | string  | 1574327555669        | 订单创建时间                                                                                                     |   |

## 撤销订单

<mark style="color:green;">`POST`</mark> `https://openapi.xxx.xx/sapi/v1/cancel`

#### Headers

| Name        | Type   | Description |
| ----------- | ------ | ----------- |
| X-CH-SIGN   | String | 签名          |
| X-CH-APIKEY | String | 您的API-key   |
| X-CH-TS     | String | 时间戳         |

#### Request Body

| Name                                      | Type   | Description                                                    |
| ----------------------------------------- | ------ | -------------------------------------------------------------- |
| orderId<mark style="color:red;">\*</mark> | String | 订单id                                                           |
| newClientOrderId                          | String | 客户端订单标识                                                        |
| symbol<mark style="color:red;">\*</mark>  | String | <p>币对名称 E.g.</p><p><code>BTCUSDT</code></p><p>Responses200</p> |

{% tabs %}
{% tab title="200: OK  撤销订单成功" %}
```javascript
{
    'symbol': 'BHTUSDT', 
    'clientOrderId': '0', 
    'orderId': '499890200602846976', 
    'status': 'CANCELED'
}

```
{% endtab %}
{% endtabs %}

**权重(IP/UID): 5**

#### Response:

| orderId       | long   | `150695552109032492` | 订单ID（系统生成）                                                                                                 |   |
| ------------- | ------ | -------------------- | ---------------------------------------------------------------------------------------------------------- | - |
| clientorderId | string | `213443`             | 订单ID（自己发送的）                                                                                                |   |
| symbol        | string | `BTCUSDT`            | 币对名称                                                                                                       |   |
| status        | string | `NEW`                | 订单状态。可能出现的值为：`NEW`(新订单，无成交)、`PARTIALLY_FILLED`（部分成交）、`FILLED`（全部成交）、`CANCELED`（已取消）和`REJECTED`（订单被拒绝）.POST |   |

## 批量撤销订单

<mark style="color:green;">`POST`</mark> `https://openapi.xxx.xx/sapi/v1/batchCancel`

**一次批量最多10个订单**

#### Headers

| Name        | Type   | Description |
| ----------- | ------ | ----------- |
| X-CH-SIGN   | String | 签名          |
| X-CH-APIKEY | String | 您的API-key   |
| X-CH-TS     | String | 时间戳         |

#### Request Body

| Name                                       | Type   | Description                                                          |
| ------------------------------------------ | ------ | -------------------------------------------------------------------- |
| orderIds<mark style="color:red;">\*</mark> | String | <p>要取消的订单id集合</p><p><code>[123,456]</code></p><p>Responses200GET</p> |
| symbol<mark style="color:red;">\*</mark>   | String | <p>币对名称 E.g.</p><p><code>BTCUSDT</code></p><p>Responses200</p>       |

{% tabs %}
{% tab title="200: OK " %}
```javascript
{
    "success": [
        165964665990709251,
        165964665990709252,
        165964665990709253
    ],
    "failed": [ //取消失败一般是因为订单不存在或订单状态已经到终态
        165964665990709250  
    ]
}
```
{% endtab %}
{% endtabs %}

**权重(IP/UID): 10**

***

***

## &#x20;当前订单

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/openOrders`

#### Query Parameters

| Name                                     | Type   | Description                                 |
| ---------------------------------------- | ------ | ------------------------------------------- |
| symbol<mark style="color:red;">\*</mark> | String | <p>币对名称 E.g.</p><p><code>BTCUSDT</code></p> |
| limit                                    | String | 默认100; 最大1000                               |

#### Headers

| Name        | Type   | Description |
| ----------- | ------ | ----------- |
| X-CH-SIGN   | String | 签名          |
| X-CH-APIKEY | String | 您的API-key   |
| X-CH-TS     | String | 时间戳         |

{% tabs %}
{% tab title="200: OK " %}
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
{% endtab %}
{% endtabs %}

#### **权重(IP/UID): 1**

#### Response:

| orderId       | long   | `150695552109032492`   | 订单ID（系统生成）                                                                                                 |   |
| ------------- | ------ | ---------------------- | ---------------------------------------------------------------------------------------------------------- | - |
| orderIdString | String | "`150695552109032492"` | 字符串类型的订单ID(推荐使用)                                                                                           |   |
| clientorderId | string | `213443`               | 订单ID（自己发送的）                                                                                                |   |
| symbol        | string | `BTCUSDT`              | 币对名称                                                                                                       |   |
| price         | float  | `4765.29`              | 订单价格                                                                                                       |   |
| origQty       | float  | `1.01`                 | 订单数量                                                                                                       |   |
| executedQty   | float  | `1.01`                 | 已经成交订单数量                                                                                                   |   |
| avgPrice      | float  | `4754.24`              | 订单已经成交的平均价格                                                                                                |   |
| type          | string | `LIMIT`                | 订单类型`LIMIT`(限价)`MARKET`（市价）                                                                                |   |
| side          | string | `BUY`                  | 订单方向。可能出现的值只能为：`BUY`（买入做多） 和 `SELL`（卖出做空）                                                                  |   |
| status        | string | `NEW`                  | 订单状态。可能出现的值为：`NEW`(新订单，无成交)、`PARTIALLY_FILLED`（部分成交）、`FILLED`（全部成交）、`CANCELED`（已取消）和`REJECTED`（订单被拒绝）.POST |   |
| time          | string | 1574327555669          | 创建时间                                                                                                       |   |

## &#x20;交易记录

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/myTrades`

#### Query Parameters

| Name                                     | Type   | Description                                 |
| ---------------------------------------- | ------ | ------------------------------------------- |
| symbol<mark style="color:red;">\*</mark> | String | <p>币对名称 E.g.</p><p><code>BTCUSDT</code></p> |
| limit                                    | String | 默认100; 最大1000                               |
| fromId                                   | String | 从这个tradeId开始检索                              |

#### Headers

| Name        | Type   | Description |
| ----------- | ------ | ----------- |
| X-CH-SIGN   | String | 签名          |
| X-CH-APIKEY | String | 您的API-key   |
| X-CH-TS     | String | 时间戳         |

{% tabs %}
{% tab title="200: OK " %}
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
    "fee":"0.001",
    "bidUserId":23334,
    "askUserId":44112
  },...
]
```
{% endtab %}
{% endtabs %}

**权重(IP/UID): 1**

#### Response:

| id        | long    | `150695552109032492` | 成交id                                      |    |
| --------- | ------- | -------------------- | ----------------------------------------- | -- |
| symbol    | String  | 币对                   | 字符串类型的订单ID(推荐使用)                          | ti |
| time      | long    | 1499865549590        | 创建时间                                      |    |
| qty       | string  | `12`                 | 交易数量                                      |    |
| price     | float   | `4765.29`            | 订单价格                                      |    |
| fee       | string  | `0.001`              | 交易手续费币                                    |    |
| feeCoin   | String  | `xxx`                | 手续费币种                                     |    |
| isBuyer   | boolean | `true`               | `true`= 买 `false`= 卖                      |    |
| isMaker   | boolean | false                | `true`=市价 `false`=限价                      |    |
| bidId     | long    | `1200000200`         | 买单id                                      |    |
| askId     | long    | `1200000200`         | 卖单id                                      |    |
| side      | string  | `BUY`                | 订单方向。可能出现的值只能为：`BUY`（买入做多） 和 `SELL`（卖出做空） |    |
| bidUserId | long    | 23334                | 买方uid                                     |    |
| askUserId | long    | 44112                | 卖方uid                                     |    |
| isSelf    | boolean | true                 | 是否是自成交                                    |    |

## 账户

### 安全类型: USER\_DATA

## 账户信息

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/account`

#### Headers

| Name        | Type   | Description |
| ----------- | ------ | ----------- |
| X-CH-SIGN   | String | 签名          |
| X-CH-APIKEY | String | 您的API-key   |
| X-CH-TS     | String | 时间戳         |

{% tabs %}
{% tab title="200: OK " %}
```javascript
```
{% endtab %}
{% endtabs %}

**权重(IP/UID): 1**
