# 自然言語処理（Natural Language Processing）

## 形態素解析器

### MeCab
https://taku910.github.io/mecab/
* install
```bash
# install library
apt-get -y install mecab libmecab-dev mecab-ipadic-utf8

# setup dictionary NEologd
git clone --depth 1 https://github.com/neologd/mecab-ipadic-neologd.git
cd mecab-ipadic-neologd
./bin/install-mecab-ipadic-neologd -n -y

# install python lib
pip install mecab-python3 --upgrade
```

### Janome
https://mocobeta.github.io/janome/
* install
```bash
pip install janome
```

### Sudachi
https://github.com/WorksApplications/SudachiPy
* install
```bash
pip install sudachipy
```

### Nagisa
https://github.com/taishi-i/nagisa
* install
```bash
pip install nagisa
```
