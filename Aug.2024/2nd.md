# 2024/08/02(金)
## 🧩 タスクばらし
### プラクティス『FizzBuzz問題(Ruby)』の修了
- [x] 各参考ページを確認
- [x] FizzBuzz問題に取り組む
- [x] 課題提出
- [ ] 完了したら他の方の提出物と自分の提出物を見比べる


## 📋 段取り
<details><summary>各参考ページを確認</summary>

- [x] [rubyでコマンドを作る | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/articles/40)
- [x] [Gitで課題提出するまでの手順をまとめた（Sakiさんのブログ）](https://saki-htr.hatenablog.com/entry/2021/02/25/115930)
- [x] [Pull Requestのやり方](https://www.youtube.com/watch?v=XMgLL4qIyEA)
- [x] [GitHubでコードを提出するときに気をつけること](https://bootcamp.fjord.jp/pages/info-for-github)
- [x] [プルリクエスト形式で提出物を出す際の「これはやっちゃダメ」リスト](https://bootcamp.fjord.jp/reports/98547/edit)
</details>

<details><summary>FizzBuzz問題に取り組む</summary>

- [x] FizzBuzzプログラムを書く
</details>

<details><summary>課題提出</summary>

- [x] Pull Request としてアップする
- [x] URL と Terminal での実行結果を提出
</details>

<details><summary>完了したら他の方の提出物と自分の提出物を見比べる
</summary>

- [ ] 他の方の提出物と自分の提出物を見比べる
</details>


## ✍🏻 本日の取り組み
### プラクティス『FizzBuzz問題(Ruby)』
- 課題提出


## 💡 本日の学び・気付き
### 課題提出
#### 手順
1. Pull Request 作成のための雛形リポジトリからリポジトリを fork する。

![スクリーンショット 2024-08-02 14.10.32.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMXFrQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--6cafd8fb40e25ef219da951149908e31303f0b69/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-08-02%2014.10.32.png)

2. 自分のマシンにリポジトリをクローンする。
    1. Code から HTTPS を選択して HTTPS をコピー。
    2. `cd /tmp` を入力し、tmpディレクトリに移動。
    3. Terminal で `% git clone コピーしたHTTPS` を入力。
    4. lsコマンドで確認すると、**ruby-practices** というディレクトリができる。
```
ls
ruby-practices
```
3. `cd ruby-practices` で **ruby-practices** に移動し、lsコマンドで ruby-pracitcesディレクトリの中身を表示。
```
ls
01.fizzbuzz		03.bowling		05.wc			07.ls_object		99.wc_object
02.calendar		04.ls			06.bowling_object	98.rake			README.md
```
4. 作業用のブランチを作成する。
    1. `git branch fizzbuzz` と入力（fizzbuzzブランチを作成するコマンド）。
    2. `git branch` と入力し、fizzbuzzブランチが作成できたか確認。
```
git branch fizzbuzz
git branch
  fizzbuzz
* main
```
5. 作成した fizzbuzzブランチに移動する。
    1. `git switch fizzbuzz` と入力（fizzbuzzブランチに移動するコマンド）し、fizzbuzzブランチに移動。
    2. `git branch` と入力し、fizzbuzzブランチに移動できているか確認。
```
git switch fizzbuzz
Switched to branch 'fizzbuzz'
git branch
* fizzbuzz
  main
```
6. ここで、目的のコード（今回はFizzBuzz問題のプログラム（コード））を書く。
    1. （動画では）`vi 01.fizzbuzz/fizzbuzz.rb` と入力されている。
    2. エディター（編集）画面で FizzBuzz問題のプログラムを書く。
    3. プログラムを書き終えたら、`:wq` コマンドで保存・終了。
    4. `cat 01.fizzbuzz/fizzbuzz.rb` コマンドでファイルの中身を表示。
```
vi 01.fizzbuzz/fizzbuzz.rb
cat 01.fizzbuzz/fizzbuzz.rb
(1..20).each do |number|
  if number % 15 == 0
    puts "FizzBuzz"
  elsif number % 3 == 0
    puts "Fizz"
  elsif number % 5 == 0
    puts "Buzz"
  else
    puts number
  end
end
```
7. リポジトリの状態を確認。
    1. `git status` でリポジトリの状態を確認。
```
git status
On branch fizzbuzz
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	01.fizzbuzz/fizzbuzz.rb

nothing added to commit but untracked files present (use "git add" to track)
```
8. 作成したファイル`01.fizzbuzz/fizzbuzz.rb`をインデックスに add（登録）する。
    1. `git add 01.fizzbuzz/fizzbuzz.rb` と入力。
    2. `git status`でリポジトリの状態を確認。
```
git add 01.fizzbuzz/fizzbuzz.rb 
git status
On branch fizzbuzz
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   01.fizzbuzz/fizzbuzz.rb
```
9. 変更点をコミットする。
    1. `git commit -m ‘Add fizzbuzz’` （動画では）と入力。`-m` でコミットメッセージを付ける必要がある。今回はコミットメッセージに「Add FizzBuzz program」と入力。
```
git commit -m 'Add FizzBuzz program'
[fizzbuzz 8791e6f] Add FizzBuzz program
 1 file changed, 11 insertions(+)
 create mode 100644 01.fizzbuzz/fizzbuzz.rb
```
10. リポジトリの状態を確認。
    1. `git status` でリポジトリの状態を確認。
```
git status
On branch fizzbuzz
nothing to commit, working tree clean
```
11. リモートリポジトリに push する。
    1. `git push origin fizzbuzz` と入力。すると、**リモートリポジトリ（GitHub）にも fizzbuzzブランチが作成**される。
    2. GitHub に戻り、画面を更新させて、左にあるブランチをクリックして fizzbuzzブランチが作成されたことを確認。
```
git push origin fizzbuzz
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 454 bytes | 454.00 KiB/s, done.
Total 4 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'fizzbuzz' on GitHub by visiting:
remote:      https://github.com/YSWEngineer/ruby-practices/pull/new/fizzbuzz
remote: 
To https://github.com/YSWEngineer/ruby-practices.git
 * [new branch]      fizzbuzz -> fizzbuzz
```

![スクリーンショット 2024-08-02 14.58.51.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMStrQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--02983c3d789f067dece982bd39798d86fee65fe9/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-08-02%2014.58.51.png)

12. Pull Request を作成。
    1. Pull requests タブをクリック、New pull request をクリック。
    2. komagata の fizzbuzzブランチから、komagata の mainブランチに PR を送るので、プルダウンリストをそのように選択する。`base repository:YSWEngineer/ruby-practices` `base:main` ← `head repository:YSWEngineer/ruby-practices` `compare: fizzbuzz`
    3. このとき、**ブランチ間の差分も確認**すること。
    4. （確認したら）Create pull request をクリック、PR のタイトルを適切に設定して作成する。（動画では）fizzbuzzプログラムを作成、と記述。
    5. 下部にある Create pull request をクリックして、PR が完成。画面には **fizzbuzzプログラムを作成#1** が表示されていればOK。

![スクリーンショット 2024-08-02 15.09.30.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMkNrQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--0606865007b580e448562a3588babc7032f4e4b5/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-08-02%2015.09.30.png)

![スクリーンショット 2024-08-02 15.12.01.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMkdrQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--6bbd1a6e6338bebdb704b4b6ac3a0f63546daccf/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-08-02%2015.12.01.png)

![スクリーンショット 2024-08-02 15.14.07.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMktrQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--dfbe99f454b2b4c5b6c2df5153bdb6dc9934510f/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-08-02%2015.14.07.png)

![スクリーンショット 2024-08-02 15.14.51.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMk9rQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--dc496e48dfe90e0d96c0face1eefb77a6aca7954/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-08-02%2015.14.51.png)

13. そして、ここの URL を提出する。

![スクリーンショット 2024-08-02 15.14.51.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMlNrQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--a87a50762ff5cfafa323e97f64575847810ba964/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-08-02%2015.14.51.png)

14. Terminal での実行結果は、実際に Terminal で編集した FizzBuzzプログラムを実行して出力された内容をスクリーンショットで撮る。
```
yoshiwo@YSWs-MBP ruby-practices % ruby 01.fizzbuzz/fizzbuzz.rb 
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
16
17
Fizz
19
Buzz
```


## 📍 次回
### プラクティス『FizzBuzz問題(Ruby)』
- 完了したら他の方の提出物と自分の提出物を見比べる
### プラクティス『カレンダーのプログラム(Ruby)』
- 内容の把握、タスクばらし・段取りを組む


## ❤️‍🔥 感想
### 🤔 「何をどうするのか」を意識して
FizzBuzz 問題の提出物を提出。提出時に留意したことは「何をどうするのか」を意識することでした。時間は多少掛かったものの、途中で躓くことなく進めることができました。今回の作業は今後もよく行われる大事なことですので、作業の流れを Notion にまとめ、一つ一つの工程をスクリーンショットに収めました。あとは実践を積み重ねて慣れるしかありません。

メンターさんからのレビューを頂くまでの間は、次のプラクティスの内容の把握とタスクばらし・段取りを組むことに集中します。


## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 4 hours 33 min
- Total: 450 hours 43 min
