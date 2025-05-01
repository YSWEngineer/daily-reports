# 2025/05/01(木)
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

- [ ] ソースコードの言語化
  - [ ] position.rb
  - [ ] reversi_methods.rb
  - [ ] reversi_methods_test.rb
  - [ ] reversi.rb
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
- テストコードを実行し、その結果を言語化して確認


---


## 🎯 次回
### プラクティス『プログラムの修正（リバーシ編）』
- ソースコードの言語化
    

---


## 💡 本日の学び・気付き
### テストコードを実行し、その結果を1つずつ言語化して確認していく
テストコードの実行
```shell
~/bug_reversi % ruby test/reversi_methods_test.rb 
Run options: --seed 20221

# Running:

FF..FFF..

Finished in 0.060686s, 148.3044 runs/s, 230.6957 assertions/s.

  1) Failure:
ReversiMethodsTest#test_cannot_put_stone [test/reversi_methods_test.rb:73]:
Expected true to not be truthy.

  2) Failure:
ReversiMethodsTest#test_finished_of_quickest_win_board [test/reversi_methods_test.rb:120]:
Expected false to be truthy.

  3) Failure:
ReversiMethodsTest#test_put_stone [test/reversi_methods_test.rb:38]:
--- expected
+++ actual
@@ -1 +1 @@
-[["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "W", "B", "-", "-", "-"], ["-", "-", "-", "B", "B", "-", "-", "-"], ["-", "-", "-", "-", "B", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"]]
+[["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "W", "B", "-", "-", "-"], ["-", "-", "-", "B", "B", "B", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"]]


  4) Failure:
ReversiMethodsTest#test_turn [test/reversi_methods_test.rb:89]:
--- expected
+++ actual
@@ -1 +1 @@
-[["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "B", "-", "-", "-", "-"], ["-", "-", "B", "B", "-", "-", "-", "-"], ["-", "B", "B", "B", "B", "-", "-", "-"], ["-", "-", "W", "W", "W", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"]]
+[["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "B", "-", "-", "-", "-"], ["-", "-", "B", "B", "-", "-", "-", "-"], ["-", "-", "B", "B", "B", "-", "-", "-"], ["-", "-", "W", "W", "W", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"]]


  5) Failure:
ReversiMethodsTest#test_finished_of_full_board [test/reversi_methods_test.rb:107]:
Expected false to be truthy.

9 runs, 14 assertions, 5 failures, 0 errors, 0 skips
```

#### 1. テスト結果
```shell
FF..FFF..
```
- `.`は成功、`F`は失敗（Failure）を表す。
- `FF`：2つ続けて失敗。
- `..`：2つ成功。
- `FFF`：3つ失敗。
- `..`：2つ成功。
- テストメソッド 9件のうち 5件が失敗。

#### 2. Failure の詳細な情報
```shell
  1) Failure:
ReversiMethodsTest#test_cannot_put_stone [test/reversi_methods_test.rb:73]:
Expected true to not be truthy.
```
- `1) Failure`：1つ目の失敗。
- `ReversiMethodsTest#test_cannot_put_stone [test/reversi_methods_test.rb:73]:`：ReversiMethodsTestクラスのインスタンスメソッドtest_cannot_put_stone（reversi_methods_test.rbの73行目）で失敗した。
- `Expected true to not be truthy.`：「true は truthy（真）ではないと予想した」

```shell
  2) Failure:
ReversiMethodsTest#test_finished_of_quickest_win_board [test/reversi_methods_test.rb:120]:
Expected false to be truthy.
```
- `2) Failure`：2つ目の失敗。
- `ReversiMethodsTest#test_finished_of_quickest_win_board [test/reversi_methods_test.rb:120]:`：ReversiMethodsTestクラスのインスタンスメソッドtest_finished_of_quickest_win_board（reversi_methods_test.rbの120行目）で失敗した。
- `Expected false to be truthy.`：「false が truthy になることを予想した」

```shell
  3) Failure:
ReversiMethodsTest#test_put_stone [test/reversi_methods_test.rb:38]:
--- expected
+++ actual
@@ -1 +1 @@
-[["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "W", "B", "-", "-", "-"], ["-", "-", "-", "B", "B", "-", "-", "-"], ["-", "-", "-", "-", "B", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"]]
+[["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "W", "B", "-", "-", "-"], ["-", "-", "-", "B", "B", "B", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"]]
```
- `3) Failure`：3つ目の失敗。
- `ReversiMethodsTest#test_put_stone [test/reversi_methods_test.rb:38]:`：ReversiMethodsTestクラスのインスタンスメソッドtest_put_stone（reversi_methods_test.rbの38行目）で失敗した。
- `--- expected`：--- 期待した
- `+++ actual`：+++ 実際の
- `@@ -1 +1 @@`：差分？（よくわかっていない箇所）
- `[[ から ]]`：おそらくリバーシの盤面についての情報。`B`は黒石（Black）を意味し、`W`は白石（White）を意味していると推測。

```shell
  4) Failure:
ReversiMethodsTest#test_turn [test/reversi_methods_test.rb:89]:
--- expected
+++ actual
@@ -1 +1 @@
-[["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "B", "-", "-", "-", "-"], ["-", "-", "B", "B", "-", "-", "-", "-"], ["-", "B", "B", "B", "B", "-", "-", "-"], ["-", "-", "W", "W", "W", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"]]
+[["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "B", "-", "-", "-", "-"], ["-", "-", "B", "B", "-", "-", "-", "-"], ["-", "-", "B", "B", "B", "-", "-", "-"], ["-", "-", "W", "W", "W", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-"]]
```
- `4) Failure`：4つ目の失敗。
- `ReversiMethodsTest#test_turn [test/reversi_methods_test.rb:89]:`：ReversiMethodsTestクラスのインスタンスメソッドtest_turn（reversi_methods_test.rbの89行目）で失敗した。
- `--- expected`：--- 期待した
- `+++ actual`：+++ 実際の
- `@@ -1 +1 @@`：差分？（よくわかっていない箇所）
- `[[ から ]]`：おそらくリバーシの盤面についての情報。`B`は黒石（Black）を意味し、`W`は白石（White）を意味していると推測。← 3つ目の失敗と同じ。
```shell
  5) Failure:
ReversiMethodsTest#test_finished_of_full_board [test/reversi_methods_test.rb:107]:
Expected false to be truthy.
```
- `5) Failure`：5つ目の失敗。
- `ReversiMethodsTest#test_finished_of_full_board [test/reversi_methods_test.rb:107]:`：ReversiBethodsTestクラスのインスタンスメソッドtest_finished_of_full_board（reversi_methods_test.rbの107行目）で失敗した。
- `Expected false to be truthy.`：「false が truthy になることを予想した」
```shell
9 runs, 14 assertions, 5 failures, 0 errors, 0 skips
```
最後の行はテストの実行結果のまとめ。
- `9 runs`：実行したテストメソッドの件数。
- `14 assertions`：実行した検証メソッドの件数。
- `5 failures`：検証に失敗したテストメソッドの件数。
- `0 errors`：検証中にエラーが発生したテストメソッドの件数。
- `0 skips`：skipメソッドにより実行をスキップされたテストメソッドの件数。

※ `failures`と`erros`の件数がどちらも`0`であれば、テストは全てパスしたことになる。

### もう一度プラクティスの内容を確認
- 注意点・ヒントには、`test/reversi_methods_test.rb`の修正はせずに、テストがパスするようにしてください。と、記されている。→ `test/reversi_methods_test.rb`ファイルのコードには間違いが含まれていないことがわかる。


---


## ✍🏻 感想
### ⚪️⚫️ ようやく歩き出せたような......
ファイルとずーーーっとにらめっこしても手掛かりが得られなかったので、「とりあえずテストコードを実行して出力された内容を確認しよう」と思い、1行ずつ言語化しながらコードの理解に努めました。

その結果、「あれ？このインスタンスメソッドで失敗しているのだから、そこを重点的に調べていけば何かしら手掛かり掴めるのでは？じゃあ、いきなり`binding.break`を書き込んで`Failure`の原因を探し出す前に他のソースコードも同じように 1行ずつ読み解いていったほうがいいよね！」という考えに至りました。

このアプローチが正しいかどうかはまだわかりませんが、次回は各ファイルを順番に丁寧に読み解いていきます。


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 7 hours 02 min
- Total: 1085 hours 04 min
