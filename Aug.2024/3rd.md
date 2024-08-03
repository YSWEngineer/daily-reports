# 2024/08/03(土)
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
- [ ] [コマンドライン引数・オプションの処理](https://bootcamp.fjord.jp/pages/251)
- [ ] [プログラミングでよく使う英単語のまとめ【随時更新】 - Qiita](https://qiita.com/Ted-HM/items/7dde25dcffae4cdc7923)
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
- 内容の把握
- タスクばらし・段取りの組み立て
- 各参考ページを確認
   - [class Enumerator](https://docs.ruby-lang.org/ja/latest/class/Enumerator.html)
   - [library optparse](https://docs.ruby-lang.org/ja/latest/library/optparse.html)
   - [class Date](https://docs.ruby-lang.org/ja/latest/class/Date.html)
   - [rubyでコマンドを作る](https://bootcamp.fjord.jp/articles/40)

---


## 💡 本日の学び・気付き
### プラクティス『カレンダーのプログラム（Ruby）』
- 内容の把握
- タスクばらし・段取りの組み立て

#### class Enumerator
- Enumerable：たくさんのものを順番に一つずつ取り出して何かをするための道具。例えば、おもちゃの箱の中から一つずつおもちゃを取り出して遊ぶような感じ。`Enumerable`を使うと、配列やハッシュに対していろいろと便利なことができる。
- ラッパークラス：何かを包んで特別な機能を追加するクラス。例えばおもちゃを包むプレゼントの箱のようなもの。
- 外部イテレータ：コレクション（例えば、配列）の中の要素を一つずつ取り出すための道具。
- モジュール：プログラムの中で使用する便利な道具が入った「道具箱」のようなもの。モジュールを使用すると、同じ道具をいろいろな場所で使用することができるようになる。モジュールを使うには、クラスにそのモジュールを「インクルード」する。インクルードすることで、そのクラスはモジュールの中の道具を使えるようになる。
- インクルード：クラスにモジュールを追加して、その道具を使えるようにすること。
- クラス：設計図のようなもの。
- インスタンス：設計図から作られた具体的なオブジェクト。
- インスタンスメソッド：クラスから作られたインスタンスが使用できるメソッド。
##### Enumeratorクラスの基本
- `Enumerator`クラスは、配列やハッシュなどのコレクションを一つずつ取り出して操作するための道具。これを使うと、繰り返し処理を柔軟に行うことができる。
- `Enumerator.new`あるいは`Object#to_enum`や`Object#enum_for`を使って`Enumerator`オブジェクトを作成できる。

#### library optparse
- `optparse`は Ruby でコマンドラインのオプションを取り扱うためのライブラリ。
##### optparseの基本
1. `OptionParse`オブジェクト`opt`を生成する。
2. オプションを取り扱うブロックを`opt`に登録する。
3. `opt.parse(ARGV)`でコマンドラインを実際に`prase`する。

#### class Date
- `Date`クラスは、日付を扱うためのクラス。例えば、今日の日付や特定の日付を簡単に操作することができる。`Date`クラスを使うためには、プログラムの最初に`require 'date'`と書き、`Date`クラスを読み込ませる。

---


## 📍 次回
### プラクティス『カレンダーのプログラム（Ruby）』
- 各参考ページを確認
   - [コマンドライン引数・オプションの処理](https://bootcamp.fjord.jp/pages/251)

---


## ❤️‍🔥 感想
### 📖✍🏻 先ずは慣れよう
Ruby のリファレンスマニュアルを読むのに難儀しています。自分の言葉に言い換えて理解しようとしているのですが、情報量の多さとまだ意味を知らない用語の羅列に終始頭の中はちんぷんかんぷんでした。[『Rubyの公式リファレンスが読めるようになる本』](https://zenn.dev/jnchito/books/how-to-read-ruby-reference)を片手に先ずはリファレンスに慣れることを目標とします。

今は「私にカレンダーのプログラムが書けるのかな🤔」という不安と「また新しい知識を学べる😊」という好奇心が綯い交ぜになっています。不安を解消するためには勉強するしかないので、前に進むだけです......頑張れ自分。

---


## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 3 hours 47 min
- Total: 454 hours 30 min
