# 2025/07/09(水)
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
    - [ ] 修正
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
- `binding.break`を書き込み、挙動を一つずつ確認する


---


### 🎯 次回
#### プラクティス『プログラムの修正（リバーシ編）』
- `binding.break`を書き込み、挙動を一つずつ確認する
    

---


### 💡 本日の学び・気付き
#### プラクティス『プログラムの修正（リバーシ編）』
<details><summary>バグの修正　⚠️ネタバレ注意</summary>

##### 1. 石を置く位置の行（row）と列（col）の順序が逆
###### 該当箇所：
- `reversi_methods.rb`の`put_stone`メソッド内、50行目
```ruby
copied_board[pos.col][pos.row] = stone_color
```
###### 問題点：
- 行（row）と列（col）の順番が逆。
- 盤面では、`board[row][col]`となっている。
###### 修正：
```ruby
copied_board[pos.row][pos.col] = stone_color
```
</details>

##### テスト結果を確認
```shell
~/bug_reversi/test % ruby reversi_methods_test.rb 
Run options: --seed 5627

# Running:

..F..FF..

Finished in 0.004859s, 1852.2330 runs/s, 3292.8586 assertions/s.

  1) Failure:
ReversiMethodsTest#test_cannot_put_stone [reversi_methods_test.rb:73]:
Expected true to not be truthy.

  2) Failure:
ReversiMethodsTest#test_finished_of_quickest_win_board [reversi_methods_test.rb:120]:
Expected false to be truthy.

  3) Failure:
ReversiMethodsTest#test_finished_of_full_board [reversi_methods_test.rb:107]:
Expected false to be truthy.

9 runs, 16 assertions, 3 failures, 0 errors, 0 skips
```
1. `test_cannot_put_stone`
- 盤面で石を置けないことについて。
- `Expected true to not be truthy.`
  - 返ってきた値が`true`（真）だったが、`true`ではないこと（つまり`false`）を期待していた。

2. `test_finished_of_quickest_win_board`
- 最短で勝利した盤面について。
- `Expected false to be truthy.`
  - 返ってきた値が`false`（偽）だったが、`true`であることを期待していた。

3. `test_finished_of_full_board`
- 盤面全てに石が置かれてリバーシゲームが終了した場合について。
- `Expected false to be truthy.`
  - 返ってきた値が`false`（偽）だったが、`true`であることを期待していた。

---


### ✍🏻 感想
#### 🤝🏻 binding.breakと仲良くなりたい
メンターの田中さんからいただきましたアドバイス：

> コード読むにあたって、よくわからないところに binding.break を入れて、step実行などをして、コードを理解するためにも使えます。理解せずにやみくもに使うのはよく無いですが、理解するためにも使えるのでやってないならやってみてください 💪

この言葉を参考に、実際に`binding.break`を書き込みながら、処理の挙動を一つずつ丁寧に確認しています。やはりハンズオンでの操作は、理解の解像度がグッと上がりますね。次回もポチポチ動かしながら、地道に理解を深めていきたいです。


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3 hours 25 min
- Total: 1155 hours 57 min
