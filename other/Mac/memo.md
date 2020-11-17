## 隠しファイルの表示
command⌘ + shift⇧ + .


## アニメーションGif作成
1. 「cmd + 5」でキャプチャしてmovファイルを作成
2. `ffmpeg` でgifファイルを作成
```
ffmpeg -i {movファイル}.mov -r 24 {Gifファイル}.gif
```
参考 : https://qiita.com/wMETAw/items/fdb754022aec1da88e6e
