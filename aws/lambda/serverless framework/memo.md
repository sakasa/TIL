## Serverless Framework で Lambda Layers のバージョンを指定せずにデプロイする方法
参考： http://blog.serverworks.co.jp/tech/2019/06/03/sls-lambdalayers/

layerに以下を指定する
setverless.yml
```yaml
...
function
  sample-function:
    handler: lambda_function.lambda_handler
    layers:
      - ${cf:[スタック名].[出力キー]}
...
```
