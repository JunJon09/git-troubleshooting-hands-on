# Gitのトラブルシューティング

## mainブランチで作業してしまい別のブランチに移動する方法
1 コードを避難 -> 2 ブランチを変更 -> 3 コードを元に戻す．

1. コードを避難
```
git stash
```

2. ブランチを作成
```
git branch issue1
git checkout issue1
```
or 
```
git checkout -b issue1
```

3. コードを元に戻す
```
git stash pop
```

> [!Tip]
> コミットしてしまった後に気づいてしまった場合 <br>
```
git checkout -b issue1
git checkout main
git reset --hard HEAD~1
git checkout issue1
```

## コンフリクト
1. '<<<<<<<' HEAD (自分の変更)
2. '=======' (区切り線)
3. '>>>>>>>' [ブランチ名] (相手の変更)
4. マークの削除: <<<<<<<, =======, >>>>>>> をすべて削除し、正しいコードにする。
5. ステージング: git add <ファイル名> で修正をステージ。
6. コミット: git commit でマージを完了させる

## 開発中に main が進んでしまった時の追従
``` 
git merge main
```


## コマンドまとめ

|アクション|コマンド|目的|
|作業退避|git stash|ブランチの移動|
|コンフリクト解消|git merge|複数人開発での衝突回避|
|最新化|git pull|古いコードベースで開発し続けるのを防ぐ|
