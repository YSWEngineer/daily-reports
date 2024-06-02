# 2024/06/01(日)
## 🕺 日頃からの意識
<details><summary>日頃からの意識</summary>

- 成長スピードを早めよう。
- 自分の考えや気持ちを簡潔に言語化したり、相手にわかりやすく伝える話し方ができるようになろう。
- 心と身体の状態を把握しながら行動しよう。
- 腕立て・スクワット・腹筋・ストレッチを継続しよう。
- 説明文をよく読もう。ここでの「読む」は内容を認識・把握すること。
- 体調の回復に努めて、行動の範囲を元に戻そう。
- Git & GitHub とお友達になろう。
- 「何を、どうするのか」という意識を常に持ちながらプラクティスに臨むこと。
- **Rubykaigi から得られた刺激や経験を学習に活かすこと ←New✨**

</details>

---


## 📝 プラクティス『Ruby 初級』の段取り
<details><summary>段取り</summary>

- [x] 各参考ページを確認
   - [x] [ホワイの(感動的)Rubyガイド](http://www.aoky.net/articles/why_poignant_guide_to_ruby/chapter-1.html)
   - [x] [TryRuby](https://try.ruby-lang.org/)
   - [x] [ゼロからわかるRuby超入門の読み方](https://bootcamp.fjord.jp/pages/289)
   - [x] [学習を加速させるインデックス読書術](https://qiita.com/dkatsura/items/3364b293ed1451a66a8a)
   - [x] [Ruby の公式リファレンスが読めるようになる本](https://zenn.dev/jnchito/books/how-to-read-ruby-reference)
   - [x] [オブジェクト指向スクリプト言語 Ruby リファレンスマニュアル](https://docs.ruby-lang.org/ja/latest/doc/index.html)
   - [x] [【新人プログラマ応援】公式ドキュメントも読もう - Qiita](https://qiita.com/chooyan_eng/items/cd0d3174b77ff1e02c3f)
- [x] 動画講座
   - [x] [ゼロからわかるRuby超入門動画講座](https://bootcamp.fjord.jp/pages/374)
- [ ] 課題取り組み
   - [ ] ゼロからわかる Ruby 超入門の各章の練習問題
   - [ ] [TryRuby](https://try.ruby-lang.org/)
</details>

---


## 🗓️ 今週の ToDo
<details><summary>今週の ToDo</summary>

- [x] ~~各参考ページを確認~~
   - [x] ~~[ホワイの(感動的)Rubyガイド](http://www.aoky.net/articles/why_poignant_guide_to_ruby/chapter-1.html)~~
   - [x] ~~[TryRuby](https://try.ruby-lang.org/)~~
   - [x] ~~[ゼロからわかるRuby超入門の読み方](https://bootcamp.fjord.jp/pages/289)~~
   - [x] ~~[学習を加速させるインデックス読書術](https://qiita.com/dkatsura/items/3364b293ed1451a66a8a)~~
   - [x] ~~[Ruby の公式リファレンスが読めるようになる本](https://zenn.dev/jnchito/books/how-to-read-ruby-reference)~~
   - [x] ~~[オブジェクト指向スクリプト言語 Ruby リファレンスマニュアル](https://docs.ruby-lang.org/ja/latest/doc/index.html)~~
   - [x] ~~[【新人プログラマ応援】公式ドキュメントも読もう - Qiita](https://qiita.com/chooyan_eng/items/cd0d3174b77ff1e02c3f)~~
- [x] 動画講座
   - [x] [ゼロからわかるRuby超入門動画講座](https://bootcamp.fjord.jp/pages/374)
- [ ] 課題取り組み
   - [ ] ゼロからわかる Ruby 超入門の各章の練習問題
   - [ ] [TryRuby](https://try.ruby-lang.org/)
</details>

---


## ✍🏻 本日の取り組み
- Urawa.rb に初参加 & 地域rbデビュー
- プラクティス『Ruby 初級』
   - 書籍『ゼロからわかる Ruby 超入門』
      - CHAPTER 6

---


## 💡 本日の学び・気付き
<details><summary>書籍『ゼロからわかる Ruby 超入門』</summary>

## CHAPTER 6
### ハッシュ（Hash）とは
- ハッシュは複数のオブジェクトをまとめることができる入れ物。
- ハッシュは「キー」と「値」のセットで複数のデータを扱うことができる。
- 辞書に例えると、辞書の「見出し語」がハッシュでは「キー」、辞書の「書かれた意味」がハッシュでは「値」になる。
- ハッシュは`{`で始まり`}`で終わる。
- ハッシュのクラス名は`Hash`。
- ハッシュのことを、`ハッシュオブジェクト`、または`Hashオブジェクト`、`ハッシュ`と呼ぶ。

### シンボル（Symbol）とは
- シンボルでは文字列は、コロン記号（`:`）から始める。
- シンボルのクラス名は`Symbol`。
- シンボルは文字列と相互に変換することができる。
   - 文字列からシンボルへは`to_sym`メソッドを使い、シンボルから文字列へは`to_s`メソッドを使う。

### ハッシュには2つの書き方がある
```ruby
# 今までの書き方
{:coffee => 300, :caffe_latte => 400}
# 新しい書き方
{coffee: 300, caffe_latte: 400}
```

### 変数に代入してハッシュに名前をつける
- 変数への代入は、ほかのオブジェクトの時と同じく、ハッシュオブジェクトに名札をつけるイメージ。

### ハッシュから値を取得する
- 値の取得は`ハッシュ[キー]`という書き方をする。
- 配列は「n番目を取得」したり、「全要素を取得」して使うことが多いのに対し、ハッシュは「キーの値を取得」という使い方が多い。

### ハッシュへキーと値の組を追加する
- ハッシュへのキーと値の追加は`ハッシュ[キー] = 値`

### ハッシュは同じキーを複数持てない
- ハッシュは同じキーを複数持てない

### 存在しないキーを指定したとき
- ハッシュから存在しないキーを取得すると、`nil`を得る。

### ハッシュからキーと値の組を削除する
- ハッシュからの削除は`ハッシュ .delete（キー）`

### ハッシュを繰り返し処理する
- eachメソッドとブロックを使うとハッシュの全要素を繰り返し処理できる。
- キーと値がそれぞれ変数に代入されて、繰り返し処理が実行される。


</details>

---


## 📍 次回
- プラクティス『Ruby初級』
   - 書籍『ゼロからわかる Ruby 超入門』
      - CHAPTER 7

---


## ❤️‍🔥 感想
### 🕊️💎 Urawa.rb 初参加 & 地域rbデビュー
:@suzukahori: さんとほりゆうさん主催の Urawa.rb に参加しました。穏やかな雰囲気の中、自己紹介、もくもく、勉強の進捗報告、ボードゲーム、懇親会（お食事会）が行われました。ご参加された皆さんからたくさんの刺激を得られ、「私も皆さんに負けずに頑張っていこう」と学習へのモチベーションが湧き上がりました。どうもありがとうございました☺️✨

### ハッシュって......
ハッシュはデータを整理して扱うことができる道具なのかな......と考えました。ハッシュも次に学ぶ「メソッド」もプログラミングを学ぶ上で大事な概念だと思いますので、引き続き解説動画からインプットをしっかり行います。

---


## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 2 hours 30 min
- Total: 372 hours 56 min
