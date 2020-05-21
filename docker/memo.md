## install ping
```bash
yum install iputils
```
```bash
apt-get install iputils-ping
```

## install ip,etc...
```bash
yum install net-tools
```
```bash
apt-get install net-tools
```

## install ps,top,etc...
```bash
yum install procps
```
```bash
apt-get install procps 
```

## コンテナイメージubuntuでdocker-compose実行時に対話的インストールになることがあるので抑止する
参考：https://qiita.com/yagince/items/deba267f789604643bab
- Dockerfileに以下を記述
```
ENV DEBIAN_FRONTEND=noninteractive
```
