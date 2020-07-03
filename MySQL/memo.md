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
