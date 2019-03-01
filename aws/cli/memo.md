# aws-cli関連メモ

## localstack使用時のオプション
`aws configure` で `localstack` を設定済みの前提
 
```
$ aws --endpoint-url http://localhost:{サービスごとのポート} --profile localstack <command> <subcommand>

# Ex.
$ aws --endpoint-url http://localhost:4572 --profile localstack s3 ls
```

## localstack使用

### s3

#### s3オブジェクト確認

```
$ aws --endpoint-url="http://localhost:4572" --profile localstack s3 ls [{オブジェクト名}/]
```

#### s3バケット作成

```
$ aws --endpoint-url="http://localhost:4572" --profile localstack s3 mb s3://{バケット名}
```

#### s3オブジェクト同期（削除なし）

```
$ aws --endpoint-url="http://localhost:4572" --profile localstack s3 sync {同期元} {同期先}  # ローカル→s3、s3→ローカルどちらも可能
```

#### s3オブジェクト同期（削除あり）

```
$ aws --endpoint-url="http://localhost:4572" --profile localstack s3 sync {同期元} {同期先} --delete
```

#### s3オブジェクトコピー

```
$ aws --endpoint-url="http://localhost:4572" --profile localstack s3 cp {コピー元} {コピー先}  # ローカル→s3、s3→ローカルどちらも可能
```

#### s3オブジェクト削除

```
$ aws --endpoint-url="http://localhost:4572" --profile localstack s3 rm s3://{オブジェクト名}
```

### sqs

#### sqsキュー作成

```
$ aws --endpoint-url="http://localhost:4576" --profile localstack sqs create-queue --queue-name {キュー名}
```

#### sqsキュー確認

```
$ aws --endpoint-url="http://localhost:4576" --profile localstack sqs list-queues
```

### ssm

#### ssmパラメータストア作成

```
$ aws --endpoint-url="http://localhost:4583" --profile localstack ssm put-parameter \
    --name {パラメータストア名} \
    --value {セットする値（json形式）} \
    --type SecureString  # ※
```
※ [SecureStringパラメータ](https://docs.aws.amazon.com/ja_jp/systems-manager/latest/userguide/sysman-paramstore-about.html#sysman-paramstore-securestring) を使用する場合

#### ssmパラメータストア確認

```
$ aws --endpoint-url="http://localhost:4583" --profile localstack ssm get-parameters --name {パラメータストア名}
```

