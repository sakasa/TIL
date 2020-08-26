## 公開バケットにhtmlを配置
`aws-cli` や アプリケーションでHTMLや画像などを配置する場合、 `ContentType` が `binary/octet-stream` になりブラウザのアクセスでコンテンツのダウンロードが開始される。
putする際に `ContentType` を指定するようにする。
HTMLの場合は、 `text/html` 。
画像の場合は画像の種類に合わせる。
