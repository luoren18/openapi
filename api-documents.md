

### 成交记录
#### GET /api/v1/perpetual/admin/deal-record

请求参数：


#### 请求参数：


##### Query
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
AccessKeyId|y|string|访问key||
SignatureVersion|y|string|版本||
SignatureMethod|y|string|签名方法||HmacSHA256
Signature|y|string|签名||
Timestamp|y|string|时间戳||
startDate|n|long|开始时间||
endDate|n|long|结束时间||
contractCode|n|string|合约code||
page|n|integer|页数|1|
pageSize|n|integer|每页数量|20|
startId|n|long|开始id||
endId|n|long|结束id||



```json
{
    "code": 200,
    "data": {
        "data": [
            {
                "amount": "6.0000000000000000",
                "contractCode": "btcusdt",
                "contractCodeDisplayName":"btcusdt",
                "createDate": "2021-11-14 20:52:03",
                "currencyCode": "usdt",
                "currencyCodeDisplayName":"usdt",
                "dealType": 1,
                "env":0,
                "detailSide": "close_long",
                "fee": "1.3579752900000000",
                "id": "666746374653476864",
                "makerTaker": "maker",
                "orderId": 125090120907072,
                "price": "64665.4900000000000000",
                "profit": "0.9555748956901509",
                "refOrderId": 125090122965326,
		"refUserId": 10000,
                "size": "3879.9294000000000000",
                "userId": "2000011"
            }
        ],
        "pageNum": 1,
        "pageSize": 20,
        "totalCount": 112677
    },
    "msg": "success"
}

```

#### 返回：

参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
amount|y|string|成交数量||
contractCode|y|string|合约code||
contractCodeDisplayName|y|string|合约Code 显示名||
createDate|y|string|创建时间||
currencyCode|y|string|币种||
currencyCodeDisplayName|y|string|币种显示名||
dealType|y|string|成交类型，1：自成交，2：与其他用户成交||
detailSide|y|string|开平方向||
fee|y|string|手续费||
id|y|long|成交记录id||
makerTaker|y|string|maker or taker||
orderId|y|long|订单id||
price|y|string|成交价格||
profit|y|string|收益||
refOrderId|y|long|关联订单id||
refUserId|y|long|关联userId||
size|y|string|成交价值||
userId|y|long|uid||
env|y|int|0-实盘/1-模拟盘||


### 历史订单记录
#### GET /api/v1/perpetual/admin/{contractCode}/order/list

请求参数：


#### 请求参数：

##### 路径参数
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
contractCode|y|string|合约code||

##### Query
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
AccessKeyId|y|string|访问key||
SignatureVersion|y|string|版本||
SignatureMethod|y|string|签名方法||HmacSHA256
Signature|y|string|签名||
Timestamp|y|string|时间戳||
startDate|n|long|开始时间||
endDate|n|long|结束时间||
page|n|integer|页数|1|
pageSize|n|integer|每页数量|20|
userIds|n|List<long>|用户id||

```json
{
    "code": 200,
    "data": {
        "rows": [
            {
                "amount": "1",
                "avgPrice": "23000",
                "base": "usdt",
                "brokerId": 1,
                "contractCode": "btcusdt",
                "contractDirection": 0,
                "createdDate": 1659685346000,
                "dealAmount": "1",
                "detailSide": "open_short",
                "direction": "",
                "env": 0,
                "fee": "-0.1495",
                "id": 148428130610224,
                "indexBase": "btc",
                "indexBaseDisplayName": "BTC",
                "lever": "125",
                "modifyDate": 1659685346000,
                "orderPriceType": 0,
                "orderSize": "232.968878",
                "positionType": 0,
                "price": "23000",
                "profit": "0",
                "quote": "usdt",
                "reason": 0,
                "refConditionOrderId": 0,
                "refOrderCondition": null,
                "side": "short",
                "source": "WEB",
                "status": 2,
                "stopLimitType": 0,
                "stopLoss": null,
                "stopProfit": null,
                "systemType": 10,
                "triggerBy": "",
                "triggerDate": 0,
                "triggerPrice": "",
                "userId": 20100195
            }
        ],
        "total": 18
    },
    "msg": "success"
}

```

#### 返回：

参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
id|y|string|订单id||
lever|y|string|杠杆||
userId|y|long|uid||
contractCode|y|string|合约code||
userId|y|long|uid||
base|y|string|基础币||
quote|y|string|计价币||
indexBase|y|string|指数币||
env|y|int|0-实盘/1-模拟盘||
contractDirection|y|string|合约方向：0:正向,1:反向||
side|y|string|仓位方向：long多，short空||
detailSide|y|string|详细仓位方向：1.开多open_long 2.开空open_short 3.平多close_long 4.平空close_short||
amount|y|string|委托数量||
dealAmount|y|string|已成交数量||
avgPrice|y|string|平均成交价格||
price|y|string|委托价格||
orderSize|y|string|委托价值||
status|y|int|委托状态：0 等待成交 1 部分成交 2 已经成交 -1 已经撤销||
systemType|y|long|委托类型：全部、10:限价 11:市价 13:强平单 14:爆仓单 15：穿仓 16：强减||
direction|y|long|触发方向，greater大于，less小于||
profit|y|string|该笔订单成交后对应的盈亏: 正表示盈利,负表示亏损||
fee|y|string|手续费||
modifyDate|y|Long|最后操作时间||
createdDate|y|date|创建时间||


### 当前持仓
#### GET /api/v1/perpetual/admin/{contractCode}/position

请求参数：

#### 请求参数：

##### 路径参数
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
contractCode|y|string|合约code||

##### Query
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
AccessKeyId|y|string|访问key||
SignatureVersion|y|string|版本||
SignatureMethod|y|string|签名方法||HmacSHA256
Signature|y|string|签名||
Timestamp|y|string|时间戳||
startDate|n|long|开始时间||
endDate|n|long|结束时间||
contractCode|n|string|合约code||
page|n|integer|页数|1|
pageSize|n|integer|每页数量|20|
userIds|n|List<long>|用户id||

```json
{
    "code": 200,
    "data": {
        "rows": [
            {
                "amount": "1.0000000000000000",
                "base": "usdt",
                "baseDisplayName": "USDT",
                "brokerPrice": "100000000.0000000000000000",
                "closingAmount": "0E-16",
                "contractCode": "btcusdt",
                "contractCodeDisplayName": "BTCUSDT",
                "createdDate": 1608185501000,
                "env": 0,
                "fee": "0E-16",
                "gear": "",
                "indexBase": "btc",
                "indexBaseDisplayName": "BTC",
                "lever": "125.0000000000000000",
                "liqudatePrice": "100000000.0000000000000000",
                "maintenanceMargin": "0.9200000000000000",
                "markPrice": "",
                "minQuoteDigit": 0,
                "minTradeDigit": 0,
                "openMaginRate": "",
                "openMargin": "1.8400000000000000",
                "orderAmount": "0E-16",
                "preLiqudatePrice": "0E-16",
                "price": "23000.0000000000000000",
                "profitRate": "",
                "quote": "usdt",
                "quoteDisplayName": "USDT",
                "realizedSurplus": "0E-16",
                "risk": "",
                "side": "short",
                "size": "230.0000000000000000",
                "type": 0,
                "unRealizedSurplus": "-1.9787",
                "userId": 20100195
            }
        ],
        "total": 3
    },
    "msg": "success"
}

```

#### 返回：

参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
env|y|int|0-实盘/1-模拟盘||
createdDate|y|int|创建时间||
orderAmount|y|int|订单数量||
userId|y|long|uid||
contractCode|y|string|合约code||
base|y|string|基础币||
quote|y|string|计价币||
indexBase|y|string|指数币||
type|y|int|0全仓，1逐仓||
side|y|string|仓位类型，long多，short空||
lever|y|string|杠杆||
gear|y|string|风险限额||
closingAmount|y|string|正在平仓的数量||
realizedSurplus|y|string|已实现盈亏||
unRealizedSurplus|y|string|未实现盈亏||
price|y|string|成交均价||
amount|y|string|持仓数量||
openMargin|y|string|持仓保证金||
maintenanceMargin|y|string|维持保证金||
liqudatePrice|y|string|强平价||
size|y|string|强平价||
brokerPrice|y|string|爆仓价||

