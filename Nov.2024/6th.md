# 2024/11/06(水)

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
### プラクティス『rubygems の基本を理解する』
- [Docs：debug.gemの使い方を学ぶ](https://bootcamp.fjord.jp/pages/how-to-use-debug-gem)
   - [rubygems (debug.gem)の使い方 - YouTube](https://www.youtube.com/watch?v=4r7-uN3RvNA)

------------

## 💡 本日の学び・気付き
### rubygems(debug.gem)の使い方
#### デバッガとは？
プログラムを一つずつステップ実行しながら、プログラムの内部状態を確認したり、問題を特定したりするための**Gem**（ライブラリ）。
例えば......
- **変数の中身を確認**：現在の変数の値が何であるかを確認。
- **ステップ実行**：プログラムを1行ずつ実行して、その過程で変数や条件を確認。

などができる。

#### debug.gem
- Ruby 3.1以降のバージョンでは、**debug.gem**をインストールしなくても使用できる。
- インストールしてみる
```shell
% gem install debug
Fetching debug-1.9.2.gem
Building native extensions. This could take a while...
Successfully installed debug-1.9.2
Parsing documentation for debug-1.9.2
Installing ri documentation for debug-1.9.2
Done installing documentation for debug after 1 seconds
1 gem installed

A new release of RubyGems is available: 3.5.9 → 3.5.23!
Run `gem update --system 3.5.23` to update your installation.
```
- インストールできたかどうか確認
```shell
% rdbg --version   
rdbg 1.9.2
```
- 上記のコマンド`rdbg`は`ruby debug`の略語で、**デバッグ(debug)Gemをインストールしたことによって使える**ようになる。

#### 以前書いたFizzBuzzコードを基に**デバッガ**を知る
- インストールした**debug.gem**を使えるようするため、ソースコードの中に`require 'debug'`と`binding.break`または`debugger`を書き込む。
```ruby
#!/usr/bin/env ruby
require 'debug'

(1..20).each do |number|
  binding.break
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
```shell
% ruby fizzbuzz.rb
[1, 10] in fizzbuzz.rb
     1| #!/usr/bin/env ruby
     2| require 'debug'
     3| 
     4| (1..20).each do |number|
=>   5|   binding.break
     6|   if number % 15 == 0
     7|     puts "FizzBuzz"
     8|   elsif number % 3 == 0
     9|     puts "Fizz"
    10|   elsif number % 5 == 0
=>#0	block {|number=1|} in <main> at fizzbuzz.rb:5
  #1	[C] Range#each at fizzbuzz.rb:4
  # and 1 frames (use `bt' command for all frames)
(rdbg) 
```
- `binding.break`：コードの実行を止めている。
- (rdbg)の隣に変数名（今回は`number`）を入力すると、今入っている変数の中身が出力される。
```shell
(中略)
(rdbg) number
1
```
- `step`を入力すると、**プログラムの処理を一つ先に進ませる**ことができる。
ちなみに、`s`だけでも入力が可能。
```shell
(rdbg) step    # command
[1, 10] in fizzbuzz.rb
     1| #!/usr/bin/env ruby
     2| require 'debug'
     3| 
     4| (1..20).each do |number|
     5|   binding.break
# 矢印の位置が変わった
=>   6|   if number % 15 == 0
     7|     puts "FizzBuzz"
     8|   elsif number % 3 == 0
     9|     puts "Fizz"
    10|   elsif number % 5 == 0
=>#0	block {|number=1|} in <main> at fizzbuzz.rb:6
  #1	[C] Range#each at fizzbuzz.rb:4
  # and 1 frames (use `bt' command for all frames)
```
- 何も入力していない状態で`return`キーを押すと、**直前のコマンドを繰り返し実行**してくれる。
- 終了したい時は`quit`または`q`を入力する。Yes/Noの選択肢が面倒なときは、`q!`ですぐに終わらせることもできる。
```shell
(rdbg) quit    # command
Really quit? [Y/n] n
(rdbg) q    # quit command
Really quit? [Y/n]
(ruby) q!
```
- 一気に進めたいときは`continue`または`c`を使う。
```shell
(中略)
(rdbg) continue
```
- **メソッドの実行を抜ける**：「今いるメソッドの処理を終えて、次の箇所で止まる」という意味。
- `finish`：**メソッドの呼び出しの最後まで行った状態**になる。`step`で一つずつ作業をステップするのが面倒なときに`finish`を使用すると良い。`fin`でも実行可能。
```shell
(中略)
(rdbg) finish    # command
2
[9, 18] in fizzbuzz.rb
     9|   elsif number % 5 == 0
    10|     puts "Buzz"
    11|   else
    12|     puts number
    13|   end
=>  14| end
    15| 
    16| (1..20).each do |number|
    17|   binding.break
    18|   fizzbuzz(number)
=>#0	Object#fizzbuzz(number=2) at fizzbuzz.rb:14 #=> nil
  #1	block {|number=2|} in <main> at fizzbuzz.rb:18
  # and 2 frames (use `bt' command for all frames)
```
- `next`：今回の例だとFizzBuzzの中には入らずに、FizzBuzzメソッドを実行してくれる。`n`でも可能。
- `help`：使えるコマンドを知りたいときは`help 知りたいコマンド`で仕様を調べることができる。
```shell
(rdbg) help list    # command

### Information

* `l[ist]`
  * Show current frame's source code.
  * Next `list` command shows the successor lines.
* `l[ist] -`
  * Show predecessor lines as opposed to the `list` command.
* `l[ist] <start>` or `l[ist] <start>-<end>`
  * Show current frame's source code from the line <start> to <end> if given.
```
- debug時に使用できるコマンドはたくさんあるが、動画内で紹介された以下のコマンドを押さえれば何とかなる!!!

   - `step`
   - `quit`
   - `q!`
   - `continue`
   - `finish`
   - `next`
   - `help`

- 変数名やメソッド名がコマンドと重複してしまった場合。例えば変数`number`を`n`にして、変数の中身を知りたくなった場合。`p n`と入力する。
```shell
% ruby fizzbuzz.rb
[12, 19] in fizzbuzz.rb
    12|     puts number
    13|   end
    14| end
    15| 
    16| (1..20).each do |n|
=>  17|   binding.break
    18|   fizzbuzz(n)
    19| end
=>#0	block {|n=1|} in <main> at fizzbuzz.rb:17
  #1	[C] Range#each at fizzbuzz.rb:16
  # and 1 frames (use `bt' command for all frames)
(rdbg) p n    # command
=> 1
```
- `(rdbg)`内で FizzBuzz を実行したり、変数の値を入力したり、変数の値を求めたり、変数に対して`to_s`を呼んだりすることもできる。
```shell
(ruby) fizzbuzz(15)
FizzBuzz
nil
(rdbg) p n % 15    # command
=> 1
(ruby) fizzbuzz(100)
Buzz
nil
(ruby) n.to_s
"1"
```

### VSCode上でもデバッガを使用できる
- VSCode の Extensions から**rdbg**というワードで検索して、**VSCode rdbg Ruby Debugger**をインストール。インストール後コードの行の左端に赤丸が表示されるのでクリックすると、**binding.breakの代わり**になる。実際に実行するときは、VSCode の**虫のアイコン**（Rub and Debug）をクリックして**Run and Debug**ボタンをクリック。**黄緑色の三角**をクリックするとdebugの対象となるファイルのパスが表示されるのでreturnキーを押す。

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeFM5QXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--a39e2bdabdbd0633943a4c6c5aee5c5901470705/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-11-06%2018.15.31.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeFM5QXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--a39e2bdabdbd0633943a4c6c5aee5c5901470705/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-11-06%2018.15.31.png" width="3584" height="1590" alt="スクリーンショット 2024-11-06 18.15.31.png"></a>

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeFc5QXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--f28499f16f017de2b869858f49ae1fef03d6f88a/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-11-06%2018.21.15.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeFc5QXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--f28499f16f017de2b869858f49ae1fef03d6f88a/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-11-06%2018.21.15.png" width="3584" height="1590" alt="スクリーンショット 2024-11-06 18.21.15.png"></a>


<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeGE5QXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--66b4a39dea596637cbc8596eaad5f712cc80dec7/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-11-06%2018.26.08.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeGE5QXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--66b4a39dea596637cbc8596eaad5f712cc80dec7/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-11-06%2018.26.08.png" width="1452" height="522" alt="スクリーンショット 2024-11-06 18.26.08.png"></a>


<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeGU5QXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--1eee4f8e90b7c8f6cccdbcd08053a51722796be9/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-11-06%2018.38.40.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeGU5QXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--1eee4f8e90b7c8f6cccdbcd08053a51722796be9/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-11-06%2018.38.40.png" width="2422" height="200" alt="スクリーンショット 2024-11-06 18.38.40.png"></a>

------------

## ⏭️ 次回
### プラクティス『rubygems の基本を理解する』
- [Docs：debug.gemの使い方を学ぶ](https://bootcamp.fjord.jp/pages/how-to-use-debug-gem)
   - [byebugの良さを教えてください！ | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/questions/1162)
   - [Ruby 3.1 の debug.gem を自慢したい - クックパッド開発者ブログ](https://techlife.cookpad.com/entry/2021/12/27/202133)
   - [VS Codeでターミナルからの入力を伴うRubyプログラムをデバッグ実行する方法 - Qiita](https://qiita.com/jnchito/items/3254118d666ef1ea2923)
   - [Railsをステップ実行する方法を学ぶ（VS CodeとRubyMine） | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/pages/how-to-debug-rails)

------------

## ✍🏻 感想
### 🛠️✨ デバッガはプログラミングにおいて非常に重要なツール
1. バグの発見
- プログラムが予期しない動作をする原因を特定するために使用されます。デバッガを使うことで、どの行でエラーが発生しているのか、なぜそのエラーが発生しているのかを詳細に調査できます。

2. 変数の確認
- プログラムの実行中に変数の値を確認できます。これにより、変数の値が期待どおりに変化しているかどうかを確認し、問題を見つける手助けをします。

3. ステップ実行
- プログラムを一行ずつ実行して、各ステップの挙動を詳細に観察できます。これにより、プログラムの流れや論理を理解しやすくなります。

以上のことから、デバッガはプログラムの品質を高めるために必須なツールですし、プログラマーにとってデバッガの使い方を理解し、効果的に活用することは非常に重要だと感じました。

↑開発の経験はまだありませんが、本日の学習で得たことから想像で語っています。もし認識が間違っていましたらご指摘ください🙏🏻😅

------------

## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 6 hours 14 min
- Total: 609 hours 24 min
