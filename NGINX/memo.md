## SSIの有効化
`/etc/nginx/conf.d/default.conf`
```default.conf
server {
    listen       80;
    server_name  localhost;
 
    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
        # 以下を追記する
        ssi  on;
        ssi_last_modified on;
    }
```
