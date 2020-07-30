## Create Session API
- 定期支払の商品に対して `mode=payment` でリクエストすると `403` エラーが返ってくる
  - HTTPステータスより、レスポンスのメッセージをみたほうが良い `You specified `payment` mode but passed a recurring price. Either switch to ``subscription`` mode or use only one-time prices.`
