# 2024/12/09(月)

## 📚 プラクティス『ボウリングのスコア計算プログラム』


### 🧩 タスクばらし
- [x] ボウリングのルールを知る
- [ ] 各参考ページを確認
- [ ] ボウリングのスコア計算プログラムを作成
- [ ] 課題提出


### 🐾 スモールステップ
<details><summary>ボウリングのルールを知る</summary>

- [x] ルール詳細を確認
</details>

<details><summary>各参考ページを確認</summary>

- [ ] [Docs: 「新ルール（カレントフレームシステム）」のボウリングのスコア計算プログラムの書き方](https://bootcamp.fjord.jp/pages/249)
- [ ] [Docs: ボウリングのルールとスコアの付け方](https://bootcamp.fjord.jp/pages/619)
- [ ] [プログラミングでよく使う英単語のまとめ【随時更新】 - Qiita](https://qiita.com/Ted-HM/items/7dde25dcffae4cdc7923)
</details>

<details><summary>ボウリングのスコア計算プログラムを作成</summary>

- [ ] ボウリングのスコア計算プログラムを作成
</details>

<details><summary>課題提出</summary>

- [ ] ボウリングのスコア計算プログラムに rubocop-fjord を通す
- [ ] ボウリングのスコア計算プログラムを Pull Request として提出
- [ ] 提出物作成・メンターさんへの提出
   - [ ] Pull Request の URL を貼り付ける
   - [ ] Terminal で実行した結果を**テキスト**で提出物本文に貼り付ける
   - [ ] 「プログラム実行の例」にある入力例全て実行結果をスクリーンショットで貼り付ける
   - [ ] rubocop-fjord のチェックが全てパスした内容をスクリーンショットで貼り付ける
</details>


------------


### 🧑🏻‍💻 本日の取り組み
#### プラクティス『プログラムの修正』
- 他のコードを見比べる
- Pull Requests の Conversation を確認

#### プラクティス『ボウリングのスコア計算プログラム』
- 各参考ページを確認
   - [Docs: 「新ルール（カレントフレームシステム）」のボウリングのスコア計算プログラムの書き方](https://bootcamp.fjord.jp/pages/249)


### 🎯 次回
#### プラクティス『ボウリングのスコア計算プログラム』
- 各参考ページを確認
   - [Docs: 「新ルール（カレントフレームシステム）」のボウリングのスコア計算プログラムの書き方](https://bootcamp.fjord.jp/pages/249)
   - [Docs: ボウリングのルールとスコアの付け方](https://bootcamp.fjord.jp/pages/619)
   - [プログラミングでよく使う英単語のまとめ【随時更新】 - Qiita](https://qiita.com/Ted-HM/items/7dde25dcffae4cdc7923)


------------


### 💡 本日の学び・気付き
### プラクティス『プログラムの修正』
#### コードを見比べる
- 「明らかにこっちの方がコードが良くなる」というケース以外では、**プログラムの修正は極力diffを小さくするのが正解**。
- 価格が文字列で定義されているのが妥当なのかどうか考えること。
- 変数名は具体化すること。

### プラクティス『ボウリングのスコア計算プログラム』
#### Docs: 「新ルール（カレントフレームシステム）」のボウリングのスコア計算プログラムの書き方
##### 1投毎に分割する
```ruby
#!/usr/bin/env ruby

score = ARGV[0]
p score.split(',')
```
```shell
% ./bowling.rb 6,3,9,0,0,3,8,2,7,3,X,9,1,8,0,X,6,4
["6", "3", "9", "0", "0", "3", "8", "2", "7", "3", "X", "9", "1", "8", "0", "X", "6", "4"]
```
`score = ARGV[0]`
- コマンドライン引数として渡された最初の値を取得し、それを`score`という変数に代入している。
- `ARGV`は、コマンドライン引数を格納する配列。例えば、スクリプト（命令やコードが書かれたファイル）を実行する際に`./bowling.rb 6,3,9,0,...`と引数を渡すと、`ARGV`にはその値（引数）が格納される。
- `ARGV[0]`は、配列`ARGV`の最初の要素を取得する。この場合、`ARGV[0]`には引数として渡された文字列`"6,3,9,0,...`が格納される。

`p score.split(',')`
- `score`変数に格納された文字列をカンマで分割し、その結果を配列として表示している。
- `split(',')`メソッドは、文字列をカンマ（`,`）で分割し、各部分を配列の要素として返す。
- 例えば、`score`が`"6,3,9,0,..."`という文字列の場合、`split`メソッドは`["6", "3", "9", "0", ...]`のような配列を返す。

##### 数字に変換
```ruby
#!/usr/bin/env ruby

score = ARGV[0]
scores = score.split(',')
shots = []
scores.each do |s|
  if s == 'X' # strike
    shots << 10
    shots << 0
  else
    shots << s.to_i
  end
end
p shots
```
```shell
% ./bowling.rb 6,3,9,0,0,3,8,2,7,3,X,9,1,8,0,X,6,4
[6, 3, 9, 0, 0, 3, 8, 2, 7, 3, 10, 0, 9, 1, 8, 0, 10, 0, 6, 4]
```
`scores = score.split(',')`
- `score`変数に格納された文字列をカンマで分割し、`scores`という配列に格納する。

`shots = []`
- `shots`という空の配列を作成し、ここにボウリングの各ショットの点集を格納する。

`scores.each do |s|`
- 各スコア`s`に対して処理を行う。

`if s == 'X'`
- スコアが'X'（ストライク）である場合。

`shots << 10`
- ストライクの10点を`shots`配列に追加する。

`shots << 0`
- ストライクの2投目に0点を追加する。

`<<`
- `<<`は、Rubyの配列や文字列に対して要素や文字を追加するために使われる演算子。このコードでは、`shots`という配列に対して`10`と`0`という要素を追加している。
- もし、`s`（スコア）がストライク（`X`）だった場合、`shots`の配列は以下のようになる。
```shell
[... , 10, 0, ...]
```

`else`
- それ以外の場合。

`shots << s.to_i`
- `s`（スコア）を整数に変換して`shots`配列に追加する。

##### scores や shots が複数形になっている理由
- `scores`は、間まで区切られたスコアのリストを表していて、複数のスコアが含まれているため複数形になっている。
- `shots`は、各投球の結果を格納するリストを表していて、複数の投球結果が含まれているため複数形になっている。
- 変数名を複数形にすることで、コードの読み手に対して、その変数が複数の要素を含む配列であることが分かりやすくなる。

##### フレーム毎に分割
```ruby
#!/usr/bin/env ruby

score = ARGV[0]
scores = score.split(',')
shots = []
scores.each do |s|
  if s == 'X'
    shots << 10
    shots << 0
  else
    shots << s.to_i
  end
end

frames = shots.each_slice(2).to_a
p frames
```
```shell
% ./bowling.rb 6,3,9,0,0,3,8,2,7,3,X,9,1,8,0,X,6,4
[[6, 3], [9, 0], [0, 3], [8, 2], [7, 3], [10, 0], [9, 1], [8, 0], [10, 0], [6, 4]]
```
`frames = shots.each_slice(2).to_a`
- `each_slice`メソッドは、配列を指定したサイズの小さな配列に分割するためのメソッド。このメソッドを使うと、元の配列を一定のサイズ毎に区切って新しい配列を作成できる。

1. 配列`shots`の内容
まず、`shots`という配列にはボウリングの各投球のスコアが格納されている。例えば、以下のような内容
```ruby
shots = [6, 3, 9, 0, 0, 3, 8, 2, 7, 3, 10, 0, 9, 1, 8, 0, 10, 0, 6, 4]
```
2. `each_slice(2)`の挙動
`shot.each_slice(2)`は、配列`shots`の要素を2つずつのグループに分割する。`each_slice`メソッドは Enumerator を返す。Enumeratorは、**配列の中の要素を一つずつ取り出して**使うことができる。具体的には、`each_slice(2)`は元の配列を2つの要素ごとに区切って、新しい小さな配列を作成する。その小さな配列が順に処理される。
```ruby
shots.each_slice(2)
```
次のような2つずつの小さな配列を作成する。
- [6, 3]
- [9, 0]
- [0, 3]
- [8, 2]
- [7, 3]
- [10, 0]
- [9, 1]
- [8, 0]
- [10, 0]
- [6, 4]

3. `.to_a`で一つの配列に格納
小さい配列達をを一つの配列の中に格納される。
```ruby
frames = shots.each_slice(2).to_a
```
これにより、`frames`は次のような配列になる。
```ruby
frames = [
  [6, 3],
  [9, 0],
  [0, 3],
  [8, 2],
  [7, 3],
  [10, 0],
  [9, 1],
  [8, 0],
  [10, 0],
  [6, 4]
]
```
まとめると、
- `each_slice(2)`：元の配列を2つずつに分割する。
- `to_a`：Enumerator で返すものを配列に変換する。

これにより、配列`shots`が2投毎のフレームに分割され、それらが配列`frame`に格納される。

##### 単純に合計する
```ruby
#!/usr/bin/env ruby

score = ARGV[0]
scores = score.split(',')
shots = []
scores.each do |s|
  if s == 'X'
    shots << 10
    shots << 0
  else
    shots << s.to_i
  end
end

frames = []
shots.each_slice(2) do |s|
  frames << s
end

point = 0
frames.each do |frame|
  point += frame.sum
end
puts point
```
```shell
% ./bowling.rb 6,3,9,0,0,3,8,2,7,3,X,9,1,8,0,X,6,4
89
```
`frames = []`
- `frames`という空の配列を作成し、そこに配列`shots`を2つずつ分割した小さい配列達を格納する。

`shots.each_slice(2) do |s|`
- 配列`shots`を2つずつに分割し、`s`スコアに対して処理を行う。

`frames << s`
- 分割された小さい配列を配列`frames`に格納する。
- 例えば、`shots`が`[6, 3, 9, 0, 0, 3, 8, 2, 7, 3, 10, 0, 9, 1, 8, 0, 10, 0, 6, 4]`の場合、`frames`は`[[6, 3], [9, 0], [0, 3], [8, 2], [7, 3], [10, 0], [9, 1], [8, 0], [10, 0], [6, 4]]`となる。

`point = 0`
- ※何故`point = 0`にするのか、分かりませんでした🤔

`frames.each do |frame|`
- 配列`frames`の各フレームに対して処理を行う。

`point += frame.sum`
- 各フレーム`frame`のスコアの合計を変数`point`に加算される。
- `sum`は Array（配列）の中身を全部足したものを得るメソッド。

##### frames と frame 
- `frames`は、配列全体を指し、複数のフレームを含むため複数形になる。
- `frame`は、その配列の中の各要素を指し、各フレームを順番に処理するために使われる。


------------


### ✍🏻 感想
#### 🧑🏻‍💻 一行ずつ言語化する
ボウリングのスコア計算プログラムを書けるようになるために、参考URLに載っているコードを一行ずつ解説しながら読み進めました。特に、各コードの意味や機能を詳しく理解するために、コマンドライン引数の取り扱い、配列の操作方法、Enumerator の仕組みについて学びました。

各行を丁寧に言語化することで、本当にちょっとずつですがコードの流れや構造が分かったような気がしました。次回もこの地道な作業を続け、ボウリングのスコア計算プログラムのさらに複雑な部分を理解できるように頑張ります。


------------


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 6 hours 46 min
- Total: 758 hours 54 min
