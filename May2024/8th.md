# 2023/05/08(水)
## 🕺 日頃からの意識
<details><summary>日頃からの意識</summary>

- 成長スピードを早めよう。
- 自分の考えや気持ちを簡潔に言語化したり、相手にわかりやすく伝える話し方ができるようになろう。
- 心と身体の状態を把握しながら行動しよう。
- 腕立て・スクワット・腹筋・ストレッチを継続しよう。
- 説明文をよく読もう。ここでの「読む」は内容を認識・把握すること。
- 体調の回復に努めて、行動の範囲を元に戻そう。
- Git & GitHub とお友達になろう。
- RubyKaigi 当日まで Ruby についてできる限り学ぶこと。
- 「何を、どうするのか」という意識を常に持ちながらプラクティスに臨むこと。
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
- プラクティス『Ruby 初級』
   - 書籍『ゼロからわかる Ruby 超入門』
      - CHAPTER 4

---


## 💡 本日の学び・気付き
<details><summary>書籍『ゼロからわかる Ruby 超入門』</summary>

## CHAPTER 4
### オブジェクトをまとめて扱う
- 配列：オブジェクトをまとめて扱う部品。数値や文字列と同じように、**配列自身もオブジェクト**である。
- 配列のクラスは**Array**（読み方は「アレイ」）。Array は配列という意味の英単語。
- 配列のことを**配列オブジェクト**、**Arrayオブジェクト**、あるいはそのまま**配列**と呼ぶ。
- 配列は`[`で始まり`]`で終わる。`[`と`]`の間にカンマ区切りで複数のオブジェクトを書くことができる。
- 配列の中身である個々のオブジェクトを**要素**と呼ぶ。例えば`["カフェラテ", "モカ", "コーヒー"]`は3つの要素 "カフェラテ" と "モカ" と "コーヒー" を持っている。
- 配列はさらに新しい要素を追加することもできるし、配列から要素を削除することもできる。
- 配列は種類の違うオブジェクトを1つの配列に入れることもできる。
```ruby
p ["カフェラテ", 400, 1.08] # 文字列オブジェクト、整数オブジェクト、小数オブジェクトが入った配列
p [300] # 要素が1つの配列
p [] # 要素が1つもないからの配列

```
- 配列を代入する変数名は複数名にすること。以下はその例。
```ruby
sugars = ["白砂糖", "黒糖", "角砂糖"]
coffee_beans = ["Brazil", "Kenya", "Nicaragua"]
even_numbers = [2, 4, 6] # even number：偶数
```
- `[ ]`は空の配列を意味している。
</details></details>


---


## 📍 次回
- プラクティス『Ruby初級』
   - 書籍『ゼロからわかる Ruby 超入門』
      - CHAPTER 4 続きから

---


## ❤️‍🔥 感想
### 💻🪫 MacBook Air を購入か？それともバッテリー交換か？
二週間ほど前からバッテリーの持ちが悪くなったので新しい Mac を購入するか、それともバッテリーの交換だけにするか？考えています。今使用しているもの（MacBook Pro 13-inch, intel, 2020）は愛着が湧いて「バッテリー以外で問題がなければこのまま使い続けたい」と思っています。RubyKaigi を終えるまでもう少し頑張っておくれ🥹

---


## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 0 hours 52 min
- Total: 315 hours 25 min
