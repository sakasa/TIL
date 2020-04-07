# PHP

## Laravel
.envファイルの値に `#` を使用する場合はダブルクオートで囲む
例
```sh
DB_PASS=12Ab#;xx04   # `#` 以降がコメントになって使用できない
DB_PASS="12Ab#;xx04" # 正しく認識される
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
