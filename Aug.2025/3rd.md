# 2025/08/03(日)
## 📚 プラクティス『プログラムの修正（リバーシ編）』


### 🧩 タスクばらし
- [x] プラクティスの内容を咀嚼
- [x] タスクばらし、スモールステップの作成
- [x] ソースコードの言語化
- [x] ソースコードを修正
- [ ] 課題提出


### 🐾 スモールステップ
<details><summary>プラクティスの内容を咀嚼</summary>

- [x] プラクティスの内容を咀嚼
</details>

<details><summary>タスクばらし、スモールステップの作成</summary>

- [x] タスクばらし、スモールステップの作成
</details>

<details><summary>ソースコードの言語化</summary>

- [x] ソースコードの言語化 **※①から順に行う**
  - [x] ① reversi_methods_test.rb
  - [x] ② reversi.rb
  - [x] ③ reversi_methods.rb
  - [x] ④ position.rb


</details>

<details><summary>ソースコードを修正</summary>

- [x] ソースコードを修正
  - test_cannot_put_stone
    - [x] 修正
  - test_finished_of_quickest_win_board
    - [x] 修正
  - test_put_stone
    - [x] 修正
  - test_turn
    - [x] 修正
  - test_finished_of_full_board
    - [x] 修正

</details>

<details><summary>課題提出</summary>

- [ ] 修正したソースコードを Pull Request としてアップ
- [ ] Pull Request としてアップした URL とテストコードの実行結果を提出
</details>


---
### 🧑🏻‍💻 本日の取り組み
#### プラクティス『プログラムの修正（リバーシ編）』
##### test_finished_of_quickest_win_board / test_finished_of_full_board
- バグの原因を探る
- 修正


---


### 🎯 次回
#### プラクティス『プログラムの修正（リバーシ編）』
- 修正したソースコードを Pull Request としてアップ
- Pull Request としてアップした URL とテストコードの実行結果を提出
    

---


### 💡 本日の学び・気付き
#### test_finished_of_quickest_win_board / test_finished_of_full_board
<details><summary>⚠️ ネタバレ注意</summary>

### finished?メソッド / placeable?メソッドが書かれているコードを丁寧に言語化
`finished?`メソッドが「リバーシの終了に関係する」と思い確認してみると`placeable?`メソッドが`finished?`メソッドの中に組み込まれていたので、それぞれのメソッドが該当するコードを言語化し、コードの意味や内容を正しく把握する。
```ruby
def finished?(board)
  !placeable?(board, WHITE_STONE) && !placeable?(board, BLACK_STONE)
end

def placeable?(board, attack_stone_color)
  board.each_with_index do |cols, row|
    cols.each_with_index do |cell, col|
      next unless cell == BLANK_CELL

      position = Position.new(row, col)
      return true if put_stone(board, position.to_cell_ref, attack_stone_color, dry_run: true)
    end
  end
end
```

#### finished?(board)の言語化
```ruby
def finished?(board)
```
- 「`board`を引数に持つ`finished?`メソッドを定義」。
  - `finished?`：`?`で終わるメソッドなので真偽値（`true`または`false`）を返す。

```ruby
!placeable?(board, WHITE_STONE) && !placeable?(board, BLACK_STONE)
```
- 「盤面上に白石を置く場所が**なく**、且つ盤面上に黒石を置く場所が**なければ**`ture`を返す」。
  - `!`：このときの`!`は、論理否定の演算子。以下、**チェリー本p.203を引用**
> `!A`と書いた場合、`A`が真であれば`false`を、そうでなければ`true`を返します。つまり、値が`true`または`false`のどちらかに変換されます。

  - `&&`：複数の条件を1つにまとめる論理演算子。`条件1 && 条件2`は「条件1 かつ 条件2」の意味で、**条件1も条件2も真であれば真**になる。

まとめると.....
```ruby
def finished?(board)
  !placeable?(board, WHITE_STONE) && !placeable?(board, BLACK_STONE)
end
```
- 「**盤面で、白石も黒石もどちらも置ける場所がなければ、リバーシの試合は終了する**」という意味になる。

#### placeable?(board, attack_stone_color)の言語化
```ruby
def placeable?(board, attack_stone_color)
```
- 「`board`, `attack_stone_color`を引数に持つ`placeable?`メソッドを定義」。
  - `attack_stone_color`：これからマスに置く石の色を表す（白石なら`WHITE_STONE`、黒石なら`BLACK_STONE`）。

```ruby
board.each_with_index do |cols, row|
```
- 「盤面（`board`）の配列を一行ずつ取り出しながら`cols`（行）と`row`（行番号）を同時に取得する」。
  - `each_with_index`メソッド：「要素（行）」と「インデックス（行番号）」を同時に取得するメソッド。**※ チェリー本：p.143**
  - `board`：このときの`board`は「行の配列」の集合を指す。
```shell
board = [
  [a1, b1, c1, …],  # これが“行0”
  [a2, b2, c2, …],  # これが“行1”
  …
]
```
  - `cols`：本来は「columns（列）のまとまり」を意味する略語だが、ここでは「**一行分の配列**」を受け取る変数。つまり、「行0」であれば`[a1, b1, c1, …]`が変数`cols`に入る。
  - `row`：`each_with_index`の「**インデックス**」なので、何番目の行なのかを表す番号（0, 1, 2...）が入る。

要するに、この一行で「**盤面から行を取り出し、同時にその行の行番号を取得する**」という動きをしている。

```ruby
cols.each_with_index do |cell, col|
```
- 「一行分の配列（cols）からcell（一つのマスの情報）とcol（列番号）を同時に取得する」。
  - `cell`：その行（`cols`）の中の「一つのマスの情報」（`BLANK_CELL`か`W`か`B`）を受け取る。`cell`は、ここでは「1マス」という意味。

**ここまで登場した変数のまとめ**
- `board`：行の配列が並んだ「盤面全体」
- `cols`：「一行分の配列」（本来は columns の略だが、ここでは「行」）
- `row`：その行が何行目かを示す「行番号」
- `cell`：「一マスの情報」
- `col`：そのマスが何列目かを示す「列番号」

```ruby
next unless cell == BLANK_CELL
```
- 「もし`cell`が空白のマス（`BLANK_CELL`）ではないのなら、今の繰り返し処理を終わりにして次に進む」。
  - `next`：繰り返し処理のその回をそこで終わりにして、次の回へ進む。
  - `unless`：条件式が偽の場合だけ処理を実行する。`if`と反対の動きをする。

```ruby
position = Position.new(row, col)
```
- 「`row`（行番号）と`col`（列番号）を持つインスタンスを作成し、変数`position`に紐付ける」。

```ruby
return true if put_stone(board, position.to_cell_ref, attack_stone_color, dry_run: true)
```
- 「もし、置こうとしているマス（`position.to_cell_ref）に石（`attack_stone_color）を置いてみてひっくり返しが行われるのなら（`put_stone(board, position.to_cell_ref, attack_stone_color, dry_run: true`）`true`を返して、`placeable?`メソッドを途中で終わらせる」。

**ここまで登場した引数のまとめ**
- `board`：現在の盤面を表す
- `position.to_cell_ref`：「置こうとしているマスの位置」
- `attack_stone_color`：「置こうとしている石」（黒石なら`BLACK_STONE`、白石なら`WHITE_STONE`）
- `dry_run: true`：「シミュレーション（ドライラン）をオン（`true`）にする」......？🤔

---

### デバッグを行う
メンターの岡嵜さんからいただきましたアドバイスを参考に
> ちなみに p を使って動作を把握されているようですが、 binding.irb や debug gemは使われていますか？
もし使われていないようでしたら、これらを使うことでより効率的に動作を把握できるかもしれません。

`binding.irb`を使ってバグの原因を突き止めてみる。

#### binding.irb の準備
そのままでは irb のライブラリが読み込まれないため、
- `require 'irb'`

または、**tabの補完**を使用したい場合は、
- `require 'irb/completion'`

をファイルの先頭に追加しておく必要がある。

##### 1. ファイルの先頭に irb を読み込むコードを追加
```ruby
# 以下のコードどちらかを追加する
require 'irb'
require 'irb/completion'  # tabの補完を使用したい場合
```

##### 2. デバッグしたい行に binding.irb を書く
```ruby
def finished?(board)
  binding.irb    # ここで irb が起動する
  !placeable?(board, WHITE_STONE) && !placeable?(board, BLACK_STONE)
end
```

##### 3. Rubyコマンドでテストを起動
```shell
% ruby reversi_methods_test.rb
```

これで`binding.irb`が実行され、その場で irb のプロンプトが表示される。
```shell
~/bug_reversi/test % ruby reversi_methods_test.rb
Run options: --seed 22402

# Running:

..
From: /Users/yoshiwo/bug_reversi/lib/reversi_methods.rb @ line 82 :

    77:       false
    78:     end
    79:   end
    80: 
    81:   def finished?(board)
 => 82:     binding.irb
    83:     !placeable?(board, WHITE_STONE) && !placeable?(board, BLACK_STONE)
    84:   end
    85: 
    86:   def placeable?(board, attack_stone_color)
    87:     board.each_with_index do |cols, row|

irb(#<ReversiMethodsTest:0x000000...):001>
```

#### binding.irb でデバッグ
##### 1.引数boardの中身を確認
```shell
irb(#<ReversiMethodsTest:0x000000...):001> p board
[["W", "W", "W", "W", "W", "W", "W", "W"], ["W", "B", "B", "W", "W", "B", "W", "B"], ["W", "B", "B", "B", "B", "W", "B", "B"], ["W", "B", "W", "B", "B", "B", "B", "B"], ["W", "B", "W", "W", "B", "B", "B", "B"], ["W", "B", "W", "W", "W", "B", "B", "B"], ["W", "W", "W", "W", "W", "W", "B", "B"], ["W", "B", "B", "B", "B", "B", "B", "B"]]
=> 
[["W", "W", "W", "W", "W", "W", "W", "W"],
 ["W", "B", "B", "W", "W", "B", "W", "B"],
 ["W", "B", "B", "B", "B", "W", "B", "B"],
 ["W", "B", "W", "B", "B", "B", "B", "B"],
 ["W", "B", "W", "W", "B", "B", "B", "B"],
 ["W", "B", "W", "W", "W", "B", "B", "B"],
 ["W", "W", "W", "W", "W", "W", "B", "B"],
 ["W", "B", "B", "B", "B", "B", "B", "B"]]
```
- テストで渡された盤面をチェック。


##### 2. 空白のマスの数を調べる
```shell
irb(#<ReversiMethodsTest:0x000000...):002> p board.flatten.count(BLANK_CELL)
0
=> 0
```
- 1. の結果を見ても分かるが、返ってくる数が`0`なのでリバーシの試合の終了条件は「**盤面全てのマスが石で置かれている状態**」という条件になる。

##### 3. 盤面に置かれている白石・黒石の数を調べる
```shell
irb(#<ReversiMethodsTest:0x000000...):003> p board.flatten.count(WHITE_STONE)
30
=> 30
irb(#<ReversiMethodsTest:0x000000...):004> p board.flatten.count(BLACK_STONE)
34
=> 34
```
- これも先ほどの結果を見れば分かるが終了条件は「**盤面全てのマスが石で置かれている状態**」、もし白石・黒石のどちらかが**0枚**なら終了条件は「（盤面に白石だけまたは黒石だけが残っている）最も早い勝利」。

##### 4. placeable? の挙動を確認
```shell
# trueやfalseの真偽値が返らず、盤面が表示された
irb(#<ReversiMethodsTest:0x000000...):005> p placeable?(board, WHITE_STONE)
[["W", "W", "W", "W", "W", "W", "W", "W"], ["W", "B", "B", "W", "W", "B", "W", "B"], ["W", "B", "B", "B", "B", "W", "B", "B"], ["W", "B", "W", "B", "B", "B", "B", "B"], ["W", "B", "W", "W", "B", "B", "B", "B"], ["W", "B", "W", "W", "W", "B", "B", "B"], ["W", "W", "W", "W", "W", "W", "B", "B"], ["W", "B", "B", "B", "B", "B", "B", "B"]]
=> 
[["W", "W", "W", "W", "W", "W", "W", "W"],
 ["W", "B", "B", "W", "W", "B", "W", "B"],
 ["W", "B", "B", "B", "B", "W", "B", "B"],
 ["W", "B", "W", "B", "B", "B", "B", "B"],
 ["W", "B", "W", "W", "B", "B", "B", "B"],
 ["W", "B", "W", "W", "W", "B", "B", "B"],
 ["W", "W", "W", "W", "W", "W", "B", "B"],
 ["W", "B", "B", "B", "B", "B", "B", "B"]]
irb(#<ReversiMethodsTest:0x000000...):006> p placeable?(board, BLACK_STONE)
[["W", "W", "W", "W", "W", "W", "W", "W"], ["W", "B", "B", "W", "W", "B", "W", "B"], ["W", "B", "B", "B", "B", "W", "B", "B"], ["W", "B", "W", "B", "B", "B", "B", "B"], ["W", "B", "W", "W", "B", "B", "B", "B"], ["W", "B", "W", "W", "W", "B", "B", "B"], ["W", "W", "W", "W", "W", "W", "B", "B"], ["W", "B", "B", "B", "B", "B", "B", "B"]]
=> 
[["W", "W", "W", "W", "W", "W", "W", "W"],
 ["W", "B", "B", "W", "W", "B", "W", "B"],
 ["W", "B", "B", "B", "B", "W", "B", "B"],
 ["W", "B", "W", "B", "B", "B", "B", "B"],
 ["W", "B", "W", "W", "B", "B", "B", "B"],
 ["W", "B", "W", "W", "W", "B", "B", "B"],
 ["W", "W", "W", "W", "W", "W", "B", "B"],
 ["W", "B", "B", "B", "B", "B", "B", "B"]]
```
- `p placeable?(board, WHITE_STONE)`, `p placeable?(board, BLACK_STONE)`それぞれのコードの返り値は`true`もしくは`false`の真偽値のはず。しかし、実際は盤面（`board`）が返ってきた。

#### 浮かぶ疑問
##### 返り値が配列？
- `placeable?`メソッドを呼び出して得られた出力が`board`の内容そのままだった。
- 本来は`true`や`false`を返して欲しいのに（期待する内容）、実際は配列が返ってきた → **真偽値を返していない**
- つまり「何もしていない」のと同じ状況。

という点で「`false`を返すコードが足りないのでは？」と推測。

##### 何故、配列が返ったのか？
Rubyという言語には「最後に評価された式の値が返り値になる」という仕様（ルール）が存在している。`placeable?`メソッドでは最後に実行されたのが`board`だったため真偽値ではなく盤面（配列）を返している。

参考サイト：[【Ruby】 返り値（戻り値）とは？returnの使い方を初心者向けに解説](https://pikawaka.com/ruby/return-value)

↑一次情報に辿り着けなかったのは今の私の実力不足。けれど、参考にさせていただきました。

##### return true if put_stone(...)は書かれているが、置けないときの false が抜けている？
コードをよく読むと、「**石が置けなかった**」場合に返す`false`の一文が書かれていないことに気付ける。
```ruby
      return true if put_stone(board, position.to_cell_ref, attack_stone_color, dry_run: true) # もし石が置ける場合はtrueを返す
# ↑ここまででreturn trueが実行されなかったら......？
# ↓石が置けない場合の処理（false）が何も書かれていない
    end
  end
end
```

### false を書く場所
`board.each_with_index do |cols, row|`と`cols.each_with_index do |cell, col|`の2つの繰り返し処理が終わった後に実行されるように、繰り返し処理の外に配置する。
```ruby
def placeable?(board, attack_stone_color)
  board.each_with_index do |cols, row|
    cols.each_with_index do |cell, col|
      next unless cell == BLANK_CELL

      position = Position.new(row, col)
      return true if put_stone(board, position.to_cell_ref, attack_stone_color, dry_run: true)
    end
  end
  false
end
```

### テスト結果を確認
```shell
~/bug_reversi/test % ruby reversi_methods_test.rb
Run options: --seed 30759

# Running:

.........

Finished in 0.021072s, 427.1071 runs/s, 854.2141 assertions/s.

9 runs, 18 assertions, 0 failures, 0 errors, 0 skips
```
......多分大丈夫！
</details>


---


### ✍🏻 感想
#### 💡 binding.irbの利便性を実感！
「あといくつ修正すればいいのだろう......」と思いながら進めていましたが、メンターの岡嵜さんからのアドバイスを参考に`binding.irb`を使用してデバッグしてみました。事前に使い方を調べ、いつものようにポチポチと操作していたのですが、その便利さに驚きました。

ちなみに、先日の特別授業で駒形さんが`binding.irb`をスムーズに使いこなしていた様子がとても印象的で覚えています🧑🏻‍💻

無事に？修正を終えて、残すは提出のみです。今日はこれ以上頭が回らないので、PR の作成とメンターさんへの提出は別日に行いたいと思います。


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 8 hours 31 min
- Total: 1208 hours 25 min
