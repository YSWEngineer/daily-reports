# 2024/06/07(金)
## 🕺 日頃からの意識
<details><summary>日頃からの意識</summary>

- 成長スピードを早めよう。
- 自分の考えや気持ちを簡潔に言語化したり、相手にわかりやすく伝える話し方ができるようになろう。
- 心と身体の状態を把握しながら行動しよう。
- 腕立て・スクワット・腹筋・ストレッチを継続しよう。
- 説明文をよく読もう。ここでの「読む」は内容を認識・把握すること。
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
- プラクティス『Ruby初級』
   - 書籍『ゼロからわかる Ruby 超入門』
      - CHAPTER 6 （復習）
      - CHAPTER 7

---


## 💡 本日の学び・気付き
<details><summary>CHAPTER 6（復習）</summary>

### 「破壊的変更」と「破壊的メソッド」
それぞれプログラムのルールを大きく変える変更や、オブジェクト自体を変更するメソッドのことを指す。
#### 破壊的変更
- **プログラムの動作を変える**ような大きな変更のことを指す。

#### 破壊的メソッド
- **オブジェクト自体を変更する**メソッドのことを指す。
- メソッド名の最後に`!`（ビックリマーク、エクスクラメーション）がついているメソッドが多い。

### keysメソッドでコードを短く
ハッシュには`keys`メソッドという全てのキーを配列で取得するメソッドが用意されている。これを使うとコードを短く、且つ、直感的に書くことができる。
```ruby
menu = {"コーヒー" => 300, "カフェラテ" => 400}
keys = []
menu.each do |key, value|
  keys.push(key)
end
p keys #=> ["コーヒー", "カフェラテ"]

# 上記のコードをkeysメソッドで全てのキーを配列で取得することが可能
menu = {"コーヒー" => 300, "カフェラテ" => 400}
p menu.keys #=> ["コーヒー", "カフェラテ"]
```

</details>

<details><summary>CHAPTER 7</summary>

### メソッドとは
- メソッドはプログラムが大きくなってきた時に意味のあるまとまりで分けるための道具。
- メソッドは名前をつけた「処理の部品」で、これまで勉強してきた`puts`, `p`, `each`, `uniq`, `sum`...... などは Ruby があらかじめ用意しているメソッドである。

### メソッドを定義する
- 実は自分でもメソッドを作れる仕組みが用意されている。
- メソッドを作ることを「**メソッドを定義する**」と言う。
- メソッドを定義するには`def`に続いてメソッド名を書く。
- メソッドは定義しただけでは実行されず、呼び出さなければならない。
- メソッドの名前には`英字`、`数字`、`_`などを使うことができる。ただ、数字から始めることはできない。慣習では、英字は全て小文字で書き、2単語以上を繋げるときは`_`を間に入れる（**スネークケース**）。

### メソッドを呼び出す
- メソッドを実行することを「**呼び出す**」と言う。
- 定義したメソッドは、メソッド名を書くことで呼び出す（実行する）ことができる。

### メソッドの戻り値
- 戻り値とは、関数やメソッドなどが終了したときに「返す」値のことを指す。
- 複数のオブジェクトを戻り値として返したい時は、配列へ入れて1つにまとめることができる。

### 引数を使ってオブジェクトを渡せるメソッドを定義する
- メソッド定義の`def`でメソッド名の後ろに続けて`(変数)`を書くと、メソッド呼び出しで引数としてオブジェクトを渡せるようになる。
- ↑この時の変数は、一般の変数と同じように自由に名付けることができる。
- 引数は**メソッドへオブジェクトを渡す**機能。
- 戻り値は**メソッドから呼び出し元へオブジェクトを返す**機能。

### 2つ以上の引数を持つメソッドを定義する
- 引数は3つ以上にすることもできる。
- 原則として、**引数の個数はメソッドの定義側と呼び出し元で同数にする**がある。

### メソッドを途中で終わらせる - return
- `return`を実行すると、その時点でメソッド処理を終わらせることができる。
- `return`は`if`や`unless`で条件分岐するために使われる。
- `return`した時に戻り値を指定したい時は、`return`の後ろに戻り値で戻したいオブジェクトを書いてあげること。
- メソッドの`()`は省略可能
   - 呼び出し側の`()`の省略はよく行われるが、定義の時は省略はあまりされない。

### 引数を省略したときのデフォルト値
- メソッドの引数には、デフォルト値を指定することができる。
- デフォルト値とは、引数を省略してメソッドが呼び出された時に使われる値。
- デフォルト値を指定するには、メソッド定義で`引数 = デフォルト値`と書く。

### 引数の順番を変えられるキーワード引数
- メソッド定義で引数名の後ろに`:`を付けるとキーワード引数になる。
```ruby
def メソッド名(引数1: , 引数2: , ...)
   処理
end
```
- キーワード引数を使ったメソッドを呼び出すときは......
```ruby
メソッド名(引数1: オブジェクト1, 引数2: オブジェクト2, ...)
```

### キーワード引数でのデフォルト値
- 引数にデフォルト値を設定すると、メソッドの呼び出し時に引数を省略することができる。
- キーワード引数を使うと......
   - メソッドの呼び出し時に引数を名前付きで指定できる。
   - メソッドの呼び出し時に引数を書く順番を変えられる。

### ローカル変数とスコープ
- 変数にはスコープ（見える範囲と寿命）がある。
- ローカル変数は、定義したメソッドの中がスコープになり、メソッドの外では見えない。
- 同様に、メソッドの外で定義したローカル変数は、メソッドの中では見えない。
- 大きなプログラムを書いていくと「影響範囲を如何にして狭くできるか？」という意識や、**プログラムの中で使う道具の影響範囲を狭くできる道具**がとても大事になる。

</details>

---


## 📍 次回
- プラクティス『Ruby初級』
   - 書籍『ゼロからわかる Ruby 超入門』
      - CHAPTER 8

---


## ❤️‍🔥 感想
### 🧑🏻‍💻🧠 プログラミング的思考を身に付けたい
本日学んだ動画でもプログラミングで大事なことを随所で仰っていたので Notion にしっかりまとめましたが、それらを身に付けるには知識と経験が不可欠です......本当に地道にコツコツとですね（しみじみ🤔）。

---


## ⏰ 学習時間
- Today:&nbsp;&nbsp; 5 hours 55 min
- Total: 387 hours 16 min