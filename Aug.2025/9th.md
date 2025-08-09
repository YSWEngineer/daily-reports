# 2025/08/09(土)
## 📚 プラクティス『lsコマンドを作る1』

<details><summary>🎯 学習の狙い</summary>

- 標準出力について学ぶ
- 標準ライブラリの使い方を学ぶ
- Enumeratorには、each以外に便利なメソッドがあることを学ぶ
- RailsじゃないRubyプログラミングを学ぶ
- メソッド分割を学ぶ
- わかりやすい変数名メソッド名を学ぶ
- 大きな問題を分割する力を学ぶ
</details>


<details><summary>📌 要件</summary>

- [ ] オプション（`-a`や`-r`など）を付けず、且つ引数（フォルダのパス）も指定せずに実行する
- [ ] そのまま実行すると、今いるフォルダ（カレントディレクトリ）の中身を表示する
- [ ] `gem`は使わずに Ruby の標準ライブラリだけで作ること
- [ ] 完成したコードは GitHub の Pull Request として提出すること
- [ ] `rubocop-fjord`でデバッグを実行し、全てパスさせること
- [ ] 2つ以上のメソッドを自分で定義すること
- [ ] 表示は横に最大3列になるようにレイアウトすること
  - 3, 6, 9, 12のように3の倍数の件数だけでなく、最後の列に空欄ができるケースの結果も載せる
  - 「3列から5列に仕様変更してください」または「3列から100列に変えてください」とあとから言われても必要最小限の変更で対応できるようなロジックにしておくこと

</details>

<details open><summary>📚 参考資料</summary>

<details><summary>参考</summary>

  - [x] [lsコマンドを作る](https://bootcamp.fjord.jp/pages/380)
</details>
 

<details><summary>学習の狙い</summary>

  - [x] [【lsコマンド】大きな問題を小さく分解してから取り組む](https://bootcamp.fjord.jp/pages/279)
</details>

<details open><summary>ヒント</summary>

  - [x] [lsコマンドの使い方と覚えたい15のオプション【Linuxコマンド集】](https://eng-entrance.com/linux_command_ls)
  - [x] [library optparse (Ruby 2.6.0)](https://docs.ruby-lang.org/ja/latest/library/optparse.html)
  - [ ] [コマンドライン引数によるオプションに対応する (optparse) | まくまくRubyノート](https://maku77.github.io/ruby/io/optparse.html)
  - [ ] [コマンドライン引数・オプションの処理](https://bootcamp.fjord.jp/pages/251)
  - [ ] [binding.irb](https://docs.ruby-lang.org/ja/latest/method/Kernel/m/binding.html)
  - [ ] [Fileクラス](https://docs.ruby-lang.org/ja/latest/class/File.html)
  - [ ] [lsコマンドで表示されるファイルのモード(drwxr-xr-x) 〜RubyのFile::Stat#modeとは〜](https://zenn.dev/universato/articles/20201202-z-mode)
</details>

<details><summary>良いプログラムを書くための方法</summary>

  - [ ] [プログラミング初心者は変数名やメソッド名を略さない方がいいよ、という話 - give IT a try](https://blog.jnito.com/entry/2020/10/20/092724)
  - [ ] [\[RubyTips\] ハッシュテーブルによる分岐数削減](https://docs.komagata.org/5691)
  - [ ] [プログラムを書くときの考え方](https://bootcamp.fjord.jp/pages/147)
  - [ ] [rubyでコマンドを作る](https://bootcamp.fjord.jp/pages/250)
  - [ ] [RubyTips - komagataのブログ](https://docs.komagata.org/tags/rubytips/)
  - [ ] [Rubyスクリプトにもmainメソッドを定義するといいかも、という話 - Qiita](https://qiita.com/jnchito/items/4b4cae54170cc2f4377e)
  - [ ] [初心者がRailsプロジェクトへの初PRする前に見るチェックリスト - komagataのブログ](https://docs.komagata.org/5676)
  - [ ] [プログラミングでよく使う英単語のまとめ【随時更新】 - Qiita](https://qiita.com/Ted-HM/items/7dde25dcffae4cdc7923)
  - [ ] [代表的なデータ構造](https://bootcamp.fjord.jp/pages/148)
  - [ ] [配列の二人三脚を避ける](https://bootcamp.fjord.jp/pages/388)
  - [ ] [参考：lsコマンドの列幅が人によって異なるのはなぜ？ | FBC
](https://bootcamp.fjord.jp/questions/707)
</details>

 <details><summary>終了条件の確認</summary>

- [x] [終了条件 - lsコマンドを作る](https://bootcamp.fjord.jp/pages/ls-command#requirements)
</details>
</details>


---


### 🧑🏻‍💻 本日の取り組み
#### プラクティス『lsコマンドを作る1』🛠️💻
- [lsコマンドの使い方と覚えたい15のオプション【Linuxコマンド集】](https://eng-entrance.com/linux_command_ls)
- [library optparse (Ruby 2.6.0)](https://docs.ruby-lang.org/ja/latest/library/optparse.html)
- [コマンドライン引数によるオプションに対応する (optparse) | まくまくRubyノート](https://maku77.github.io/ruby/io/optparse.html)

---


### ⏭️ 次回
#### プラクティス『lsコマンドを作る1』🛠️💻
- [コマンドライン引数によるオプションに対応する (optparse) | まくまくRubyノート](https://maku77.github.io/ruby/io/optparse.html)


---


### 💡 本日の学び・気付き
#### コマンドライン引数によるオプションに対応する (optparse) | まくまくRubyノート
##### OptionParse の基本
- `OptionParser`クラスを使用すると`-a`や`--add`といったコマンドラインオプションを簡単に扱うことができる。
- `optionParser`で**ハンドルすべきオプション**は、`on`メソッドで設定する。
```ruby
on(short, long, desc = "") {|v| ... }
on(short, desc = "") {|v| ... }
on(long, desc = "") {|v| ... }
```
- `short`はショートオプションを表し、`-a`や`-d`のように指定する。
- `long`はロングオプションを表し、`--add`や`--delete`のように指定する。
- `desc`はオプションの説明文で、`--help`オプションを指定して実行した場合に表示される説明文を設定する。そして、後ろのブロックには、**オプションが指定された場合に実行されるコード**を記述する。
- オプションについて`on`メソッドによる定義を完了したら、`parse(ARGV)`を実行すれば、指定したオプションに一致したブロックが実行されていく。

##### 「ハンドルすべきオプション」とは？
- ざっくり言うと**プログラムが「受け取って処理しなければならない」コマンドライン引数**のこと。もっと噛み砕くと、プログラムに渡されるオプションを**見つけて取り出し、期待通りに動かすこと**を指す。つまり「（オプションを）受け取って処理する」こと。

↑いつものように言語化してまとめたのですが、もし間違えていましたらご指摘いただけると助かります。

##### 簡単なサンプル
`OptionParser`を使用して、`-a (--add)`オプションと、`-d (--delete)`オプションをハンドル（受け取って適切に扱う（処理する））する。
```ruby
require 'optparse' 

opt = OptionParser.new
opt.on('-a', '--add', 'add an item') { puts 'Added' }
opt.on('-d', '--del', 'delete an item') { puts 'Deleted' }
opt.parse(ARGV)
```
**一行ずつ言語化**
- `require 'optparse'`：optparseライブラリを読み込む（コマンドラインのオプションを扱うための標準ライブラリ）
- `opt = OptionParser.new`：`OptionParser`のインスタンスを作る（オプション定義を登録する「入れ物」のようなもの）
- `opt.on('-a', '--add', 'add an item') { puts 'Added' }`：`-a`や`--add`オプションが指定されたら、ブロック（`{ }`）の中身を実行する。ブロックの中では`'Added'`を出力する。
- `opt.on('-d', '--del', 'delete an item') { puts 'Deleted' }`：`-d`や`--del`オプションが指定されたら、ブロック（`{ }`）の中身を実行する。ブロックの中では`Deleted`を出力する。
- `opt.parse(ARGV)`：ARGV（コマンドライン引数）を解析して、登録したオプションがあればそれに対応したブロックを実行する。

**add an item / delete an item**
`'add an item'`や`'delete an item'`はオブションの説明文。「このオプションは何をするのか」を伝えるためのメタ情報。実際の動作には影響しない。
- `add an item`
  - 「アイテムを追加」
- `delete an item`
  - 「アイテムを削除」

下記はオプションを指定してプログラムを実行したときの実行例。
```shell
~/opt % ruby sample.rb -a
Added

~/opt % ruby sample.rb -d
Deleted

~/opt % ruby sample.rb -a -d
Added
Deleted
```

`optionParser`を使用すると、デフォルトで`-h`（`--help`）オプションが定義され、`on`メソッドの`desc`オプションで指定した説明文が表示される。
```shell
~/opt % ruby sample.rb --help
Usage: sample [options]
    -a, --add                        add an item
    -d, --del                        delete an item
```


---


### ✍🏻 感想
#### 🥹🙌🏻 プラクティス修了
『プログラムの修正（リバーシ編）』を無事修了しました。時間がかかりましたが、その分しっかり学びを得られました。取り組んでいる間はプライベートもわちゃわちゃして心身ともに疲れていたので、喜びもひとしおです！

#### 🫂 久し振りだね'optparse'
optparseと再会するのはカレンダー問題のプラクティス以来です。当時を思い出しながら参考資料を読み進めました......が、今日は朝からこの日報を書く直前まで、家人の仕事の関係者が出入りしており、落ち着いて学習する時間は取れませんでした。

気持ちを切り替えて、次頑張ります！


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2 hours 42 min
- Total: 1227 hours 34 min
