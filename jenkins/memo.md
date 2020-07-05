## Dockerで動かす場合
参考：https://web.plus-idea.net/2019/07/proxy-jenkins-plugin-install-docker/
- コンテナイメージはDockerHub公式の `jenkins` よりjenkinsチームがメンテナンスしている `jenkins/jenkins` がよさそう
- コンテナから通信させるためにプロキシを通す必要あり

`-env JAVA_OPTS="-Dhttp.proxyHost=proxy_server -Dhttp.proxyPort=proxy_port -Dhttps.proxyHost=proxy_server -Dhttps.proxyPort=proxy_port"`
