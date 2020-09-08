git_mycheatsheet

# gitの利用目的
昔の変更履歴を管理
別機能を開発するために、異なるバージョンを同時並行で開発

# コード共同編集の基本的な流れ
1. ファイルをダウンロードする "git pull"
1. コードを変更する 
1. 共有したいファイルを選択する "git add" "git remote add"
1. 選択したファイルを記録する "git commit"
1. 共有する "git commit" "git push"

# git における3つの状態
1. 作業ディレクトリ
1. ステージングエリア（インデックス）
1. リポジトリ

１→２　意味のあるまとまりで保存していく


# 基本コマンド集

## gitフォルダの 新規作成 "git init"
`git init`
--bare : 作業ディレクトリを持たない（コミットできない）

## gitフォルダのクローン作成 "git clone"
`git clone <クローンしたいgitフォルダの場所>`
場所は、パスまたはgithubURLでも可能
紐付けはあるので`git remote add`は不要

## ファイルの共有準備 "git add"
`git add <共有したいファイル名>`
フォルダ全体の場合は
`git add .`

## ファイルのコミット "git commit"
`git commit -m "<コメント>"`
⭐️メッセージは、どんな修正を行ったかはっきりと端的に！
`git commit --ammend`
直前のコミットを変更してコミット（新しくコミット履歴が残らない）

## リモートで共有準備 "git remote add"
`git remote add <リモート名> <リモート先URL>`
リモート名はクライアント側で一意に認識するためのもの

## リモート先に共有 "git push"
`git push <リモート名> <ブランチ名>`
`git push -u <リモート名> <ブランチ名>`
-u : 次回以降は`git push`のみで、今回引数に指定したリモート名、ブランチ名でpushしてくれる

## リモートからファイルをダウンロード "git pull"
`git pull <リモート名> <ブランチ名>`

## 変更したファイルのうち、starged(addされている)かを確認 "git status"
`git status`

## ファイルを直前コミット時の状態に戻す "git restore"
`git restore <ファイル名>`

## ステージング中のファイルを作業リポジトリに戻す "git restore --staged"
`git restore --staged <ファイル名>`

## コミット後のファイルの移動 "git mv"
`git mv <ファイル名>`

## gitで紐づいたものを全体でファイルの削除
`git rm <ファイル名>`

## 差分を表示 "git diff"
↓作業ディレクトリのもの
`git diff`
↓ステージング状態のもの
`git diff --cached`

## コミット履歴の確認 "git log"
`git log` 変更履歴の表示
`git log -p <コミットID>` 変更履歴＋差分の表示
`git log --oneline` 各変更履歴を一行表示
`git log --stat` 変更ファイル数、また各ファイルの変更箇所数を表示

## コミットのタグ付け "git tag"
`git tag <タグの名前> <コミットID>`
<コミットID>：なければHEAD（直前のコミット）
`git tag -d <タグの名前>`
タグの削除


## コミットの内容を見る "git show"
`git show <コミットID or タグの名前>`


## "git config" コマンドのヘルプをみたい時
`git config --help`
`git help config`

"help"部を別のコマンドに差し替えても
同様にヘルプ、オプションの参照が可能

## コマンドのエイリアスを設定 "git config --global alias"
`git config --global alias.<略称> <コマンド名>`
ex.) git config --global alias.co checkout

## 直前のコミットに戻す "git reset"
`git reset --hard <コミットID>`
--hard : ステージングを含める（作業ディレクトリのみならず）
<コミットID> 
HEAD : (直前)
HEAD^ : (直前の直前)
ORIG_HEAD : 直前のリセットをなかったことにする
タグの名前：タグの名前がついたコミット

## ブランチについて "git branch"
ブランチ一覧、自分が居るブランチを知る
`git branch`
ブランチを作る
`git branch <ブランチ名>`
ブランチを削除する
`git branch -d <ブランチ名>`
<ブランチ名>の書き方
【ブランチルール】
feat/[issueの番号]/[作業内容]
例：feat/1/createWebTemplate

## ブランチを移動する "git checkout"
`git checkout <ブランチ名>`

## ブランチをマージする "git merge"
`git merge <ブランチ名>`
ブランチ名はマージさせたい先のブランチ名を指定する
例：masterから `git branch hoge`

## 変更を退避する "git stash"
作業途中なのでコミットしたくないが一時的に退避させたい、というときに使う
退避の実行
`git stash`
`git stash save "コメント"`

退避の一覧
`git stash list`

退避を取り出す
`git stash pop`
`git stash pop stash@{<引数>}`



# gitで共有しないファイルを指定 .gitignore ファイルを作成
そのファイルがある階層以下で機能
サブディレクトリにおいても良い

# マージでコンフリクトが起きた場合
コンフリクトが起きたファイルに両方の内容が記載されているので
反映させたい側の内容だけを残し（周りのテンプレートも削除）
add と commitを行う
