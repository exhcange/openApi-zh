# 杠杆交易

## 交易

### 安全类型: TRADE

交易下方的接口都需要签名API Key验证

{% swagger method="post" path="/sapi/v1/margin/order" baseUrl="https://openapi.xxx.com" summary=" 创建杠杆订单" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
签名
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
您的API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
时间戳
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" %}
币对名称 E.g. 

`BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="volume" type="number" %}
订单数量
{% endswagger-parameter %}

{% swagger-parameter in="body" name="side" %}
订单方向, 

`BUY/SELL`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" %}
订单类型, 

`LIMIT/MARKET`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type="number" %}
订单价格, 对于

`LIMIT`

订单必须发送
{% endswagger-parameter %}

{% swagger-parameter in="body" name="newClientOrderId" %}
客户端订单标识
{% endswagger-parameter %}

{% swagger-parameter in="body" name="recwwindow" %}
时间窗口
{% endswagger-parameter %}

{% swagger-response status="200: OK" description=" 发送杠杆订单成功" %}
```javascript
{
    'symbol': 'LXTUSDT', 
    'orderId': '494736827050147840', 
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

**权重(IP/UID): 5**

****

{% swagger method="get" path="/sapi/v1/margin/order" baseUrl="https://openapi.xxx.com" summary=" 杠杆订单查询" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
签名
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
您的API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
时间戳
{% endswagger-parameter %}

{% swagger-parameter in="query" name="orderId" %}
订单ID
{% endswagger-parameter %}

{% swagger-parameter in="query" name="newClientOrderId" %}
客户端订单标识
{% endswagger-parameter %}

{% swagger-parameter in="query" name="symbol" %}
币对名称E.g. 

`BTCUSDT`

Header
{% endswagger-parameter %}

{% swagger-response status="200: OK" description=" 查询杠杆订单成功" %}
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

**权重(IP/UID): 5**

****

{% swagger method="post" path="/sapi/v1/margin/cancel" baseUrl="https://openapi.xxx.com" summary=" 撤销杠杆订单" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
签名
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
您的API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
时间戳
{% endswagger-parameter %}

{% swagger-parameter in="body" name="orderId" %}
订单id
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" %}
币对名称 E.g. 

`BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="newClientOrderId" %}
客户端订单标识
{% endswagger-parameter %}

{% swagger-response status="200: OK" description=" 发送杠杆订单成功" %}
```javascript
{
    'symbol': 'LXTUSDT', 
    'orderId': '494736827050147840', 
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

**权重(IP/UID): 5**

****

{% swagger method="get" path="/sapi/v1/margin/openOrders" baseUrl="https://openapi.xxx.com" summary=" 杠杆当前委托" %}
{% swagger-description %}
**权重(IP/UID): 5**

****
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
签名
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
您的API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
时间戳
{% endswagger-parameter %}

{% swagger-parameter in="query" name="symbol" %}
币对名称E.g. 

`BTCUSDT`

Header
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" %}
默认100; 最大1000
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

**权重(IP/UID): 1**

****

{% swagger method="get" path="/sapi/v1/margin/myTrades" baseUrl="https://openapi.xxx.com" summary=" 杠杆交易记录" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
签名
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
您的API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
时间戳
{% endswagger-parameter %}

{% swagger-parameter in="query" name="symbol" %}
币对名称 E.g. BTCUSDT
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" %}
默认100；最大1000
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fromId" %}
从这个tradeld开始检索
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

**权重(IP/UID): 1**
