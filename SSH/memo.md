## SSHトンネル経由でSFTP
参考：https://qiita.com/Zero_Kohaku/items/308c73fa1ab355699032

```bash
$ ssh [-i ssh_key.pem] -L ＜任意のポート番号＞:＜接続先のIPアドレス＞:＜接続先ポート＞ ＜踏み台のユーザ名＞@＜踏み台のIPアドレス＞ -p ＜踏み台ポート＞
```
※任意のポート番号・・・ローカルの任意のポート<br>
※接続先・・・踏み台からのsshのみ許可<br>
※踏み台・・・ローカルからssh可能<br>
※踏み台の認証に鍵ファイルを使う場合 `-i` オプションで指定<br>
<br>

ex.
- 接続先: user@10.0.0.1:22
- 踏み台： humidai_user@1.2.3.4:22
- ローカル: localhost:1022
- 踏み台鍵ファイル: ssh_key.pem
<br>

1. ローカルのターミナルでコマンド実行
```bash
ssh -i ssh_key.pem -L 1022:10.0.0.1:22 humidai_user@1.2.3.4 -p 22
```
2. 以下設定でsftp
```text
ホスト: localhost
ポート: 1022
ユーザー: user
認証: 接続先で使用する認証（パスワード、鍵ファイル等）
```
