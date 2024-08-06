# 2024/08/06(火)
## 🧩 タスクばらし
### プラクティス『カレンダーのプログラム(Ruby)』の修了
- [x] 各参考ページを確認
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
- [x] [プログラミング初心者は変数名やメソッド名を略さない方がいいよ、という話 - give IT a try](https://blog.jnito.com/entry/2020/10/20/092724)
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
   - [プログラミング初心者は変数名やメソッド名を略さない方がいいよ、という話 - give IT a try](https://blog.jnito.com/entry/2020/10/20/092724)

---


## 💡 本日の学び・気付き

### プラクティス『カレンダーのプログラム（Ruby）』

#### プログラミング初心者は変数名やメソッド名を略さない方がいいよ、という話 - give IT a try
- プログラミング初心者は経験が浅いため変数名やメソッド名を略すとなると「一般的かどうか」「誤解が発生しないかどうか」といった判断ができない。そのため、**命名した本人と読み手の間に誤解が発生**してしまう。
- プログラミング初心者は変数名やメソッド名を略すのは、先輩プログラマからOKをもらった時だけにすること。
- 長い名前を入力するのが大変だと感じる人は、たとえば、Vim であれば`Ctrl-N`やCtrl-P`でバッファ内に表示されている文字列を自動補完することができる。また、Visual Studio Code や RubyMine などの IDE でも、途中まで変数名をタイプすると変数やメソッドの候補を表示してくれる。
- `number`を`no`と略すのは、一般的な略称と言えるかもしれないが、問題が起きやすい名前でもある。
   - `yse/no`の`no`と混同しやすい。
   - 配列に格納する場合などに複数形を使おうとすると`nos`や`noes`になるが、複数形になると急に馴染みが薄くなる（`no`の複数形であることがパッと理解しずらい）。

##### 略していいケース
- 以下のような単語は他のコードでも省略形をよく見かけるので、省略して書く場合がある。
   - execute = exec
   - initialize = init
   - calculate = calc
   - character = char
   - arguments = args
- 寿命が短いローカル変数や仮引数に対しては以下のような名前を付ける場合がある。
   - average = avg
   - maximum / minimum = max / min
   - message = msg
   - exception = e または ex
   - event = e
- 単純なループの変数に対しては以下のような略称を付けることがある。
   - 文字列の場合 = s または str（stringの略）
   - 文字の場合 = c（characterの略）
   - 数値の場合 = i（integerの略）または n（numberの略）
   - ファイルオブジェクトの場合 = f （fileの略）
```ruby
# ループの変数名をiとする場合のコード例
[1, 2, 3].map do |i|
  i * 10
end
```
- 寿命が極めて短い変数に対してはクラス名の頭文字を使う場合がある。
```ruby
# Userクラスのインスタンスを配列に格納
users = User.all

# ブロック内の変数の寿命が極めて短いので、名前をuとする
users.map { |u| u.name.upcase }
```
- だが、寿命がそれなり長い場合は略さずに書く。
```ruby
# 寿命がそれなりに長いので略さずにuserとする
users.map do |user|
  books = find_books(user)
  cars = find_cars(user)
  "#{user.name} has #{books.size} books and #{cars.size} cars"
end
```
- 母音を引っこ抜いたようなオレオレルールな略称はわかりづらくなるだけなので、絶対に使わない。
```ruby
# こんな略称は絶対書かない
gbsn_gtrs = Guitar.brand('gibson')
fndr_gtrs = Guitar.brand('fender')

# 変数名は略さずに書きます
gibson_guitars = Guitar.brand('gibson')
fender_guitars = Guitar.brand('fender')
```

##### 無味無臭な名前も避ける
- ダメな部類に入る変数名。
   - `data`
   - `info`
   - `item`
   - `element`
   - `obj`
   - `array (ary, arr)`
   - `list`
- 中身が想像できる名前を付けるようにすること。

---


## 📍 次回
### プラクティス『カレンダーのプログラム（Ruby）』
- カレンダーのプログラムに取り組む

---


## ❤️‍🔥 感想
### 📖✍🏻 次はカレンダーのプログラムに取り組む
インプット学習で触れた知識はまだ定着していませんが、課題に取り組みます。「分からない → 調べる → ちょっと分かる → 分からない → 調べる......」の繰り返しで少しずつ進めていくのだろうと推量しています。諦めず、間を空けず、続けることを意識しながら励んで参ります。

---


## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp; 1 hours 31 min
- Total: 458 hours 05 min
