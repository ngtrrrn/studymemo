# git の基本コマンド

## gitフォルダの 新規作成 "git init"
`git init`

## ファイルの共有準備 "git add"
`git add <共有したいファイル名>`
フォルダ全体の場合は
`git add .`

## ファイルのコミット "git commit"
`git commit -m "<コメント>"`
⭐️メッセージは、どんな修正を行ったかはっきりと端的に！

## リモートで共有準備 "git remote add"
`git remote add <リモート名> <リモート先URL>`

## リモート先に共有 "git push"
`git push <リモート名> <ブランチ名>`

## リモートからファイルをダウンロード "git pull"
`git pull <リモート名> <ブランチ名>`

## 変更したファイルのうち、starged(addされている)かを確認 "git status"
`git status`

## 差分を表示 "git diff"
`git diff`

## コミット履歴の確認 "git log"
`git log` 変更履歴の表示
`git log -p` 変更履歴＋差分の表示




# コード共同編集の基本的な流れ
1. ファイルをダウンロードする "git pull"
1. コードを変更する 
1. 共有したいファイルを選択する "git add" "git remote add"
1. 選択したファイルを記録する "git commit"
1. 共有する "git commit" "git push"
