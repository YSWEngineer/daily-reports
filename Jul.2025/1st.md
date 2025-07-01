# 2025/07/01(火)
## 📚 プラクティス『プログラムの修正（リバーシ編）』


## 🧩 タスクばらし
- [x] プラクティスの内容を咀嚼
- [x] タスクばらし、スモールステップの作成
- [x] ソースコードの言語化
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
### グループコーチングの提出物の作成
- 立てた目標により具体性を持たせる

### プラクティス『プログラムの修正（リバーシ編）』
- 復習：rubygems（debug.gem）の使い方


---


## 🎯 次回
### グループコーチングの提出物の作成
- 立てた目標により具体性を持たせる

### プラクティス『プログラムの修正（リバーシ編）』
- 復習：rubygems（debug.gem）の使い方
    

---


## 💡 本日の学び・気付き
### 復習：rubygems（debug.gem）の使い方
#### continue / c を入力
- このコマンドは、プログラムを再開する。停止すべきポイントがなければ、そのプログラムの最後までプログラムを実行する。
- 下記のコードでは、1回目の`continue`で変数`number`の中身が`1`から`2`へ、もう一度`continue`を入力すると`2`から`3`になったのがわかる。
```shell
(rdbg) continue    # command
[1, 10] in fizzbuzz.rb
     1| #!/usr/bin/env ruby
     2| require 'debug'
     3| 
     4| (1..20).each do |number|
=>   5|   binding.break
     6|   if number % 15 == 0
     7|     puts "FizzBuzz"
     8|   elsif number % 3 == 0
     9|     puts "Fizz"
    10|   elsif number % 5 == 0
=>#0	block {|number=2|} in <main> at fizzbuzz.rb:5
  #1	[C] Range#each at fizzbuzz.rb:4
  # and 1 frames (use `bt' command for all frames)
(rdbg) number
2
(rdbg) continue    # command
2
[1, 10] in fizzbuzz.rb
     1| #!/usr/bin/env ruby
     2| require 'debug'
     3| 
     4| (1..20).each do |number|
=>   5|   binding.break
     6|   if number % 15 == 0
     7|     puts "FizzBuzz"
     8|   elsif number % 3 == 0
     9|     puts "Fizz"
    10|   elsif number % 5 == 0
=>#0	block {|number=3|} in <main> at fizzbuzz.rb:5
  #1	[C] Range#each at fizzbuzz.rb:4
  # and 1 frames (use `bt' command for all frames)
(rdbg) number
3
```
#### finish / fin を入力
- メソッドの実行をすぐに**抜ける**
  - **抜ける**：「メソッドの処理を終えて次のところで止まる」という意味。
- 下記のコードではメソッドの呼び出しの一番最後のところまで実行。例えばメソッドの実行を`step`で最後まで行うのは面倒な時は`finish`を使用すること。
```shell
[1, 10] in fizzbuzz.rb
     1| #!/usr/bin/env ruby
     2| require 'debug'
     3| 
     4| def fizzbuzz(number)
=>   5|   if number % 15 == 0
     6|     puts "FizzBuzz"
     7|   elsif number % 3 == 0
     8|     puts "Fizz"
     9|   elsif number % 5 == 0
    10|     puts "Buzz"
=>#0	Object#fizzbuzz(number=2) at fizzbuzz.rb:5
  #1	block {|number=2|} in <main> at fizzbuzz.rb:18
  # and 2 frames (use `bt' command for all frames)
(rdbg) finish    # command
2
[9, 18] in fizzbuzz.rb
     9|   elsif number % 5 == 0
    10|     puts "Buzz"
    11|   else
    12|     puts number
    13|   end
=>  14| end
    15| 
    16| (1..20).each do |number|
    17|   binding.break
    18|   fizzbuzz(number)
=>#0	Object#fizzbuzz(number=2) at fizzbuzz.rb:14 #=> nil
  #1	block {|number=2|} in <main> at fizzbuzz.rb:18
  # and 2 frames (use `bt' command for all frames)
(rdbg)
```
#### next / n を入力
- メソッドの中に入りたくない時はステップオーバーという機能がある。それが`next`。
- 下記のコードでは`fizzbuzz`メソッドの中には入らないで`fizzbuzz`メソッドを実行している。
```shell
[12, 19] in fizzbuzz.rb
    12|     puts number
    13|   end
    14| end
    15| 
    16| (1..20).each do |number|
=>  17|   binding.break
    18|   fizzbuzz(number)
    19| end
=>#0	block {|number=4|} in <main> at fizzbuzz.rb:17
  #1	[C] Range#each at fizzbuzz.rb:16
  # and 1 frames (use `bt' command for all frames)
(rdbg) n    # next command
[13, 19] in fizzbuzz.rb
    13|   end
    14| end
    15| 
    16| (1..20).each do |number|
    17|   binding.break
=>  18|   fizzbuzz(number)
    19| end
=>#0	block {|number=4|} in <main> at fizzbuzz.rb:18
  #1	[C] Range#each at fizzbuzz.rb:16
  # and 1 frames (use `bt' command for all frames)
(rdbg) n    # next command
4
[14, 19] in fizzbuzz.rb
    14| end
    15| 
    16| (1..20).each do |number|
    17|   binding.break
    18|   fizzbuzz(number)
=>  19| end
=>#0	block {|number=4|} in <main> at fizzbuzz.rb:19 #=> nil
  #1	[C] Range#each at fizzbuzz.rb:16
  # and 1 frames (use `bt' command for all frames)
```
#### help / h を入力
- 使えるコマンドを知りたい時は`help`コマンドを入力。
```shell
[14, 19] in fizzbuzz.rb
    14| end
    15| 
    16| (1..20).each do |number|
    17|   binding.break
    18|   fizzbuzz(number)
=>  19| end
=>#0	block {|number=8|} in <main> at fizzbuzz.rb:19 #=> nil
  #1	[C] Range#each at fizzbuzz.rb:16
  # and 1 frames (use `bt' command for all frames)
(rdbg) help    # command

### Control flow

* `s[tep]`
  * Step in. Resume the program until next breakable point.
* `s[tep] <n>`
  * Step in, resume the program at `<n>`th breakable point.
* `n[ext]`
  * Step over. Resume the program until next line.
* `n[ext] <n>`
  * Step over, same as `step <n>`.
* `fin[ish]`
  * Finish this frame. Resume the program until the current frame is finished.
* `fin[ish] <n>`
  * Finish `<n>`th frames.
* `u[ntil]`
  * Similar to `next` command, but only stop later lines or the end of the current frame.
  * Similar to gdb's `advance` command.
* `u[ntil] <[file:]line>`
  * Run til the program reaches given location or the end of the current frame.
* `u[ntil] <name>`
  * Run til the program invokes a method `<name>`. `<name>` can be a regexp with `/name/`.
* `c` or `cont` or `continue`
  * Resume the program.
* `q[uit]` or `Ctrl-D`
  * Finish debugger (with the debuggee process on non-remote debugging).
* `q[uit]!`
  * Same as q[uit] but without the confirmation prompt.
* `kill`
  * Stop the debuggee process with `Kernel#exit!`.
* `kill!`
  * Same as kill but without the confirmation prompt.
* `sigint`
  * Execute SIGINT handler registered by the debuggee.
  * Note that this command should be used just after stop by `SIGINT`.

中略

### Help

* `h[elp]`
  * Show help for all commands.
* `h[elp] <command>`
  * Show help for the given command.
```
#### help + コマンド
- コマンドの詳細を出力してくれる。
```shell
(rdbg) help step    # command

### Control flow

* `s[tep]`
  * Step in. Resume the program until next breakable point.
* `s[tep] <n>`
  * Step in, resume the program at `<n>`th breakable point.
```
#### 変数のn、コマンドのn
- 変数`number`を`n`に書き換えてその中身を知りたい時、`n`を入力するとコマンドの`n`（next）コマンドが優先されて変数の中身を表示させることができない。そんな時は、`p`コマンドを使用する。
```shell
[12, 19] in fizzbuzz.rb
    12|     puts number
    13|   end
    14| end
    15| 
    16| (1..20).each do |n|
=>  17|   binding.break
    18|   fizzbuzz(n)
    19| end
=>#0	block {|n=1|} in <main> at fizzbuzz.rb:17
  #1	[C] Range#each at fizzbuzz.rb:16
  # and 1 frames (use `bt' command for all frames)
(rdbg) p n    # command
=> 1 # pコマンドのおかげで変数nの中身が表示
```
#### list を入力
- 今、止まっている場所を教えてくれる。


---


## ✍🏻 感想
### ✅ おもなコマンドは押さえられた......つもり
debug.gem で使用できるおもなコマンドは一通り理解したつもりです。あとはプラクティスの課題で実践あるのみですね。次回は VSCode上でのデバッガを復習します。


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2 hours 00 min
- Total: 1144 hours 13 min
