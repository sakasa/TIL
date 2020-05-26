## MeCabのインストール
```ipynb
!apt install aptitude
!aptitude install mecab libmecab-dev mecab-ipadic-utf8 git make curl xz-utils file -y
!pip install mecab-python3==0.7
!git clone --depth 1 https://github.com/neologd/mecab-ipadic-neologd.git && cd mecab-ipadic-neologd && bin/install-mecab-ipadic-neologd -n -y
```

## 言語処理で使いそうなライブラリ
```ipynb
!pip install emoji --upgrade
!pip install mojimoji --upgrade
!pip install janome --upgrade
!pip install SudachiPy --upgrade
!pip install https://object-storage.tyo2.conoha.io/v1/nc_2520839e1f9641b08211a5c85243124a/sudachi/SudachiDict_core-20200330.tar.gz
!pip install gensim --upgrade

```
