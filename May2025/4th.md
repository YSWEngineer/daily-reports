# 2025/05/04(日)
## 📚 プラクティス『プログラムの修正（リバーシ編）』


## 🧩 タスクばらし
- [x] プラクティスの内容を咀嚼
- [x] タスクばらし、スモールステップの作成
- [ ] ソースコードの言語化
- [ ] ソースコードを修正
- [ ] 課題提出


## 🐾 スモールステップ
<details><summary>プラクティスの内容を咀嚼</summary>

- [x] プラクティスの内容を咀嚼
</details>

<details><summary>タスクばらし、スモールステップの作成</summary>

- [x] タスクばらし、スモールステップの作成
</details>

<details><summary>ソースコードの言語化</summary>

- [ ] ソースコードの言語化 **※①から順に行う**
  - [ ] ① reversi_methods_test.rb
  - [ ] ② reversi.rb
  - [ ] ③ reversi_methods.rb
  - [ ] ④ position.rb


</details>

<details><summary>ソースコードを修正</summary>

- [ ] ソースコードを修正
  - test_cannot_put_stone
    - [ ] 修正
  - test_finished_of_quickest_win_board
    - [ ] 修正
  - test_put_stone
    - [ ] 修正
  - test_turn
    - [ ] 修正
  - test_finished_of_full_board
    - [ ] 修正

</details>

<details><summary>課題提出</summary>

- [ ] 修正したソースコードを Pull Request としてアップ
- [ ] Pull Request としてアップした URL とテストコードの実行結果を提出
</details>


---


## 🧑🏻‍💻 本日の取り組み
### プラクティス『プログラムの修正（リバーシ編）』
- reversi_methods_test.rbファイルを言語化 途中まで


---


## 🎯 次回
### プラクティス『プログラムの修正（リバーシ編）』
- reversi_methods_test.rbファイルを言語化 途中から
    

---


## 💡 本日の学び・気付き
### reversi_methods_test.rbファイルを言語化
reversi_methods_test.rbファイル
```ruby
# frozen_string_literal: true # 文字列を凍結：このファイル内の文字列リテラルは書き換えができないようにする # リテラル：数値の123や、文字列の"Hello"など、ソースコードに直接埋め込むことができる値のこと
require 'minitest/autorun' # Minitestを読み込み：Ruby標準のテストフレームワークを使用可能にする
require_relative '../lib/reversi_methods' # lib/reversi_methods.rbに書かれているリバーシのコードを読み込む

class ReversiMethodsTest < Minitest::Test # クラスの作成：ReversiMehodsTestクラスを作成し、Minitestが使えるようにする
  include ReversiMethods # ReversiMethodsモジュールをReversiMethodsTestクラスにinclude（含める）する

  def build_board(board_text) # 引数board_textを受け取るbuild_boardメソッドを作成
    board = build_initial_board # build_initial_boardメソッドを呼び出して、その戻り値をローカル変数boardに代入する
    board_text.split("\n").each_with_index do |row, i| # board_textを行ごとに分けた文字列を要素に持つ配列を作り、その配列から1要素ずつ取り出してrowには取り出した要素を、iにはその要素が何番目かを、順番に代入する
      row.each_char.with_index do |cell, j| # rowを、一文字ずつ取り出して、その文字をcellに、その文字のインデックスをjに代入する
        board[i][j] = cell # cell（1つのマス）に入る文字を盤面の[i][j]に代入する
      end # ブロックの終わり
    end # ブロックの終わり
    board # build_boardメソッドは、文字列で表された盤面データ（board_text）を受け取り、それを二次元配列の盤面に変換したもの（board）を最後に返している。returnは省略されている。
  end # build_boardメソッド作成終了
```
- `split`メソッド：引数で渡した区切り文字で文字列を配列に分割するメソッド。
- `each_with_index`メソッド：ブロックパラメータに添え字を渡してくれる。具体的には「配列の中身を1つずつ取り出しながら、その取り出した順番（何番目か）も教えてくれるメソッド。
- `board_text.split(”\n”)`で「行ごとに分けた文字列」を要素に持つ配列を作る。
- `each_with_index do | row, i |`はその配列から1要素ずつ取り出して、
    - `row`に「取り出した要素」を、
    - `i`に「その要素が何番目か」を、
        
        順番に代入してくれる、という仕組み。

    よって、「配列の中身（各要素）とその順番をそれぞれ受け取る」というイメージになる。
    
- `each_char`メソッド：文字列を1文字ずつループ処理する。たとえば、`”abc”`なら、`[”a”, “b”, “c”]`を順に取り出すイメージ。
- `with_index`メソッド：`each`メソッド、`map`メソッド、`delete_if`メソッドなど繰り返し処理を行うメソッドと組み合わせて使用する。
    - 今回は、`each_char`メソッドの繰り返しに「何文字目か」の番号をセットで渡してくれる。
    - インデックスは`0`始まりなので、最初の文字は`j = 0`、次は`j = 1`、……
- 今回、`board`は盤面を示す二次元配列。
- `[i][j]`
    - `[i]`（行を選ぶ）
        - `i` は「何行目か」を示す番号（0から数えて）。
    - そのあとに続く `[j]`（列を選ぶ）        
- `= cell`
    - 右側の `cell`（たとえば `'-'`、`'W'`、`'B'` といった文字）を、`[i]`や`[j]`に代入する。        
    - `cell`はここでは盤面の「1マス分」の中身を表している。具体的には、`row.each_char.with_index do |cell, j|`の中で、
        - `row`が`"---WB---"`のような1行分の文字列
        - `.each_char`によって、その文字列を1文字ずつに分けると
            - `"-"`, `"-"`, `"-"`, `"W"`, `"B"`, `"-"`, `"-"`, `"-"`
        - その一文字一文字が`cell`という名前の変数に順番に入ってくる。
        
        つまり、`cell`は
        
        - `"-"` （空のマスを表す記号）
        - `"W"` （白石を表す記号）
        - `"B"` （黒石を表す記号）
        
        のいずれかが入っていて、`board[i][j] = cell`によって盤面配列のそのマスに代入される。
- `return`：メソッドや関数の中で処理した結果を呼び出し元に返すための命令。Ruby では`return`を使わない書き方が主流。


---


## ✍🏻 感想
### ⚪️⚫️ チェリー本を片手に
1行ずつコードを言語化しながら読み進めています。わからないところが出てきたら、その都度『チェリー本』を開いて確認。地味な作業かもしれませんが、コツコツ続けていこうと思います。

言語化の作業に入るまでに、あれこれ考えて時間をかけてしまうのはよくないなと感じつつも、準備したり、考えを巡らせたりする時間が、実は結構好きだったりします😊


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 4 hours 34 min
- Total: 1092 hours 18 min
