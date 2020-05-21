# メール配信テスト

## mailcatcher
- https://mailcatcher.me/
- ローカルでメール配信テストをする際にメールサーバの設定をmailcatcherにして、メールの確認を行える

### インストール
```bash
gem install mailcatcher
```

### 起動
```bash
mailmatcher [--ip 0.0.0.0] [-f]
```
オプションは任意

### メール設定
メールサーバを `localhost` にして、ポートを `1025` （ユーザー、パスワードはなしでOK）

### メール確認
ブラウザで `http://localhost:1080` にアクセス

※メール設定、メール確認のポートは起動オプションで変更可能

