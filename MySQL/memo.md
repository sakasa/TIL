# MySQL関連メモ

### 接続情報確認

```
SQL> \s
```

### オートコミット設定

- 確認

```
SQL> SELECT @@autocommit;
-- 1: ON
-- 0: OFF

```

- 設定

```
SQL> SET AUTOCOMMIT=0;  -- OFFにセット
-- SET AUTOCOMMIT=1;  -- ONにセット
```
