# 2025/08/05(火)
## 📚 プラクティス『プログラムの修正（リバーシ編）』


### 🧩 タスクばらし
- [x] プラクティスの内容を咀嚼
- [x] タスクばらし、スモールステップの作成
- [x] ソースコードの言語化
- [x] ソースコードを修正
- [ ] 課題提出


### 🐾 スモールステップ
<details><summary>プラクティスの内容を咀嚼</summary>

- [x] プラクティスの内容を咀嚼
</details>

<details><summary>タスクばらし、スモールステップの作成</summary>

- [x] タスクばらし、スモールステップの作成
</details>

<details><summary>ソースコードの言語化</summary>

- [x] ソースコードの言語化 **※①から順に行う**
  - [x] ① reversi_methods_test.rb
  - [x] ② reversi.rb
  - [x] ③ reversi_methods.rb
  - [x] ④ position.rb


</details>

<details><summary>ソースコードを修正</summary>

- [x] ソースコードを修正
  - test_cannot_put_stone
    - [x] 修正
  - test_finished_of_quickest_win_board
    - [x] 修正
  - test_put_stone
    - [x] 修正
  - test_turn
    - [x] 修正
  - test_finished_of_full_board
    - [x] 修正

</details>

<details><summary>課題提出</summary>

- [x] 修正したソースコードを Pull Request としてアップ
- [x] Pull Request としてアップした URL とテストコードの実行結果を提出
</details>


---
### 🧑🏻‍💻 本日の取り組み
#### プラクティス『プログラムの修正（リバーシ編）』
- Pull Request を再提出


---


### 🎯 次回
#### プラクティス『lsコマンドを作る1』
- 内容の確認・理解・把握
    

---


### 💡 本日の学び・気付き
#### Pull Request 再提出

##### 1. （ステージングしてコミットする前に）修正した内容を確認
```shell
~/bug_reversi/lib % cat reversi_methods.rb
# frozen_string_literal: true

require_relative './position'

module ReversiMethods
  WHITE_STONE = 'W'
  BLACK_STONE = 'B'
  BLANK_CELL = '-'
...
# 以下ネタバレになるため省略
```

##### 2. リポジトリのルート（作業ディレクトリ）に移動
```shell
~ % cd bug_reversi 
~/bug_reversi %
```

##### 3. リポジトリの状態を確認
```shell
~/bug_reversi % git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   lib/reversi_methods.rb

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.vscode/

no changes added to commit (use "git add" and/or "git commit -a")
```

##### 4. git checkout -b debug mainコマンドを実行
```shell
~/bug_reversi % git checkout -b debug main
M	lib/reversi_methods.rb
Switched to a new branch 'debug'
```
- `-b debug`：`debug`ブランチを作成。
- `main`：`debug`ブランチの「土台」として、既存の`main`ブランチの最新のコミットから分岐させる。
- `checkout`：`debug`ブランチに切り替える。

##### 5. リポジトリの状態を確認
```shell
~/bug_reversi % git status
On branch debug
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   lib/reversi_methods.rb

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.vscode/

no changes added to commit (use "git add" and/or "git commit -a")
```

##### 6. パーミッションを確認 → リポジトリ内のファイル・ディレクトリの権限を777（全ユーザー読み・書き・実行可）に設定
**※ もしかして蛇足かもしれませんが......**
```shell
~/bug_reversi % ls -l
total 16
drwxr-xr-x  4 yoshiwo  staff   128  4 23 17:14 lib
-rw-r--r--  1 yoshiwo  staff  2992  4 23 17:14 README.md
-rw-r--r--  1 yoshiwo  staff  1292  7  9 18:22 reversi.rb
drwxr-xr-x  3 yoshiwo  staff    96  4 23 17:14 test
~/bug_reversi % chmod -R 777 .
~/bug_reversi % ls -l
total 16
drwxrwxrwx  4 yoshiwo  staff   128  4 23 17:14 lib
-rwxrwxrwx  1 yoshiwo  staff  2992  4 23 17:14 README.md
-rwxrwxrwx  1 yoshiwo  staff  1292  7  9 18:22 reversi.rb
drwxrwxrwx  3 yoshiwo  staff    96  4 23 17:14 test
```

##### 7. リポジトリの状態を確認
```shell
~/bug_reversi % git status
On branch debug
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md
	modified:   lib/position.rb
	modified:   lib/reversi_methods.rb
	modified:   reversi.rb
	modified:   test/reversi_methods_test.rb

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.vscode/

no changes added to commit (use "git add" and/or "git commit -a")
```

##### 8. モードの変更をステージングする
```shell
~/bug_reversi % git add -u
```
- `-u`オプション：Git の管理下にあるファイルの変更をまとめて行う。

##### 9. モードの変更をコミット
```shell
~/bug_reversi % git commit -m "ファイルやディレクトリのパーミッションを777に設定"
[debug 3ada2ea] ファイルやディレクトリのパーミッションを777に設定
 5 files changed, 3 insertions(+), 1 deletion(-)
 mode change 100644 => 100755 README.md
 mode change 100644 => 100755 lib/position.rb
 mode change 100644 => 100755 lib/reversi_methods.rb
 mode change 100644 => 100755 reversi.rb
 mode change 100644 => 100755 test/reversi_methods_test.rb
```

##### 10. 修正したファイルのコミット
```shell
~/bug_reversi % git add lib/reversi_methods.rb
~/bug_reversi % git commit -m "reversi_methods.rbファイルの修正"
On branch debug
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.vscode/

nothing added to commit but untracked files present (use "git add" to track)
```

##### 11. .vscode/ディレクトリを.gitignoreに追加して無視するように設定
```shell
~/bug_reversi % echo ".vscode/" >> .gitignore
~/bug_reversi % git add .gitignore
~/bug_reversi % git commit -m ".vscodeを無視する"         
[debug 0e51173] .vscodeを無視する
 1 file changed, 1 insertion(+)
 create mode 100644 .gitignore
```

##### 12. リモートリポジトリ（GitHub）にプッシュ
```shell
~/bug_reversi % git push origin debug   
Enumerating objects: 12, done.
Counting objects: 100% (12/12), done.
Delta compression using up to 8 threads
Compressing objects: 100% (7/7), done.
Writing objects: 100% (8/8), 920 bytes | 920.00 KiB/s, done.
Total 8 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
remote: 
remote: Create a pull request for 'debug' on GitHub by visiting:
remote:      https://github.com/YSWEngineer/bug_reversi/pull/new/debug
remote: 
To https://github.com/YSWEngineer/bug_reversi.git
 * [new branch]      debug -> debug
```

##### 13. GitHubホームページの Pull requestタブをクリック
右上の`Compare & pull request`ボタンをクリック
<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMklDQkE9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--f99c7147e89faf2eca6ca090cd35eca5da8562d8/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202025-08-04%2020.50.24.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMklDQkE9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--f99c7147e89faf2eca6ca090cd35eca5da8562d8/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202025-08-04%2020.50.24.png" width="3104" height="1974" alt="スクリーンショット 2025-08-04 20.50.24.png"></a>

##### 14. Pull Requestのタイトルと詳細を記載
記載したら`Create pull request`ボタンをクリック。
<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMk1DQkE9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--c43237b4d3e5abf14b0419e74bf4279f79641036/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202025-08-04%2021.01.28.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMk1DQkE9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--c43237b4d3e5abf14b0419e74bf4279f79641036/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202025-08-04%2021.01.28.png" width="3104" height="1974" alt="スクリーンショット 2025-08-04 21.01.28.png"></a>

##### 15. 作成された Pull Request の URL をコピー

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMlFDQkE9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--612c4e17e8b3812855762882545aa4eaf37651c9/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202025-08-04%2021.02.15.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMlFDQkE9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--612c4e17e8b3812855762882545aa4eaf37651c9/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202025-08-04%2021.02.15.png" width="3104" height="1974" alt="スクリーンショット 2025-08-04 21.02.15.png"></a>


---


### ✍🏻 感想
#### 🧑🏻‍💻 久し振りの Pull Request
カレンダー問題の Pull Request を出したのを最後に、かなり時間が空いていたので、ちゃんとできるか不安でしたが、`README`に書かれていた手順通りに進めて無事に作成することができました。

とはいえ、個人的に気になっていることが2つあります。

- パーミッションの設定はこれで大丈夫だったのか？
- `.vscode/`を無視する設定は他の人はどうしているんだろう？

という点です。他の方のやり方も気になります。

それでも、なんとか提出まで辿り着きました。長かった......本当に長かった......。メンターさんからのお返事を待って、次はいよいよ新しいプラクティスへ。皆さんが「難しい」と口を揃える『lsコマンド』、どんな内容なんだろう？仲良くなれるといいな。


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3 hours 05 min
- Total: 1211 hours 30 min
