## Create Session API
- 定期支払の商品に対して `mode=payment` でリクエストすると `403` エラーが返ってくる
  - HTTPステータスより、レスポンスのメッセージをみたほうが良い `You specified `payment` mode but passed a recurring price. Either switch to ``subscription`` mode or use only one-time prices.`
- 消費税は `line_items[].tax_rate[]` を配列で渡す
```
"line_items": [
  {
    "price": "price_H5ggYwtDq4fbrJ",
    "quantity": 2,
    "tax_rate": ["tax_123XYZ"]
  }
]
```
- トライアル期間は `subscription_data.trial_period_days` で渡す
```
"line_items": [
  {
    "price": "price_H5ggYwtDq4fbrJ",
    "quantity": 2,
    "tax_rate": ["tax_123XYZ"]
  }
],
"subscription_data": {
  "trial_period_days": 30
}
```
- クーポンは `subscription_data.coupon` で渡す
```
"line_items": [
  {
    "price": "price_H5ggYwtDq4fbrJ",
    "quantity": 2,
    "tax_rate": ["tax_123XYZ"]
  }
],
"subscription_data": {
  "coupon": "aXaXaX"
}
```
- Stripe Checkputは「標準の料金体系」以外はサポート外
  - APIのエラーレスポンス `Checkout does not support package pricing, aka ``transform_quantity`` in ``line_items[price][0]``.`

