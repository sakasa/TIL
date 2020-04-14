# PHP

## Laravel
### .envファイルの値に `#` を使用する場合はダブルクオートで囲む
例
```sh
DB_PASS=12Ab#;xx04   # `#` 以降がコメントになって使用できない
DB_PASS="12Ab#;xx04" # 正しく認識される
```

### Laravelのバージョンを指定してプロジェクトを作成
```bash
# composer create-project "laravel/laravel=バージョン" プロジェクト名
composer create-project "laravel/laravel=6.*" sample-project名
```

### プロジェクトを `git clone` したあとにやること
参考：http://vdeep.net/laravel-git-clone
1. ライブラリの取得
```bash
composer install

# composer.lockがない場合
composer update
```
2. `.env` ファイルの作成
  - 環境ごとのファイルが有る場合そのファイルをコピーorシンボリックリンクを作成
  - ない場合、新規作成（ `.env.example` をコピー）し内容を編集
3. アプリケーションキーの初期化
```bash
php artisan key:generate
```
4. DBマイグレーション（必要な場合）
```bash
php artisan migrate
```
5. DBデータ投入（必要な場合）
```bash
php artisan db:seed
```
  - エラー（ `[ReflectionException]` とか `Class ‘HogeHoge’ not found` など）になった場合
```bash
composer dump-autoload
```
  - マイグレーション＆seed実行（データ投入）のやり直し
```bash
php artisan migrate:refresh --seed
```

### `.env` 反映されないとき
```bash
php artisan config:cache
```

### モデルインスタンスの作成
```bash
php artisan make:model {Model}
php artisan make:model {Model} -m // migrationファイルも作成
```

### マイグレーション
#### マイグレーションの作成
```bash
php artisan make:migration create_{Model}s_table
```
#### マイグレーション実行
```bash
php artisan migrate
```
#### 現在の状態
```bash
php artisan migrate:status
```
#### 削除
```bash
php artisan migrate:reset
```
#### 作り直し
```bash
php artisan migrate:fresh
```
#### 作り直したあとのキャッシュクリア
```bash
php artisan cache:clear
php artisan config:clear
```

### コントローラ作成
```bash
php artisan make:controller {Controller}
```

### ミドルウェアの作成
```bash
php artisan make:middleware {Middleware}
```


### blade
#### テキストエリアで送信された文字を表示する
```php
{! nl2br(e($param)) !}
```
  - `e()` ・・・HTMLエスケープ
  - `nl2br` ・・・改行を `<br>` に変換
  - `{!` 〜 `!}` ・・・HTMLエスケープ無しで表示

#### `Form` クラスを使う
https://laravelcollective.com/docs/6.0/html
```bash
composer require laravelcollective/html
```

## dockerのAmazonLinux2にhttpdとphpをインストールしてapacheを起動した際にエラーが発生したときの対処
- エラー： `ERROR: [pool www] failed to read the ACL of the socket '/run/php-fpm/www.sock': Operation not supported (95)`
- 参考：http://blog.livedoor.jp/sire2/archives/51264184.html
- 対処： `/etc/php-fpm.d/www/conf` を編集
```conf
# 有効化して値を「apache」に
listen.owner = apache
listen.group = apache

↓無効化する
;listen.acl_users = apache,nginx
```
