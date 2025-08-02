# 2025/08/02(土)
## 📚 プラクティス『プログラムの修正（リバーシ編）』


### 🧩 タスクばらし
- [x] プラクティスの内容を咀嚼
- [x] タスクばらし、スモールステップの作成
- [x] ソースコードの言語化
- [ ] ソースコードを修正
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

- [ ] ソースコードを修正
  - test_cannot_put_stone
    - [x] 修正
  - test_finished_of_quickest_win_board
    - [ ] 修正
  - test_put_stone
    - [x] 修正
  - test_turn
    - [x] 修正
  - test_finished_of_full_board
    - [ ] 修正

</details>

<details><summary>課題提出</summary>

- [ ] 修正したソースコードを Pull Request としてアップ
- [ ] Pull Request としてアップした URL とテストコードの実行結果を提出
</details>


---
### 🧑🏻‍💻 本日の取り組み
#### プラクティス『プログラムの修正（リバーシ編）』
##### test_cannot_put_stone
- 修正を行う


---


### 🎯 次回
#### プラクティス『プログラムの修正（リバーシ編）』
##### test_finished_of_quickest_win_board / test_finished_of_full_board
- バグの原因を探る
    

---


### 💡 本日の学び・気付き
#### test_cannot_put_stone
<details><summary>⚠️ ネタバレ注意</summary>

### turnメソッドの動きを丁寧に言語化
```ruby
def turn(board, target_pos, attack_stone_color, direction)
    return false if target_pos.out_of_board?
    return false if target_pos.stone_color(board) == attack_stone_color

    next_pos = target_pos.next_position(direction)
    if (next_pos.stone_color(board) == attack_stone_color) || turn(board, next_pos, attack_stone_color, direction)
    board[target_pos.row][target_pos.col] = attack_stone_color
    true
  else
    false
  end
end
```
```ruby
def turn(board, target_pos, attack_stone_color, direction)
```
- 「`board`, `target_pos`, `attack_stone_color`, `direction`を引数に持つ`turn`メソッドを定義する」。
  - `board`：リバーシの盤面。
  - `target_pos`：ひっくり返す（裏返したい）マス。
  - `attack_stone_color`：攻撃する側の石の色。
  - `direction`：方向。

```ruby
return false if target_pos.out_of_board?
```
- 「もし、ひっくり返したい（狙っている）マスが盤面外だったら、`false`を返して、`turn`メソッドを途中で終わらせる」。
  - `return`：メソッドを途中で終わらせる。予約語？
  - `target_pos.out_of_board?`：「ひっくり返すマスは盤面外ですか？」という問いに答える形で`true`または`false`を返す。

```ruby
return false if target_pos.stone_color(board) == attack_stone_color
```
- 「もし、ひっくり返したい（狙っている）マスに、攻撃する（自分の色の）石があったら`false`を返して、`turn`メソッドを途中で終わらせる」。

```ruby
next_pos = target_pos.next_position(direction)
```
- 「狙っているマスから`direction`が示す方向に一つ進んだマスを、変数`next_pos`に紐付ける」。

```ruby
if (next_pos.stone_color(board) == attack_stone_color) || turn(board, next_pos, attack_stone_color, direction)
```
- 「もし、1マス進んだ先に自分の石があるか、あるいは`next_pos`, `attack_stone_color`, `direction`を引数にして`turn`メソッドを呼び出すのなら、以下の処理を実行する」。

```ruby
board[target_pos.row][target_pos.col] = attack_stone_color
```
- 「盤面`board`の、`target_pos`が示す行（`row`）と列（`col`）の位置に、自分の石を置く」。

```ruby
    true
  else
    false
  end
end
```
- 「成功したら`true`を返し、そうでなければ`false`を返す」。

そして、
- `return false if target_pos.out_of_board?`
- `return false if target_pos.stone_color(board) == attack_stone_color`

この 2行は「この状態では何もできないので`turn`メソッドの処理を中断する役割」を担っている。

ということは、2行と同じ場所に「もし、狙っているマスが空白のマスだったら`false`を返して、`turn`メソッドを途中で終わらせる」といった内容のコードを書き加えればよい、と考える。

### 実際にコードを考える
あまり難しく考えずに、既に書かれているコードを参考に書く。
```ruby
# もし狙っているマスが空白のマスならfalseを返し、turnメソッドを途中で終わらせる
return false if target_pos.stone_color(board) == BLANK_CELL
```
```ruby
def turn(board, target_pos, attack_stone_color, direction)
  return false if target_pos.out_of_board?
  return false if target_pos.stone_color(board) == attack_stone_color
  return false if target_pos.stone_color(board) == BLANK_CELL # ←return false if target_pos.stone_color(board) == BLANK_CELLを追加

  next_pos = target_pos.next_position(direction)
  if (next_pos.stone_color(board) == attack_stone_color) || turn(board, next_pos, attack_stone_color, direction)
    board[target_pos.row][target_pos.col] = attack_stone_color
    true
  else
    false
  end
end
```

### テスト結果を確認
```shell
~/bug_reversi/test % ruby reversi_methods_test.rb
Run options: --seed 5351

# Running:

.....FF..

Finished in 0.007866s, 1144.1648 runs/s, 2161.2001 assertions/s.

  1) Failure:
ReversiMethodsTest#test_finished_of_quickest_win_board [reversi_methods_test.rb:120]:
Expected false to be truthy.

  2) Failure:
ReversiMethodsTest#test_finished_of_full_board [reversi_methods_test.rb:107]:
Expected false to be truthy.

9 runs, 17 assertions, 2 failures, 0 errors, 0 skips
```
↑`ReversiMethodsTest#test_cannot_put_stone`がなくなり、failureの残りは2つ。

### 次の修正へ
テスト結果には、
- ①`test_finished_of_quickest_win_board`
- ②`test_finished_of_full_board`

**① 最も早い勝利でリバーシの試合が終了**
**② リバーシの盤面全てに白色と黒色の石が置かれて終了**

と、「**リバーシの終了条件**」について関係している。そして①・②共に`Expected false to be truthy.`（「**true が返ることを想定していたが、実際は false を返している**」）と表示されているので、`true`が返るように修正すれば良いと考える。

### テストが何を期待しているかを確認する
- ①`test_finished_of_quickest_win_board`
  - → 「最も早い勝利で試合が終了」とは、盤面の石の色が黒色だけあるいは白色だけの状態を指す。
  - riversi_methods_test.rbファイルを確認すると以下の内容のコードが書かれている↓。
```ruby
def test_finished_of_quickest_win_board
  assert finished?(build_board(<<~BOARD)) # 白最短勝利
    --------
    ---W----
    ---WW---
    -WWWWW--
    ---WWW--
    ---WWW--
    --------
    --------
  BOARD
  assert finished?(build_board(<<~BOARD)) # 黒最短勝利
    --------
    --------
    ----B---
    ---BBB--
    --BBBBB-
    ---BBB--
    ----B---
    --------
  BOARD
end
```
コードを見ると、「最も早い勝利で試合が終了（`quickest_win`）」は以下の2パターン。
**1. 盤面に白石だけが残っているパターン。**
**2. 盤面に黒石だけが残っているパターン。**



- ②`test_finished_of_full_board`
  - これも riversi_methods_test.rbファイルを確認すると、「盤面に空白のマス（`-`などの`BLACK_CELL`）が一切なく、全てのマスに黒石・白石が置かれた状態」になっている。
  - したがって、「リバーシの盤面のマス全てに石が置かれている場合、`true`を返し、試合が終了と判定する」のが期待される内容だと考える。
```ruby
def test_finished_of_full_board
  assert finished?(build_board(<<~BOARD)) # 全て埋まった盤面
    WWWWWWWW
    WBBWWBWB
    WBBBBWBB
    WBWBBBBB
    WBWWBBBB
    WBWWWBBB
    WWWWWWBB
    WBBBBBBB
  BOARD
end
```
</details>


---


### ✍🏻 感想
#### 🏋🏻 test_cannot_put_stoneに四苦八苦しつつ一歩前進
「**修正への考え方**」や「**書いたコード**」が正しいのかどうかまだ自信が持てませんが、それでもなんとか一歩前進しました。本当は心の中では小躍りしたいほど嬉しいのですが、「本当にこれで合っているのだろうか？」という不安もあって、素直に喜びきれないのが正直なところです。

このプラクティスを乗り越えた皆さんは本当に素晴らしいです。私も皆さんに続き、最後まで諦めずに課題クリアを目指します！


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 4 hours 42 min
- Total: 1199 hours 54 min
