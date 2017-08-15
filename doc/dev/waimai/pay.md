1. 开通快捷支付
2. Hbuilder配置
3. 支付宝功能申请


## app支付同步通知
{
    "channel": {
        "id": "alipay",
        "description": "支付宝",
        "serviceReady": true
    },
    "description": "",
    "url": "http%3A%2F%2Fwww.test.shuashuada.com%2Findex%2Fpay%2Fnotify_url",
    "signature": "fOpxWJqOdUyDmR09rMn2jkLT4hsFSICdHL5ZkZi3bmsC4HxT36FC5wjIjg9+j1KL2RjazQn4pf93WLC/v7/39tSbbXlMeHbDzNdORg92Olc5nCbkXt6obume8+hAXwT2/Gst4yhrEQUUuwDP3jEaRyeyR6bSLxipKdXbdMfa3Ks=",
    "tradeno": "1708062142467509770169",
    "rawdata": "{\"resultStatus\":\"9000\",\"memo\":\"\",\"result\":\"service=\\\"mobile.securitypay.pay\\\"&partner=\\\"2088911723511293\\\"&input_charset=\\\"UTF-8\\\"&out_trade_no=\\\"1708062142467509770169\\\"&subject=\\\"充值\\\"&payment_type=\\\"1\\\"&seller_id=\\\"3187218881@qq.com\\\"&total_fee=\\\"0.1\\\"&body=\\\"充值\\\"&notify_url=\\\"http%3A%2F%2Fwww.test.shuashuada.com%2Findex%2Fpay%2Fnotify_url\\\"&success=\\\"true\\\"&sign_type=\\\"RSA\\\"&sign=\\\"fOpxWJqOdUyDmR09rMn2jkLT4hsFSICdHL5ZkZi3bmsC4HxT36FC5wjIjg9+j1KL2RjazQn4pf93WLC\\/v7\\/39tSbbXlMeHbDzNdORg92Olc5nCbkXt6obume8+hAXwT2\\/Gst4yhrEQUUuwDP3jEaRyeyR6bSLxipKdXbdMfa3Ks=\\\"\"}"
}

## app支付异步通知post
{
    "discount": "0.00",
    "payment_type": "1",
    "trade_no": "2017080621001004970280922189",
    "subject": "充值",
    "buyer_email": "linshichun19910510@126.com",
    "gmt_create": "2017-08-06 21:57:59",
    "notify_type": "trade_status_sync",
    "quantity": "1",
    "out_trade_no": "1708062156367228850169",
    "seller_id": "2088911723511293",
    "notify_time": "2017-08-06 21:58:00",
    "body": "recharge",
    "trade_status": "TRADE_SUCCESS",
    "is_total_fee_adjust": "N",
    "total_fee": "0.01",
    "gmt_payment": "2017-08-06 21:57:59",
    "seller_email": "3187218881@qq.com",
    "price": "0.01",
    "buyer_id": "2088702106732978",
    "notify_id": "a8704516f5815ea1042bc2ba7688e68nhi",
    "use_coupon": "N",
    "sign_type": "RSA",
    "sign": "O3htsDXkDekXFImf8+Y+jUGmiuz++CX3GsRkw6m3lWWrLRU4Mm3NBt1ORmhq3ad3KhNPDOZO6VZzFWJZHIkT4s8dQEgUKzQ+8yE5iaZ4eEEBU2JLeXVNVYWuXHqEq9Wdmg/mDPfntXoDqr8Y8/dHIa6Qv/X2J+/gSSwjx+ycSjc="
}
## app支付异步通知get
{
    "discount": "0.00",
    "payment_type": "1",
    "trade_no": "2017080621001004970280922189",
    "subject": "充值",
    "buyer_email": "linshichun19910510@126.com",
    "gmt_create": "2017-08-06 21:57:59",
    "notify_type": "trade_status_sync",
    "quantity": "1",
    "out_trade_no": "1708062156367228850169",
    "seller_id": "2088911723511293",
    "notify_time": "2017-08-06 21:58:00",
    "body": "recharge",
    "trade_status": "TRADE_SUCCESS",
    "is_total_fee_adjust": "N",
    "total_fee": "0.01",
    "gmt_payment": "2017-08-06 21:57:59",
    "seller_email": "3187218881@qq.com",
    "price": "0.01",
    "buyer_id": "2088702106732978",
    "notify_id": "a8704516f5815ea1042bc2ba7688e68nhi",
    "use_coupon": "N",
    "sign_type": "RSA",
    "sign": "O3htsDXkDekXFImf8+Y+jUGmiuz++CX3GsRkw6m3lWWrLRU4Mm3NBt1ORmhq3ad3KhNPDOZO6VZzFWJZHIkT4s8dQEgUKzQ+8yE5iaZ4eEEBU2JLeXVNVYWuXHqEq9Wdmg/mDPfntXoDqr8Y8/dHIa6Qv/X2J+/gSSwjx+ycSjc="
}


微信支付
1. 去微信支付品台开通移动应用支付
wxc25022b28d3c63ec
2e31b201d3f7f266ed48cf0c00609249

以前的包名
com.bahl.lifepass
