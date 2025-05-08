# 2025/05/08(木)
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
  - [x] ① reversi_methods_test.rb
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
- reversi_methods_test.rbファイルを言語化


---


## 🎯 次回
### プラクティス『プログラムの修正（リバーシ編）』
- reversi.rbファイルを言語化
    

---


## 💡 本日の学び・気付き
### reversi_methods_test.rbファイルを言語化（続き）
reversi_methods_test.rbファイル
```ruby
  def test_put_stone # test_put_stoneメソッドを作成
    board = build_initial_board # build_initial_boardメソッドを呼び出して、その結果をローカル変数boardに代入する。ここで得られるboardは、8×8の二次元配列。この変数boardを使って以降のテストで石を置いていく
    assert put_stone(board, 'e6', BLACK_STONE) # boardという盤面データ（二次元配列）に対して、'e6'の位置に黒石（BLACK_STONE）を置く処理を行うput_stoneメソッドの実行結果をassertメソッドで検証する
    assert_equal build_board(<<~BOARD), board # 変数boardの結果がこの後に書かれた盤面BOARD（期待する結果）になることをassert_equalメソッドで検証している
      --------
      --------
      --------
      ---WB---
      ---BB---
      ----B---
      --------
      --------
    BOARD # ヒアドキュメントの終わり
    assert put_stone(board, 'f4', WHITE_STONE) # boardという盤面データ（二次元配列）に対して、'f4'の位置に白石（WHITE_STONE）を置く処理を行うput_stoneメソッドの実行結果をassertメソッドで検証する
    assert_equal build_board(<<~BOARD), board # 変数boardの結果がこの後に書かれた盤面BOARD（期待する結果）になることをassert_equalメソッドで検証している
      --------
      --------
      --------
      ---WWW--
      ---BB---
      ----B---
      --------
      --------
    BOARD # ヒアドキュメントの終わり
  end # test_put_stoneメソッドを作成終了

  def test_cannot_put_stone # test_cannot_put_stoneメソッドを定義
    initial_data = <<~BOARD # ここもヒアドキュメントで、以下の盤面を変数initial_dataに代入
      W-WWWW--
      W-BWWW--
      WBWWWWW-
      WWBWWW--
      WBBBBB--
      --B-----
      --B-----
      --B-----
    BOARD # ヒアドキュメントの終わり
    board = build_board(initial_data) # initial_dataという文字列で書かれた盤面の情報をbuild_boardメソッドで配列に変換し、それを変数boardに代入する
    refute put_stone(board, 'b1', BLACK_STONE) # boardという盤面データ（二次元配列）に対して、'b1'の位置に黒石（BLACK_STONE）を置く処理を行うput_stoneメソッドの実行結果をrefuteメソッドで検証する
    assert_equal build_board(initial_data), board # initial_dataという文字列で書かれた盤面の情報をbuild_boardメソッドで配列に変換した情報（期待する結果）と、変数boardの中身が同じなのかassert_equalメソッドで検証している
  end

  def test_turn # test_turnメソッドを定義
    board = build_board(<<~BOARD) # ここもヒアドキュメントで、以下の盤面をbuild_boardメソッドで配列化し、その結果を変数boardに代入する。
      --------
      ---B----
      --WB----
      --WBB---
      --WWW---
      --------
      --------
      --------
    BOARD # ヒアドキュメントの終わり
    assert put_stone(board, 'b4', BLACK_STONE) # boardという盤面データ（二次元配列）に対して、'b4'の位置に黒石（BLACK_STONE）を置く処理を行うput_stoneメソッドの実行結果をassertメソッドで検証する
    assert_equal build_board(<<~BOARD), board # 変数boardの結果がこの後に書かれた盤面BOARD（期待する結果）になることをassert_equalメソッドで検証している
      --------
      ---B----
      --BB----
      -BBBB---
      --WWW---
      --------
      --------
      --------
    BOARD # ヒアドキュメントの終わり
  end # test_turnメソッドの定義終了

  def test_finished_of_initial_board # test_finished_of_initial_boardメソッドを定義
    board = build_initial_board # build_initial_boardメソッドを呼び出して、その戻り値をローカル変数boardに代入する
    refute finished?(board) # finished?(board)がfalse（リバーシゲームがまだ終了していない）であることをrefuteメソッドで検証する
  end # test_finished_of_initial_boardメソッドの定義終了

  def test_finished_of_full_board # test_finished_of_full_boardメソッドを定義
    assert finished?(build_board(<<~BOARD)) # 盤面の文字列情報をbuild_boardで配列化し、finished?で終了していることをassertメソッドで検証する。
      WWWWWWWW
      WBBWWBWB
      WBBBBWBB
      WBWBBBBB
      WBWWBBBB
      WBWWWBBB
      WWWWWWBB
      WBBBBBBB
    BOARD # ヒアドキュメントの終わり
  end # test_finished_of_full_boardメソッドの定義終了

  def test_finished_of_quickest_win_board # test_finished_of_quickest_win_boardメソッドを定義
    assert finished?(build_board(<<~BOARD)) # 盤面の文字列情報をbuild_boardで配列化し、finished?で終了していることをassertメソッドで検証する。
      --------
      ---W----
      ---WW---
      -WWWWW--
      ---WWW--
      ---WWW--
      --------
      --------
    BOARD # ヒアドキュメントの終わり
    assert finished?(build_board(<<~BOARD)) # 盤面の文字列情報をbuild_boardで配列化し、finished?で終了していることをassertメソッドで検証する。
      --------
      --------
      ----B---
      ---BBB--
      --BBBBB-
      ---BBB--
      ----B---
      --------
    BOARD # ヒアドキュメントの終わり
  end # test_finished_of_quickest_win_boardメソッドの定義終了

  def test_finished_of_player_skip_board # test_finished_of_player_skip_boardメソッドを定義
    refute finished?(build_board(<<~BOARD)) # build_boardで盤面を作成し、finished?がまだ終了ではないことをrefuteメソッドで検証する
      WWWWWWWB
      WBBWWBWB
      WBBBBWBB
      WBWBBBB-
      WBWWBBBB
      WBWWWBBB
      WWWWBWBB
      WBBBBBBB
    BOARD
    refute finished?(build_board(<<~BOARD)) # build_boardで盤面を作成し、finished?がまだ終了ではないことをrefuteメソッドで検証する
      WWWWWWWW
      WBBWWBWB
      WBBBBWBB
      WBWBBBBB
      WBWWBBBB
      WBWWWBBB
      BBBB-WBB
      WBBBBBBB
    BOARD
  end # test_finished_of_player_skip_boardメソッドの定義終了
end # ReversiMehodsTestクラスの作成終了
```
- `test_put_stone`：これもテストメソッド。Minitest というフレームワーク（**テスティングフレームワーク**）を利用している。メソッド名の先頭に`test_`を付けるのが決まり。
- `board = build_initial_board`
  - `board`：board は 8 × 8 の二次元配列。
- `assert put_stone(board, 'e6', BLACK_STONE)`
  - `assert`：`put_stone`メソッドの実行結果を確認するための検証メソッド。
- `assert_equal build_board(<<~BOARD), board`
  - `assert_equal`メソッド：実行結果を確認するための検証メソッド。型としては`assert_equal 期待する結果, テスト対象となる値や式`となる。今回の場合は、期待する結果には`build-board(<<~BOARD)`、テスト対象となる値や式には`board`（変数）が当てはまる。
  - `build_board(<<~BOARD)`：「期待する結果」つまり二次元配列で作られたもの。
  - `<<~BOARD`：ヒアドキュメント（行指向文字列リテラル）
  - `board`：変数`board`で、盤面に石を置いた後の結果。
- `board = build_board(initial_data)`
  - `initial_data`：二次元配列の中身。
  - `build_board`：`initial_data`の中身を配列に変換。
- `refute put_stone(board, 'b1', BLACK_STONE)`
  - `refute`：Minitest の検証メソッドの1つ。「その結果が`false`であること（偽であればパスする）」を確認するテスト。


---


## ✍🏻 感想
### ⚪️⚫️ コードを読んでファイルを知る
reversi_methods_test.rbファイルが、「リバーシゲームの各メソッドが正しく動作するかどうかを検証するためのテストコードが書かれているファイル」だということを改めて確認することができました。

ファイル名に`test`が書かれているので当然のことではありますが、実際にテストコードの中身を読み解いていく中で少しずつ理解が深まり、それがとても嬉しく感じています😊


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 4 hours 32 min
- Total: 1099 hours 32 min
