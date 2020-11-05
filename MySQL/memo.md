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

### DBとテーブルのサイズ確認
- DB

mysqlに接続した状態で（DBを選択していなくてもOK）
```
SELECT 
    table_schema, sum(data_length) /1024/1024 AS mb 
FROM 
    information_schema.tables  
GROUP BY 
    table_schema 
ORDER BY       
    sum(data_length+index_length) DESC;
```

- テーブル

mysqlに接続して対象DBに入っている状態で
```
SELECT  
    table_name, engine, table_rows AS tbl_rows,
    avg_row_length AS rlen,  
    floor((data_length+index_length)/1024/1024) AS allmb,  #総容量
    floor((data_length)/1024/1024) AS dmb,  #データ容量
    floor((index_length)/1024/1024) AS imb   #インデックス容量
FROM 
    information_schema.tables  
WHERE
    table_schema=database()  
ORDER BY
    (data_length+index_length) DESC;
```
参考：https://qiita.com/ikenji/items/b868877492fee60d85ce

### コネクション数などの確認
参考: https://qiita.com/snaka/items/b6e7500c96e04c131d9e

- 現在の接続しているスレッド数
```sql
show status like 'Threads_connected';
```
```sql
SELECT * FROM information_schema.PROCESSLIST;
```

- プロセスリスト（処理中の接続）
```sql
show processlist;
```

### テーブル定義の確認
- CREATE TABLE文を取得
```sql
SHOW CREATE TABLE tablename;
```

- SQLの結果で取得
```sql
SHOW FULL COLUMNS FROM tablename;
```
```sql
DESC tablename;
```

### テーブルコピー
- 定義をコピーしてデータをインサート
```sql
CREATE TABLE newtable LIKE oldtable;
INSERT INTO newtable SELECT * FROM oldtable;
```

- データ（と定義）を使ってコピー
```sql
CREATE TABLE newtable SELECT * FROM oldtable;
```
