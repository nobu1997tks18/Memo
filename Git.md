# Git

## 基本操作
|||
|:--|:--|
|ディレクトリにgitを追加|	git init
|ディレクトリのファイルがインデックスに一時保存される|	git add -A
|Gitの状態を確認|	git status

## Github関係
|||
|:--|:--|
|リモートリポジトリ作成|	git remote add origin URL
originになっていれば完了|	git remote
|リモートの紐付け削除|	git remote rm origin
|git管理を外す|	rm -rf .git/
|ローカルのブランチをリモートに反映、最初のプッシュ|	git push --set-upstream origin master
|ブランチ名(リモートリポジトリのブランチをローカルに反映、最初のプル|	git pull
|ブランチを指定してpull|	git pull origin ブランチ名

## commit関係
|||
|:--|:--|
|コミットしてインデックスからリポジトリに反映|	git commit -m “命令形メッセージ”
|直前のコミットメッセージ修正|	git commit -amend -m “メッセージ”
|コミットメッセージの一覧を表示|	git log
|コミットを指定して戻る|	git reset --hard ハッシュ値

## issue関係
|||
|:--|:--|
コミットメッセージに#issue番号	git commit -m “メッセージ #0”

## stash関係
|||
|:--|:--|
|変更を退避|	git stash
|退避する作業にメッセージを付ける|	git stash save "stash message”
|一覧を確認|	git stash list
|退避した作業を戻す|	git stash apply stash@{0}
|退避した作業を消す|	git stash drop stash@{0}
|戻すと同時に消す|	git stash pop stash@{0}
|作業の詳細を見る|	git stash show stash@{0}

## push関係
|||
|:--|:--|
|ローカルのブランチの変更をリモートに反映|	git push
|プッシュの前後にリモートの変更をローカルに同期する|	git pull
変更を確認|	git fetch

## marge関係
|||
|:--|:--|
|今のブランチに選択したブランチをマージ|	git merge ブランチ名
|マージされた側でCommitMargeやRevertMargeを番号を指定して取り消す|	git revert -m 1 マージ番号
＊revertした場合は必ずプルリクエストまで出す


## branch関係
|||
|:--|:--|
|変更を強制的に上書きして元に戻す、マスターブランチで作業してしまった時使用|	git checkout -f
|ブランチを作成|	git checkout -b ブランチ名
|ブランチを変更|	git checkout ブランチ名
|ファイルの変更を削除|	git checkout -- ファイル名
|ブランチ削除|	git branch -d ブランチ名
|branchの一覧を表示|	git branch
|ブランチから変更データを仮置きすることができる|	git stash
|マスターの状態をブランチに反映させることができる、最新のマスターをブランチに反映させるために使う|	git rebase master

## その他
|||
|:--|:--|
|GitHub上から指定のファイルを完全に消去|	find . -name .ファイル前 -print0 | xargs -0 git rm

## GitIgnore
* ディレクトリの最上部に.gitignoreを作成
* 管理対象から外すファイルを記述
* すでにコミット済みの場合は以下のコマンドが必要
* git rm --cached -r path
    * --cachedありの場合ファイル自体は残す
    * --cachedなしの場合ファイル自体を削除

## コミットメッセージの書き方(一例)
  * 1行目：要約の内容
  * 2行目：空行
  * 3行目：変更理由

## プルとフェッチの違い
  * プルはリモートの更新状態を引っ張ってローカルを更新する
  * フェッチは更新状態の確認のみで更新自体は実行されない

## mergeとrebase の違い
  * mergeは変更内容はそのまま残るが履歴は複雑になる
  * rebaseは最新のマスターとの違いを認識して変更する
  * masterブランチが変更が入っていた場合エラーが起こる可能性がある

