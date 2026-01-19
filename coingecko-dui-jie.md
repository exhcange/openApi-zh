# Coingecko对接

### 币对行情

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/coinGecko/pub/v1/ticker`

**请求参数**

无

**响应参数**

| 名称               | 类型     | 例子                     | 描述                   |
| ---------------- | ------ | ---------------------- | -------------------- |
| ticker\_id       | string | BTC\_USDT              | 币对                   |
| base\_currency   | string | BTC                    | 基准货币                 |
| target\_currency | string | USDT                   | 计价货币                 |
| last\_price      | number | 98000.0000000000000000 | 基于给定目标货币的基准货币的最后交易价格 |
| base\_volume     | number | 1.1200                 | 该币对24小时单边交易量（基准币单位）  |
| target\_volume   | number | 99000.0000000000       | 该币对24小时单边交易量（计价币单位）  |
| bid              | number | 97000                  | 当前最高买单价格             |
| ask              | number | 98000                  | 当前最高低单价格             |
| high             | number | 98000                  | 滚动24小时最高交易价格         |
| low              | number | 98000                  | 滚动24小时最低交易价格         |

**响应示例**

```javascript
{
    "ETH_USDT": {
        "ticker_id": "ETH_USDT",
        "base_currency": "ETH",
        "target_currency": "USDT",
        "last_price": 238.2000000000000000,
        "base_volume": 0.0000,
        "target_volume": 0.000000,
        "bid": 0,
        "ask": 0,
        "high": 238.2,
        "low": 238.2
    },
    "BCH_USDT": {
        "ticker_id": "BCH_USDT",
        "base_currency": "BCH",
        "target_currency": "USDT",
        "last_price": 1.0000000000000000,
        "base_volume": 0.000000,
        "target_volume": 0E-10,
        "bid": 0,
        "ask": 0,
        "high": 1,
        "low": 1
    }
}
```

### 盘口数据

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/coinGecko/pub/v1/orderbook`

**请求参数**

| 名称         | 类型             | 描述     |
| ---------- | -------------- | ------ |
| ticker\_id | string         | 币对     |
| depth      | integer(int32) | 订单深度数量 |

**响应参数**

| 名称         | 类型             | 例子                          | 描述                       |
| ---------- | -------------- | --------------------------- | ------------------------ |
| ticker\_id | string         | BTC\_USDT                   | 币对                       |
| timestamp  | integer(int64) | 1766976278000               | Unix时间戳，以毫秒为单位，表示上次更新的时间 |
| bids       | array          | \[\[1000,0.1], \[2000,0.2]] | 包含两个元素的数组, 每笔买单的报价及数量    |
| asks       | array          | \[\[2000,0.2], \[3000,0.3]] | 包含两个元素的数组, 每笔卖单的报价及数量    |

**响应示例**

```javascript
{
    "ticker_id": "BTC_USDT",
    "timestamp": 1766976278000,
    "bids": [
        [
            98000,
            0.46938777
        ],
        [
            98500.93,
            0.1
        ]
    ],
    "asks": [
        [
            98000,
            0.46938777
        ],
        [
            98500.93,
            0.1
        ]
    ]
}
```



### 合约产品信息及类型

<mark style="color:blue;">`GET`</mark> `https://futuresopenapi.xxx.xx/pub/coingecko/contracts`

**请求参数**

```
no
```

**响应参数**

| **字段名**                        | **类型**    | **例子**                   | **描述**                                                |
| ------------------------------ | --------- | ------------------------ | ----------------------------------------------------- |
| ticker\_id                     | string    | E-BTC-USDT               | 合约标识符，使用分隔符区分基础货币/目标货币，例如 BTC-PERP                    |
| base\_currency                 | string    | BTC                      | 基础货币的符号/货币代码，例如 BTC                                   |
| target\_currency               | string    | USDT                     | 目标货币的符号/货币代码，例如 ETH                                   |
| last\_price                    | decimal   | 92000.36                 | 基础货币相对于目标货币的最新成交价格                                    |
| base\_volume                   | decimal   | 0.2                      | 24 小时单边成交量（以基础货币为单位）                                  |
| target\_volume                 | decimal   | 0.2                      | 24 小时单边成交量（以目标货币为单位）                                  |
| bid                            | decimal   | 92000.36                 | 当前最高买单价格                                              |
| ask                            | decimal   | 92000.36                 | 当前最低卖单价格                                              |
| high                           | decimal   | 92100.36                 | 过去 24 小时最高成交价格                                        |
| low                            | decimal   | 91900.36                 | 过去 24 小时最低成交价格                                        |
| product\_type                  | string    | Perpetual                | 产品类型：期货（Futures）、永续合约（Perpetual）、期权（Options）？         |
| open\_interest                 | decimal   | 1116.3655                | 过去 24 小时未平仓合约量（以基础货币为单位）                              |
| open\_interest\_usd            | decimal   | 102573030.064            | 过去 24 小时未平仓合约量（美元计价）                                  |
| index\_price                   | decimal   | 92100.36                 | 标的指数价格                                                |
| index\_name                    | string    | BTC-USDT                 | 标的指数名称（如有）                                            |
| index\_currency                | string    | BTC                      | 指数的标的货币                                               |
| start\_timestamp               | timestamp | 0                        | 衍生品产品的生效时间（适用于到期型期货或期权）                               |
| end\_timestamp                 | timestamp | 0                        | 衍生品产品的到期时间（适用于到期型期货或期权）                               |
| funding\_rate                  | decimal   | 0                        | 当前资金费率                                                |
| next\_funding\_rate            | decimal   | 0                        | 即将到来的预测资金费率                                           |
| next\_funding\_rate\_timestamp | timestamp | <p>1768291200000<br></p> | 下一次资金费率调整的时间戳                                         |
| contract\_type                 | string    | Vanilla                  | 合约类型描述 - 普通型（Vanilla）、反向型（Inverse）或 quanto 型（Quanto）？ |
| contract\_price\_currency      | string    | USDT                     | 合约定价货币                                                |
| contract\_price                | decimal   | 92100.36                 | 每份合约的价格（若与最新价格不同）                                     |
| timestamp                      | timestamp | 1768289995029            | 查询时间戳                                                 |

**请求示例**

```
https://futuresopenapi.xxx.xx/pub/coingecko/contracts
```

**响应示例**

<pre class="language-json"><code class="lang-json"><strong>{
</strong>    "code": "0",
    "msg": "success",
    "data": {
        "contracts": [
            {
                "ticker_id": "E-BTC-USDT",
                "base_currency": "BTC",
                "target_currency": "USDT",
                "last_price": 0,
                "base_volume": 0,
                "target_volume": 0,
                "bid": null,
                "ask": 9.8E+4,
                "high": 0,
                "low": 0,
                "product_type": "Perpetual",
                "open_interest": 1116.3655,
                "open_interest_usd": 102573030.06495740245,
                "index_price": 0,
                "index_name": "BTC-USDT",
                "index_currency": "BTC",
                "start_timestamp": 0,
                "end_timestamp": 0,
                "funding_rate": 0,
                "next_funding_rate": 0,
                "next_funding_rate_timestamp": 1768291200000,
                "contract_type": "Vanilla",
                "contract_price_currency": "USDT",
                "contract_price": 0,
                "timestamp": 1768289995029
            },
            {
                "ticker_id": "E-ETH-USDT",
                "base_currency": "ETH",
                "target_currency": "USDT",
                "last_price": 0,
                "base_volume": 0,
                "target_volume": 0,
                "bid": null,
                "ask": null,
                "high": 0,
                "low": 0,
                "product_type": "Perpetual",
                "open_interest": 3004.17,
                "open_interest_usd": 9383427.795980901,
                "index_price": 0,
                "index_name": "ETH-USDT",
                "index_currency": "ETH",
                "start_timestamp": 0,
                "end_timestamp": 0,
                "funding_rate": 0,
                "next_funding_rate": 0,
                "next_funding_rate_timestamp": 1768291200000,
                "contract_type": "Vanilla",
                "contract_price_currency": "USDT",
                "contract_price": 0,
                "timestamp": 1768289995029
            }
        ]
    }
}
</code></pre>



### 合约订单簿深度详情

<mark style="color:blue;">`GET`</mark> `https://futuresopenapi.xxx.xx/pub/coingecko/orderbook`

**请求参数**

| 名称         | 类型             | 描述                     |
| ---------- | -------------- | ---------------------- |
| ticker\_id | string         | 合约名称【可选】，例如：E-BTC-USDT |
| depth      | integer(int32) | 订单深度数量                 |

**响应参数**

| 名称         | 类型             | 例子                                                     | 描述                       |
| ---------- | -------------- | ------------------------------------------------------ | ------------------------ |
| ticker\_id | string         |   E-BTC-USDT                                           | 币对                       |
| timestamp  | integer(int64) | 1768289995029                                          | Unix时间戳，以毫秒为单位，表示上次更新的时间 |
| bids       | array          | <p>[<br>[98000,0.469387],<br>[98500.93,0.1]<br>]</p>   | 包含两个元素的数组, 每笔买单的报价及数量    |
| asks       | array          | <p>[<br>[97000,0.46938777],<br>[96500.93,0.1]<br>]</p> | 包含两个元素的数组, 每笔卖单的报价及数量    |

**请求示例**

```
https://futuresopenapi.xxx.xx/pub/coingecko/orderbook?ticker_id=E-BTC-USDT&dept=100
```

**响应示例**

```json
{
    "code": "0",
    "msg": "success",
    "data": {
        "orderbook": {
            "ticker_id": "E-BTC-USDT",
            "asks": [
                [
                    98000,
                    0.46938777
                ],
                [
                    98500.93,
                    0.1
                ],
                [
                    100000,
                    3
                ],
                [
                    1800000,
                    1.111
                ],
                [
                    2000000,
                    1
                ]
            ],
            "bids": [
                [
                    97000,
                    0.46938777
                ],
                [
                    96500.93,
                    0.1
                ],
                [
                    96000,
                    3
                ],
                [
                    95500,
                    1.111
                ],
                [
                    95000,
                    1
                ]
            ],
            "timestamp": 1768289995029
        },
        "ticker_id": "E-BTC-USDT"
    }
}
```

