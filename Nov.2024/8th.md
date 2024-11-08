# 2024/11/08(金)

## 🧩 タスクばらし
### プラクティス『rubygems の基本を理解する』の修了
- [ ] 各参考ページを確認
- [x] `gem`コマンドを使用して`debug.gem`をインストールし、FizzBuzz のプログラムで使ってみること
- [ ] デバッガとデバッグを使い分けられるプログラマになる

------------

## 🐾 スモールステップ
<details><summary>各参考ページを確認</summary>

- [x] [RubyGems Guides](https://guides.rubygems.org/)
- [x] [ライブラリ（ruby-lang.org）](https://www.ruby-lang.org/ja/libraries/)
- [x] [Rubyist Magazine - シリーズパッケージマネジメント【第1回】RubyGems（1）](https://magazine.rubyist.net/articles/0006/0006-PackageManagement.html)
- [x] [RubyGems Wikipedia](https://ja.wikipedia.org/wiki/RubyGems)
- [ ] [Docs：debug.gemの使い方を学ぶ](https://bootcamp.fjord.jp/pages/how-to-use-debug-gem)
   - [x] [rubygems (debug.gem)の使い方 - YouTube](https://www.youtube.com/watch?v=4r7-uN3RvNA)
   - [ ] [byebugの良さを教えてください！ | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/questions/1162)
   - [ ] [Ruby 3.1 の debug.gem を自慢したい - クックパッド開発者ブログ](https://techlife.cookpad.com/entry/2021/12/27/202133)
   - [ ] [VS Codeでターミナルからの入力を伴うRubyプログラムをデバッグ実行する方法 - Qiita](https://qiita.com/jnchito/items/3254118d666ef1ea2923)
   - [ ] [Railsをステップ実行する方法を学ぶ（VS CodeとRubyMine） | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/pages/how-to-debug-rails)
- [ ] [デバッグ？デバッガ？debug.gem?あなたが言いたいのはどれ？？|FJORD BOOT CAMP](https://bootcamp.fjord.jp/articles/75)

</details>


<details><summary>gemコマンドを使用して debug.gem をインストールし、FizzBuzz のプログラムで使ってみること</summary>

- [x] 1. debug.gem のインストール
- [x] 2. FizzBuzzプログラムに debug を使用する

</details>


<details><summary>デバッガとデバッグを使い分けられるプログラマになる</summary>

- [ ] [Docs：debug.gemの使い方を学ぶ](https://bootcamp.fjord.jp/pages/how-to-use-debug-gem)の内容を咀嚼し、用語を使い分けられるようになること

</details>

------------

## 🧑🏻‍💻 本日の取り組み
### Advent Calendar
- 記事の草稿作成

### カレンダーのプログラム（Ruby）
- 消失したファイルをもう一度作成

------------

## 💡 本日の学び・気付き
### Advent Calendar
##### 記事の決まりごと
1. 簡潔に記すこと
   - 可能な限り無駄を削ぎ落とし、必要なことだけを伝える。
   - 必要なことだけを伝えるため、意図は可能な限り少なくする。もしくは無くす。
   - 読み手が退屈しないようにテンポ良く読み進められるかがポイント。
   - 短く伝えることで読み手に伝えたいことを印象に残させる。

2. カテゴリーを意識すること
   - 細分化しすぎず、大見出し・小見出しだけで構成すること。細かいことをたくさん付けてわちゃわちゃさせない。

### カレンダープログラム（Ruby）
#### ファイルが消失したことを確認 〜 ファイルを作り直す までの流れ
```shell
# カレンダープログラムcalendar.rbファイルがあるか確認
02.calendar % ls -l
total 0
02.calendar % cd ..
ruby-practices % cd 02.calendar/calendar.rb
cd: no such file or directory: 02.calendar/calendar.rb

# .gitディレクトリが存在しないため、Gitコマンドが適用できない状況
ruby-practices % git branch
fatal: not a git repository (or any of the parent directories): .git

# fooディレクトリを作成
/tmp % mv ruby-practices/ foo

# tmpディレクトリの中身を確認
yoshiwo@YSWs-MBP /tmp % ls   
com.apple.launchd.VRTbgn9EJs	com.brave.Browser.Sparkle.pid	msu-target-PDAYUYuX
com.apple.launchd.cm7oP4RCEO	foo

# ruby-practicesリポジトリをクローン
/tmp % git clone https://github.com/YSWEngineer/ruby-practices.git
Cloning into 'ruby-practices'...
remote: Enumerating objects: 57, done.
remote: Total 57 (delta 0), reused 0 (delta 0), pack-reused 57 (from 1)
Receiving objects: 100% (57/57), 14.54 KiB | 1.45 MiB/s, done.
Resolving deltas: 100% (23/23), done.

# tmpディレクトリの中身を確認
/tmp % ls
com.apple.launchd.VRTbgn9EJs	com.brave.Browser.Sparkle.pid	msu-target-PDAYUYuX
com.apple.launchd.cm7oP4RCEO	foo				ruby-practices

# ディレクトリの移動と現在のブランチを確認
yoshiwo@YSWs-MBP /tmp % cd ruby-practices 
yoshiwo@YSWs-MBP ruby-practices % git branch
* main

# リモートリポジトリ（GitHub）から更新された内容を取得
ruby-practices % git fetch

# calendarブランチの作成と移動
yoshiwo@YSWs-MBP ruby-practices % git checkout -b calendar origin/calendar 
Branch 'calendar' set up to track remote branch 'calendar' from 'origin'.
Switched to a new branch 'calendar'

# 現在のブランチを確認
yoshiwo@YSWs-MBP ruby-practices % git branch
* calendar
  main

# ディレクトリの中身を詳細表示
ruby-practices % ls -la
total 24
drwxr-xr-x  15 yoshiwo  wheel   480 11  8 15:21 .
drwxrwxrwt   8 root     wheel   256 11  8 15:21 ..
drwxr-xr-x  14 yoshiwo  wheel   448 11  8 15:26 .git
-rw-r--r--   1 yoshiwo  wheel  2090 11  8 15:21 .gitignore
-rw-r--r--   1 yoshiwo  wheel    57 11  8 15:21 .rubocop.yml
drwxr-xr-x   4 yoshiwo  wheel   128 11  8 15:21 01.fizzbuzz
drwxr-xr-x   4 yoshiwo  wheel   128 11  8 15:26 02.calendar
drwxr-xr-x   3 yoshiwo  wheel    96 11  8 15:21 03.bowling
drwxr-xr-x   3 yoshiwo  wheel    96 11  8 15:21 04.ls
drwxr-xr-x   3 yoshiwo  wheel    96 11  8 15:21 05.wc
drwxr-xr-x   3 yoshiwo  wheel    96 11  8 15:21 06.bowling_object
drwxr-xr-x   3 yoshiwo  wheel    96 11  8 15:21 07.ls_object
drwxr-xr-x   3 yoshiwo  wheel    96 11  8 15:21 98.rake
drwxr-xr-x   3 yoshiwo  wheel    96 11  8 15:21 99.wc_object
-rw-r--r--   1 yoshiwo  wheel  2648 11  8 15:21 README.md

# 02.calendarディレクトリに移動し、中身を確認
yoshiwo@YSWs-MBP ruby-practices % cd 02.calendar 
yoshiwo@YSWs-MBP 02.calendar % ls -la
total 8
drwxr-xr-x   4 yoshiwo  wheel  128 11  8 15:26 .
drwxr-xr-x  15 yoshiwo  wheel  480 11  8 15:21 ..
-rw-r--r--   1 yoshiwo  wheel    0 11  8 15:21 .gitkeep
-rw-r--r--   1 yoshiwo  wheel  532 11  8 15:26 calendar.rb

```

------------

## ⏭️ 次回
### カレンダーのプログラム（Ruby）
- 作成したファイルの「オーナー」「グループ」「その他のユーザ」に対して実行権限を付与
- もう一度 Pull Request で課題を提出
- メンターさんに再提出したことをお伝えする

### Advent Calendar
- 記事の草稿作成

### プラクティス『rubygems の基本を理解する』
- [Docs：debug.gemの使い方を学ぶ](https://bootcamp.fjord.jp/pages/how-to-use-debug-gem)
   - [byebugの良さを教えてください！ | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/questions/1162)
   - [Ruby 3.1 の debug.gem を自慢したい - クックパッド開発者ブログ](https://techlife.cookpad.com/entry/2021/12/27/202133)
   - [VS Codeでターミナルからの入力を伴うRubyプログラムをデバッグ実行する方法 - Qiita](https://qiita.com/jnchito/items/3254118d666ef1ea2923)
   - [Railsをステップ実行する方法を学ぶ（VS CodeとRubyMine） | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/pages/how-to-debug-rails)

------------

## ✍🏻 感想
### 🫥 ファイルが消失
メンターさんから頂きましたアドバイスを基にGitコマンドや GitHub の仕組みついて復習し、昨日から見当たらないファイルを探していたのですが見つけることができず、丁度、雑談部屋にいらしていた :@tadaaki: tadaさんにお訊きし、**Pull Request 後に何かしらの原因でファイルが消失してしまった**ことがわかりました。これはイレギュラーなケースのようで「自己解決では難しく、時間がかかってしまう」と仰っていました。

### 🫶🏻 「恩送り」という素敵な考え方
##### 恩送りとは？
自分が受けた恩を恩をくれた人ではなく、別の人に渡すことです。バトンを繋いでいくようなイメージで受けた恩を次の人に送ることで、善意を循環させるというものです。「Yoshiwoさんが転職して後輩ができたら、その後輩さんに私がしたことをしてあげてね!!」と教えてくださいました。:@tadaaki: tadaさん、いつもありがとうございます。またいろんなことを学ばせてください😊🙏🏻

------------

## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 6 hours 45 min
- Total: 625 hours 28 min
