# 2023/05/07(火)
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
      - CHAPTER 2
      - CHAPTER 3

---


## 💡 本日の学び・気付き
<details><summary>書籍『ゼロからわかる Ruby 超入門』</summary>

## CHAPTER 2
### コメント
- プログラム中に空行を入れることができるが、実行する時に空行は無視される。主にプログラムを読みやすくするための区切りとして使用する。
- `#`は行の途中にも書くことができ、その後ろがコメントになる。
- `=begin`から`=end`で囲むと、その範囲はコメントとして扱われる。が、実際のところあまり使用されない。
```ruby
puts 1
=begin
puts 2
puts 3
puts 4
=end
puts5
```

### 対話的に実行する
- `irb（Interactive Ruby）`はターミナルで使用する。ターミナルで`irb`と入力すると出てきた画面で Ruby のプログラムを実行することができる。
```shell
# irbを始める
yoshiwo@YSWs-MBP rubybook % irb
irb(main):001>

# irbを終了させる時はexitを入力
irb(main):002> exit
yoshiwo@YSWs-MBP rubybook %
```
- **注意**`irb`の世界では Ruby の言語、`ターミナル`の世界では shell の言語が通じている。それぞれが違う世界で違う言語を使用するため、ターミナルで Ruby の言語を打つとエラーになる。逆もまた然り。

### プログラムの途中で一時停止してirbを使う
- `irb`にはプログラムの途中で一時停止して起動する方法もある。この方法を使うことで、変数の内容を確認したり、書き換えたりすることができる。この方法はデバッグ（バグを修正する）時に役に立つ。
```ruby
a = 1
# binding.irbを入力するとプログラムが一時停止し、irbが起動する
binding.irb
puts a
```

### プログラムの間違いを見つけて直す
- `p`メソッドは`puts`と同じだが、デバッグ専用として使用され、プログラムの作成には使用されない。

### エラーメッセージを読み解く
- エラーメッセージを読む作業はとても大事で、エラーメッセージからヒントを得ることは日頃の業務において多く行われている。
```
hi.rb:1:in `<main>': undefined method `put' for main (NoMethodError)

put "hi"
^^^
Did you mean?  puts
               putc
```
- エラーメッセージの解説
   - `hi.rb`：エラーを起こしているファイル名。
   - `1`：エラーが起きている行数。
   - `undefined method `put' for main (NoMethodError)`：エラーメッセージの本文。「putメソッドを実行しようとしたが、定義（用意）されていない」。
   - `NoMethodError`：エラーの種類。`NoMethodError`はメソッドがない時に発生するエラー。
   - `Did you mean? puts putc`：`Did you mean?`は日本語で「もしかして？」という意味で「`puts`または`putc`ではないですか？」と提案している。

### いろいろなエラーメッセージを体験する
#### 変数の名前を間違えた
```
xy.rb:2:in `<main>': undefined local variable or method `y' for main (NameError)

p y
  ^
```
- `undefined local variable or method `y' for main`：y という変数かメソッドが定義されていない
- `NameError`：（そのような名前はありませんという意味の）エラーの種類。

#### 0で割り算した
- 0で割り算するとエラーが発生する。
```
0div.rb:1:in `/': divided by 0 (ZeroDivisionError)
	from 0div.rb:1:in `<main>'
```
- `divided by 0`：0で割り算をした。
` `ZeroDivisionError`：0除算エラー。

#### 実行するファイル名が違う
```
ruby: No such file or directory -- ab.rb (LoadError)
```
- `ruby: No such file or directory -- ab.rb (LoadError)`：ab.rbというようなファイルまたはディレクトリはない。
- `LoadError`：読み込みができないという内容のエラー。

## CHAPTER 3
### 条件を判断する
- 等しくない時に **true** を返す`!=`がある。算数での≠に相当する。
- `==`や`!=`は、数値オブジェクトだけでなく、文字列オブジェクトを比較することもできる。
- even?メソッド：偶数かどうかを判断して true か false を返す。
- 末尾に「?」が付くメソッドは true か false を返すことが多い。
- 等しいかどうかの判断は`==`、変数への代入は`=`。

### 条件を満たしたときに処理をする
- 行頭にスペースを入れて一段下げることを「インデントを下げる」と言い、その時の段を「インデント」呼ぶ。インデントは半角スペース2つ分が主流。
- 条件を満たしたときの処理は、インデントを下げて書く。
- インデントはプログラムを書く上で作り手自身やプログラムを読む読み手に分かりやすくするために必要なもの。
- 後置if（if修飾子）：if から end まで複数行で書いたプログラムを一行で書くことができる。end を書く必要がなく、プログラムを短く読みやすく書くことができる。
- `if`の条件が満たされない2つのケース
   - 1つは`false`のとき。もう1つは`nil`のとき。`nil`は「何もない」ことを表すオブジェクト。
- `unless`：条件を満たさないときに処理を実行する。if と同じように後置で書くことができる。

### 条件を満たさないときにも処理する
- `elsif`：else のときに別の条件を続けて書くことができる部品。実際はそんなに使用することはない。読み方は「エルシフ」。
- 読みやすいプログラムは、読み心地の良い物語のようにするすると意味が頭に入っていく。プログラムはコンピューターのためだけでなく、人間のためでもある。

### 複数の条件を組み合わせる
- `||`：「または」「オア」と呼ぶ。「または」で複数の条件を書くときの文法に使用される。「a または b」は`a || b`と書く。どちらか一方でも満たせば条件を満たす。
- `&&`：「かつ」「アンド」と呼ぶ。複数の条件を満たされたときの文法に使用される。「a かつ b」は`a && b`と書く。両方を満たせば条件を満たす。

### 複数の道から1つを選んで分岐する
- case：「変数の値に応じて、複数の道から1つを選んで分岐する」処理。
- 二択のときは`if`、三択以上のときは`case`から、と考えると良い。

### なんども繰り返す
```ruby
3.times do
  puts "カフェラテ"
end
```
- `do`から`end`までのプログラムのかたまりを**ブロック**と言う。
- 重複を避けてプログラムを書く習慣を**DRY（Don't Repeat Yourselfの頭文字）**と言う。DRY なプログラムを心掛けることで、読みやすく、メンテナンスしやすいプログラムになる。
```ruby
3.times {
  puts "カフェラテ"
}
```
- end と do の代わりに`{`と`}`を使うことができる。
- 慣習的にブロックを複数行で書くときは`do`と`end`を使い、一行で書くときは`{`と`}`を使うことが多い。
</details>

---


## 📍 次回
- プラクティス『Ruby初級』
   - 書籍『ゼロからわかる Ruby 超入門』
      - CHAPTER 4 から

---


## ❤️‍🔥 感想
### 🔰🧑🏻‍💻 一言一句聴き逃がさず、手を動かす
五十嵐さんの動画内で仰っている「**とっても大事なこと**」を聴き逃さないようにしながら、エディターでプログラムを書いてターミナルで挙動を確認しています。

本（テキスト）の読み方にもありましたが全てを100％理解しようとはせず「そういえば、ここはこんなことがあったな」ぐらいにしてどんどん先に進んでいきたいと考えています。

---


## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 5 hours 29 min
- Total: 314 hours 33 min
