# 提现

## 提现

{% swagger method="post" path="/sapi/v1/withdraw/apply" baseUrl="https://openapi.xxx.com" summary="发起提现" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-APIKEY" required="true" type="String" %}
您的API-Key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-SIGN" required="true" type="String" %}
签名
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" required="true" type="Integer" %}
时间戳
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" type="String" %}
币种，支持多主链的币需要传实际的币种名称，参照

[附录1](fu-lu-1.md)


{% endswagger-parameter %}

{% swagger-parameter in="body" name="withdrawOrderId" required="true" type="String" %}
自定义提现id，保证唯一
{% endswagger-parameter %}

{% swagger-parameter in="body" name="amount" required="true" type="String" %}
数量
{% endswagger-parameter %}

{% swagger-parameter in="body" name="address" required="true" type="String" %}
提币地址
{% endswagger-parameter %}

{% swagger-parameter in="body" name="label" type="String" %}
某些币种例如 XRP,XMR 允许填写次级地址标签
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```json
{
    "code":"Ѳ",//返回码，0代表成功，其他失败
    "msg":"sucess",//返回信息
    "data":{
        "id":518353 //提现id
    }
}
```
{% endswagger-response %}
{% endswagger %}

**权重(IP/UID): 100**

{% swagger method="post" path="/sapi/v1/withdraw/query" baseUrl="https://openapi.xxx.com" summary="提现记录查询" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-APIKEY" required="true" type="String" %}
您的API-Key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-SIGN" required="true" type="String" %}
签名
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" required="true" type="String" %}
时间戳
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" type="String" %}
币种，支持多主链的币需要传实际的币种名称，参照

[附录1](fu-lu-1.md)


{% endswagger-parameter %}

{% swagger-parameter in="body" name="withdrawId" type="String" %}
平台提现id
{% endswagger-parameter %}

{% swagger-parameter in="body" name="withdrawOrderId" type="String" %}
自定义提现id
{% endswagger-parameter %}

{% swagger-parameter in="body" name="startTime" type="Number" %}
开始时间，时间戳，默认90天前
{% endswagger-parameter %}

{% swagger-parameter in="body" name="endTime" type="Number" %}
结束时间，时间戳，默认当前时间
{% endswagger-parameter %}

{% swagger-parameter in="body" name="page" type="String" %}
页码，从1开始
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```json
{
    "code": "0",
    "msg": "成功",
    "data": {
        "withdrawList": [
            {
                "symbol": "TUSDT",
                "amount": 19.99999,
                "address": "TFFrjNfBAagmFWypE3Hnv6zPKAFhd3VcDf",
                "withdrawOrderId": "abc123",
                "fee": 0.00001,
                "ctime": 1605585397000,
                "txId": "749864_20201117115930",
                "id": 749864,
                "applyTime": 1666754820000,
                "status": 5,
                "info": ""
            },
            {
                "symbol": "TUSDT",
                "amount": 10.50999,
                "address": "TYsTiVVDU5VmnUPufzGD52CD1hSbPATT3Q",
                "withdrawOrderId": "abc456",
                "fee": 0.00001,
                "ctime": 1607089149000,
                "txId": "764294_20201204094130",
                "id": 764294,
                "applyTime": 1666754820000,
                "status": 5,
                "info": ""
            }
        ],
        "count": 2
    }
}
```
{% endswagger-response %}
{% endswagger %}

**权重(IP/UID): 100**

#### Responses

| 参数              | 类型     | 示例                                 | 备注                                                |
| --------------- | ------ | ---------------------------------- | ------------------------------------------------- |
| symbol          | String | USDT                               | 提币币种                                              |
| amount          | Number | 9.99                               | 数量                                                |
| address         | String | TFFrjNfBAagmFWypE3Hnv6zPKAFhd3VcDf | 提币地址                                              |
| withdrawOrderId | String | abc123                             | 自定义提现id                                           |
| fee             | Number | 0.01                               | 手续费                                               |
| ctime           | Number | 1605585397000                      | 创建时间                                              |
| txId            | String | 749864\_20201117115930             | 提现交易id                                            |
| id              | Number | 749864                             | 平台提现id                                            |
| applyTime       | Number | 1605585397000                      | 上链时间                                              |
| status          | Number | 2                                  | 提币状态，0-未审核 1-审核通过 2-审核拒绝 3-支付中 4-支付失败 5-已完成 6-已撤销 |
| info            | String | 提币地址错误                             | 审核拒绝原因                                            |
