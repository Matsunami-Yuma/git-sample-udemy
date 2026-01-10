# Git学習ノート 🚀

Gitの基本操作やエラー解決方法をまとめる自分専用のメモです。

## 📋 基本の流れ（SNSの投稿に例えると）

1. **git pull**
   - 役割：最新の状態を取り込む
   - コマンド：`git pull`

2. **コードを書く、消すなどの作業をする**

3. **git add**
   - 役割：写真を撮る準備（ステージング）
   - コマンド：`git add <ファイル名>` または `git add .`（全部）

4. **git commit**
   - 役割：シャッターを切る（記録の確定）
   - コマンド：`git commit -m "メッセージ"`

5. **git push**
   - 役割：アルバムをサーバーに送る（共有）
   - コマンド：`git push origin main`

6. **git status**
   - 役割：状態の確認
   - コマンド：`git status`
   - 結果1：nothing to commit, working tree clean(リモートとローカルが完全に一致している)
   - 結果2：Untracked files(Gitの管理下に入っていないファイルがある)
        - 対応：`git add <ファイル名>`/`git add .`
   - 結果3：Changes not staged for commit(Gitの管理下に入っているがステージングではない)
        - 対応：`git add <ファイル名>`/`git add .`
   - 結果4：Changes to be commited(ステージング済みでコミット待ち)
        - 対応：`git commit -m "メッセージ"`
   - 結果5：Your branch is ahead/behind of ...(ローカルとリモートでコミット数に差がある)
        - 対応：`git push`(ahead)/`git pull`(behind)

## 🛠 トラブルシューティング

### プッシュが拒否された（rejected）とき
リモートに自分にはない更新がある場合に発生。
```bash
git pull --no-rebase origin main
```

### 失敗メモ
- `git rm`に`-d`オプションはない！
- ファイル削除は`git rm <ファイル名>`
- フォルダ削除は`git rm -r <フォルダ名>`

### 失敗を恐れないためのブランチ
- 直接`main`で作業すると、ミスした時に戻すのが大変。
- `git branch <ブランチ名>`でブランチを作成
- `git switch <ブランチ名>`で指定したブランチに移動
- `git checkout -b <ブランチ名>`でブランチを作成し移動までできる

### 📝 ブランチ作成のルール
- 新しいブランチは、作成した瞬間の親ブランチの状態を「コピー」する。
- 作った後は独立した道になり、お互いに影響しない。
- 綺麗なコピーを作るために、ブランチ作成前は `git commit` を忘れずに！

こんにちはBです