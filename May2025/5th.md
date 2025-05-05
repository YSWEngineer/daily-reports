# 2025/05/05(月)
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
### reversi_methods_test.rbファイルを言語化（続き）
reversi_methods_test.rbファイル
```ruby
  def test_invalid_position # test_invalid_positionメソッドを作成
    board = build_initial_board # build_initial_boardメソッドを呼び出して、その戻り値をローカル変数boardに代入する
    e = assert_raises RuntimeError do # assert_raisesメソッドを使い、このあと実行するブロック内でRuntimeErrorが発生することを期待し、その発生した例外オブジェクトを変数eに代入する
      put_stone(board, 'x0', BLACK_STONE) # boardという盤面データ（二次元配列）に対して、'x0'の位置に黒石（BLACK_STONE）を置く処理を行うput_stoneメソッド
    end # ブロックの終わり
    assert_equal '無効なポジションです', e.message # 例外オブジェクトeが持つメッセージ（e.message）が、文字列'無効なポジションです'と確認。
  end # test_invalid_positionメソッド作成終了

  def test_already_have_a_stone # test_already_have_a_stoneメソッドを作成
    board = build_initial_board # build_initial_boardメソッドを呼び出して、その戻り値をローカル変数boardに代入する
    e = assert_raises RuntimeError do # assert_raisesメソッドを使い、このあと実行するブロック内でRuntimeErrorが発生することを期待し、その発生した例外オブジェクトを変数eに代入する
      put_stone(board, 'd5', BLACK_STONE) # boardという盤面データ（二次元配列）に対して、'd5'の位置に黒石（BLACK_STONE）を置く処理を行うput_stoneメソッド
    end # ブロックの終わり
    assert_equal 'すでに石が置かれています', e.message # 例外オブジェクトeが持つメッセージ（e.message）が、文字列'すでに石が置かれています'と確認。
  end # test_already_have_a_stoneメソッドを作成終了
```
- `e = assert_raises RuntimeError do ... end`
  - `e`：例外オブジェクトを格納する変数名。exception（「例外」という意味）の省略形として、`e`や`ex`のような名前にする。
  - `assert_raises`メソッド：これは Minitest の検証メソッドで、指定したエラー（例外）が発生したときにテストをパスさせる。
  - `RuntimeError`：Ruby が持っている例外（エラー）のクラスの一つで、「実行時になんらかの問題が起きた」ことを示す。特定のエラーに分けたい場合は、もっと細かいクラス（`ArgumentError`）などもあるが、とりあえず「エラーを投げたい」というときに`RuntimeError`がよく使われる。
    - `run-time`：プログラムが実行されている状態のこと。
    - `put_stone`：reversi_methods.rbファイル内にある`ReversiMethods`モジュール内で定義されたメソッド。
      - 1. 引数で渡された盤面（board）、位置（'x0'）、石の色（BLACK_STONEやWHITE_STONE）を受け取り、
      - 2. その位置が有効で空きがあれば石を置き、挟んだ相手の石を裏返し、
      - 3. 実際におけたかどうかをtrueまたはfalseで返す処理を行う。
    - `assert_equal`：Minitest が提供している実行結果を確認するための検証メソッド。
    - `'無効なポジションです'`：期待する結果。
    - `e.message`：テスト対象となる値や式。
      - `message`メソッド：例外発生時のエラーメッセージを返す。

`def test_already_have_a_stone 〜 end`までのコードもほぼ上記と似たような内容であることを確認。


---


## ✍🏻 感想
### ⚪️⚫️ コツコツと言語化
この数時間で約14行分の言語化。「全ファイルを全部言語化するには、何時間、何日かかるのだろう？」と考えましたが、おかげでリバーシプログラムの中身が少しずつ見えてきています。とはいえ、時間をかけるだけでなく、スピード感も大切に進めていきたいと思います。


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2 hours 42 min
- Total: 1095 hours 00 min
