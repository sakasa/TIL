参考
- https://docs.aws.amazon.com/ja_jp/general/latest/gr/aws-ip-ranges.html
- https://qiita.com/akaaariiiiin/items/e840adb7e9b8024d8519
- https://public-constructor.com/shel-jq-variable/

---
### 全リージョン・全サービス
```bash
curl https://ip-ranges.amazonaws.com/ip-ranges.json \
  |jq -r '.prefixes' \
  |jq 'sort_by(.region, .service, .ip_prefix) | .[]' \
  |jq -r 'select(has("ip_prefix")) | [.region, .service, .ip_prefix, .network_border_group] | @csv'
```

### リージョン指定
```bash
AWS_REGION_PREFIX=ap-northeast # 取得するリージョンのプレフィックス

curl https://ip-ranges.amazonaws.com/ip-ranges.json \
  |jq -r '.prefixes' \
  |jq 'sort_by(.region, .service, .ip_prefix) | .[]' \
  |jq --arg region ${AWS_REGION_PREFIX} -r 'select(has("ip_prefix")) |select(.region |test($region)) | [.region, .service, .ip_prefix, .network_border_group] | @csv'
```

### サービス指定
```bash
AWS_SERVICE_PREFIX=EC2 # 取得するサービスのプレフィックス

curl https://ip-ranges.amazonaws.com/ip-ranges.json \
  |jq -r '.prefixes' \
  |jq 'sort_by(.region, .service, .ip_prefix) | .[]' \
  |jq --arg service ${AWS_SERVICE_PREFIX} -r 'select(has("ip_prefix")) |select(.service |test($service)) | [.region, .service, .ip_prefix, .network_border_group] | @csv'
```

### リージョン・サービス指定
```bash
AWS_REGION_PREFIX=ap-northeast
AWS_SERVICE_PREFIX=EC2

curl https://ip-ranges.amazonaws.com/ip-ranges.json \
  |jq -r '.prefixes' \
  |jq 'sort_by(.region, .service, .ip_prefix) | .[]' \
  |jq --arg region ${AWS_REGION_PREFIX} --arg service ${AWS_SERVICE_PREFIX} -r 'select(has("ip_prefix")) |select(.region |test($region)) |select(.service |test($service)) |[.region, .service, .ip_prefix, .network_border_group] |@csv'
```
