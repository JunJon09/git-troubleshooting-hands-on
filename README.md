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

