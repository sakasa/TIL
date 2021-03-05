- https://redocly.github.io/redoc/
- https://github.com/Redocly/redoc

### redoc-cliでyamlからhtmlを生成
```
# on local
$ ls
openapi.yaml
$ docker run --rm -it -v$(pwd):/tmp node bash

# on container
$ cd /tmp
$ npm i -g redoc-cli
$ redoc-cli bundle openapi.yaml
$ ls
openapi.yaml redoc-static.html
$ exit

# on local
$ ls
openapi.yaml redoc-static.html
```
