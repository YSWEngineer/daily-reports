# 2024/08/05(月)
## 🧩 タスクばらし
### プラクティス『カレンダーのプログラム(Ruby)』の修了
- [ ] 各参考ページを確認
- [ ] カレンダーのプログラムに取り組む
- [ ] 課題提出前の確認
- [ ] 課題提出
- [ ] 完了したら他の方の提出物と自分の提出物を見比べる

---


## 📋 段取り
<details><summary>各参考ページを確認</summary>

- [x] [class Enumerator](https://docs.ruby-lang.org/ja/latest/class/Enumerator.html)
- [x] [library optparse](https://docs.ruby-lang.org/ja/latest/library/optparse.html)
- [x] [class Date](https://docs.ruby-lang.org/ja/latest/class/Date.html)
- [x] [rubyでコマンドを作る](https://bootcamp.fjord.jp/articles/40)
- [x] [コマンドライン引数・オプションの処理](https://bootcamp.fjord.jp/pages/251)
- [x] [プログラミングでよく使う英単語のまとめ【随時更新】 - Qiita](https://qiita.com/Ted-HM/items/7dde25dcffae4cdc7923)
- [ ] [プログラミング初心者は変数名やメソッド名を略さない方がいいよ、という話 - give IT a try](https://blog.jnito.com/entry/2020/10/20/092724)
</details>


<details><summary>カレンダーのプログラムに取り組む</summary>

- [ ] カレンダーのプログラムを書く

**※ 分からない箇所が出てきたときは、以下のヒントを適宜参考にすること**
- [library optparse](https://docs.ruby-lang.org/ja/latest/library/optparse.html)
- [Date class](https://docs.ruby-lang.org/ja/latest/class/Date.html)
- [カレンダー課題のQ&A](https://bootcamp.fjord.jp/questions/tags/%E3%82%AB%E3%83%AC%E3%83%B3%E3%83%80%E3%83%BC?all=true)
- [【新人プログラマ応援】開発タスクをアサインされたらどういう手順で進めるべきか - Qiita](https://qiita.com/jnchito/items/017487cd882091494298)
- [セルフマネジメントの必須スキル「タスクばらし」そのポイント | Social Change!](https://kuranuki.sonicgarden.jp/archives/21981)
- [プログラミング初心者歓迎！「エラーが出ました。どうすればいいですか？」から卒業するための基本と極意（解説動画付き）](https://qiita.com/jnchito/items/056325421b7e36f02335)
- [🤔 わからないことをメンターや他の受講生に質問をする方法](https://bootcamp.fjord.jp/pages/use_the_question_room) 
</details>


<details><summary>課題提出前の確認</summary>

- [ ] [RubyTips - komagataのブログ](https://docs.komagata.org/tags/rubytips/)
- [ ] [初心者がRailsプロジェクトへの初PRする前に見るチェックリスト - komagataのブログ](https://docs.komagata.org/5676)
- [ ] [GitHubでコードを提出するときに気をつけること](https://bootcamp.fjord.jp/pages/info-for-github)
- [ ] [プログラミング初心者はgit commitする前に必ずdiffを自分でレビューするクセを付けよう](https://bootcamp.fjord.jp/pages/322)
- [ ] [プルリクエスト形式で提出物を出す際の「これはやっちゃダメ」リスト](https://bootcamp.fjord.jp/pages/317)
</details>


<details><summary>課題提出</summary>

- [ ] Pull Request としてアップする
- [ ] URL と Terminal での実行結果を提出
</details>


<details><summary>完了したら他の方の提出物と自分の提出物を見比べる</summary>

- [ ] 他の方の提出物と自分の提出物を見比べる
</details>

---


## ✍🏻 本日の取り組み
### プラクティス『カレンダーのプログラム(Ruby)』
- 各参考ページを確認
   - [コマンドライン引数・オプションの処理](https://bootcamp.fjord.jp/pages/251)
   - [プログラミングでよく使う英単語のまとめ【随時更新】 - Qiita](https://qiita.com/Ted-HM/items/7dde25dcffae4cdc7923)

---


## 💡 本日の学び・気付き
### プラクティス『カレンダーのプログラム（Ruby）』
#### コマンドライン引数・オプションの処理
##### 引数とオプションについて詳しく
- 引数：コマンドに渡す文字列。コマンドの後にスペースを一個入れて文字を打ち込む。
```
% echo hello
```
- 実は引数は複数渡すことができる。スペースで区切って3つ引数を渡してみる。すると、実際には echoコマンドに3つの引数を渡しているだけだということがわかる。
   - `echo`コマンド：コンピューターの画面に文字や変数の内容を表示するためのコマンド。
```
% echo hello my friend
hello my friend
```
- 引数をどう処理してくれるのかはコマンドによって違う。echo は引数をスペースで繋げて表示する。

##### オプションとは
- `ls`はファイルやディレクトリのパスを渡すことでその一覧を見ることができる。
```
% ls /bin
```
- `-a`とパスの両方を渡すこともできる。
```
% ls -a /bin
```
- 引数の中で特に`-`（ハイフン）から始まっているものをオプションという。引数やオプションにはこうあるべきというガイドラインはあるが、必ずそれに従わないといけないわけではない。

##### オプションのガイドライン
- `-`（ハイフン）のあとアルファベット一文字がオプション。オプションは複数指定できる。
```
% command -a -b -c foo
```
オプションに文字を渡すことができるものがある（ファイルを指定する -fオプションがあった場合）。
```
% command -f /tmp/foo
```
- `--`（ハイフン2つ）から始まる同じ機能を持つオプションがある場合がある。
   - ハイフン1つのものをショートネームオプション（short name option）、ハイフン2つのものをロングネームオプション（long name option）と呼ぶ。
```
% command --name
```
- ロングネームオプションに文字を渡すことができるものがある。ロングネームオプションに文字を渡す場合`=`（イコール）を付ける。下記の2行は同じ動作をする。
```
% command -f /tmp/foo
% command --file=/tmp/foo
```
- ショートネームオプションとロングネームオプションは混在させることができる。
```
% command -a --file=/tmp/foo bar
```
- `-h`もしくは`-help`でそのコマンドの使い方が表示される。
   - Usage：「利用法」という意味。
```
% command --help
  Usage: command [options] [arguments]
    -a    append mode
    -f    target file
```
- `-v`もしくは`-version`でそのコマンドのバージョン番号が表示される。
```
% command --version
command 1.2.3
```
- `ls`や`cd`、`echo`などは歴史の古いコマンドなのであまりこのガイドラインに従っていない。新しいコマンドを見つけた時はとりあえず`-h`か`-help`で使い方を調べること。

##### マニュアルで使い方を知る
- `-h`などで表示されるヘルプは簡易的なものなので、もっと詳しく知りたい場合は`man`コマンドを使うこと。`man`は manual の略でそのままの意味。コマンド名を渡すと、そのコマンドのマニュアルが存在する場合はマニュアルを表示する。

##### マニュアルを読め
- コンピューターコミュニティには古くから自分で調べる努力をせず簡単に人に聞く人に対して、RTFM(READ THE F**ING MANUAL!) 「マニュアル読め××野郎！」という厳しい言葉がある。それくらいマニュアルを読むことは日常的に当たり前のこと。マニュアルを読む癖を身に付けよう。

##### ruby でコマンドライン引数の処理の仕方
- ruby で何かやりたいことがある場合は組み込みライブラリ・標準添付ライブラリに使えるものがないか探す。これらは便利な宝の山なのでどういうものがあるのか一通り目を通してどんなものがあるのか頭に入れておくこと。
   - [library _builtin (Ruby 2.6.0 リファレンスマニュアル)](https://docs.ruby-lang.org/ja/2.6.0/library/_builtin.html)
   - [ライブラリ一覧 (Ruby 2.6.0 リファレンスマニュアル)](https://docs.ruby-lang.org/ja/2.6.0/library/index.html)
- コマンドライン引数を扱うライブラリが標準添付ライブラリにあるのでそれを使う。
   - [library optparse (Ruby 2.6.0 リファレンスマニュアル)](https://docs.ruby-lang.org/ja/2.6.0/library/optparse.html)

##### 引数の処理
```ruby
#!/usr/bin/env ruby

puts ARGV[0]
```
```
% ./arg.rb foo
foo
```
- `optparse`を使わなくても引数は定数`ARGV`から取れる。

##### ショートネームオプションの処理
```ruby
#!/usr/bin/env ruby
require 'optparse'

options = ARGV.getopts('a')
puts options
```
```
% ./arg.rb -a 
{"a"=>true}
```
- `ARGV.getopts`で取れる。
   - [OptionParser::Arguable#getopts (Ruby 2.6.0 リファレンスマニュアル)
](https://docs.ruby-lang.org/ja/2.6.0/method/OptionParser=3a=3aArguable/i/getopts.html) 

##### 引数付きショートネームオプションの処理
```ruby
#!/usr/bin/env ruby
require 'optparse'

options = ARGV.getopts('a:')
puts options
```
```
% ./arg.rb -a 111
{"a"=>"111"}
```

##### ロングネームオプションの処理
```ruby
#!/usr/bin/env ruby
require 'optparse'

options = ARGV.getopts('', 'foo')
puts options
```
```
% ./arg.rb --foo
{"foo"=>true}
```

##### 引数付きロングネームオプションの処理
```ruby
#!/usr/bin/env ruby
require 'optparse'

options = ARGV.getopts('', 'foo:')
puts options
```
```
% ./arg.rb --foo 222
{"foo"=>"222"}
```

##### 色々オプションの処理
```ruby
#!/usr/bin/env ruby
require 'optparse'

options = ARGV.getopts('ab:', 'bar', 'buz:')
puts options
```
```
% ./arg.rb -a -b 1 --bar --buz 333
{"a"=>true, "b"=>"1", "bar"=>true, "buz"=>"333"}
```

---


## 📍 次回
### プラクティス『カレンダーのプログラム（Ruby）』
- 各参考ページを確認
   - [プログラミング初心者は変数名やメソッド名を略さない方がいいよ、という話 - give IT a try](https://blog.jnito.com/entry/2020/10/20/092724)

---


## ❤️‍🔥 感想
### 📖✍🏻 とにかく前へ
読んでいてあまりの難しさに「むむむっ🤔」となるのですが、あまり気にせず先に進むようにしています。次回も一歩前へ。

### 🏁🏃🏻‍♂️ 一日も早く......
今のアルバイト先で一月前くらいから複数人に無視をされています。何が理由で無視をされるようになったのかは分かりませんが、できるだけ冷静に感情的にならず「柳に風」の姿勢でいつもどおりに業務に集中しています。今までどの職場でも悪口を言われたり、嫌がらせを受けたりしていたので慣れてはいるのですが、やはりそのような人たちと一緒にいるとしんどいです。

プライベートでは介護をしているので、それ以外ではできるだけ「しんどいなぁ」とか「辛いなぁ」と感じるようなこと（業務が忙しくて大変なのは大丈夫）は避けたいので、他のアルバイトを探そうかな？とも考えたのですが、新しいアルバイト先で絶対に嫌がらせを受けないという保証はありません。

とにかくたくさん勉強して一日も早く FBC の卒業と就職をすることが「今感じている辛さから解放される近道」だと思っていますので、このまま頑張ります。

普段は愚痴をこぼすようなことは決してしないのですが、心に中にある「もやつき」を初めて日報で吐露してしまいました。この文章をご覧になって嫌な気持ちにさせてしまいましたらすみません🙏🏻

**本当は FBC のメンター・卒業生・受講生の皆さんのような素敵な方々と一緒に働きたいのが本音です。**

---


## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 2 hours 04 min
- Total: 456 hours 34 min
