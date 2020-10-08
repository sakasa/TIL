## sendmail
```bash
% sendmail [Toアドレス]
From: [Fromアドレス]
To: [Toアドレス] # ここは表示される値（実際のToはコマンドの第一引数）
Subject: 件名
 # 本文の前に空行
ここに本文を書く
. # 最後にドット
```

- SMTP
```bash
telnet [メールサーバーホスト] smtp
HELO [アカウントドメイン]
MAIL FROM: [Fromアドレス]
RCPT TO: [Toアドレス]
DATA
From: [Fromアドレス]
To: [Toアドレス]
Subject: 件名
 # 空行
ここに本文
. # 本文の終わりにドット
QUIT
```
