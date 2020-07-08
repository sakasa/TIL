- `git switch` と `git restore`　https://qiita.com/yukibear/items/4f88a5c0e4b1801ee952
 

## Forkリポジトリをオリジナルリポジトリに追従する
- フォークにリモートを設定する

参考：https://docs.github.com/ja/github/collaborating-with-issues-and-pull-requests/configuring-a-remote-for-a-fork

オリジナルのリポジトリを `upstream` という名前でリモートリポジトリに追加（ `remote add` ）する
```bash
git remote add upstream [オリジナルリポジトリURL]
```

- フォークを同期する

参考：https://docs.github.com/ja/github/collaborating-with-issues-and-pull-requests/syncing-a-fork

リモートリポジトリをフェッチ
```
git fetch upstream
```
マスターブランチをチェックアウト
```
git checkout master
```
ローカルにマージ
```
git merge upstream/master
```
