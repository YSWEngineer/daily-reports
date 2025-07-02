# 2025/07/02(水)
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
- グループコーチング当日までブラッシュアップを行う

### プラクティス『プログラムの修正（リバーシ編）』
- チェリー本：第9章『例外処理を理解する』、第11章『パターンマッチを理解する』
    

---


## 💡 本日の学び・気付き
### 復習：rubygems（debug.gem）の使い方
#### VSCode 上でデバッガを使用する
- あるエクステンション（拡張機能）をインストールすると VSCode 上でデバッガを使用できるようになる。それが VSCode rdbg Ruby Debugger。

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBOVA2QXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--5e4e1f4a513e694cd4cb4e886089936595893659/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202025-07-02%2017.47.09.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBOVA2QXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--5e4e1f4a513e694cd4cb4e886089936595893659/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202025-07-02%2017.47.09.png" width="2730" height="974" alt="スクリーンショット 2025-07-02 17.47.09.png"></a>

- 行番号の赤い丸をクリックすると、その行が**ブレークポイント**となり、`binding.break`の代わりになってくれる。
  - **ブレークポイント**：プログラムの実行を「一時停止」させ、その時点で変数の中身や処理の流れを確認できる仕組みのこと。
- 上部にあるボタンをクリックすると`step`や`continue`などの操作が簡単にできる。もちろん、**DEBUG CONSOLE** からコマンドを入力することも可能。
- 左の欄に注目すると、**VARIABLES** で渡された引数を簡単にわかることもできれば、**CALL STACK** でどのような順番でメソッドが呼ばれているかもわかる。

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBOWI2QXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--8073e8c5383cc6f0092e16512e03087eac27525d/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202025-07-02%2018.14.33.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBOWI2QXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--8073e8c5383cc6f0092e16512e03087eac27525d/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202025-07-02%2018.14.33.png" width="2874" height="1284" alt="スクリーンショット 2025-07-02 18.14.33.png"></a>

##### VSCode rdbg Ruby Debugger のボタン
- `Continue`：次のブレークポイントまで一気に実行
- `Step Into`：メソッドの呼び出しの中まで入り、内部を1行ずつ詳しく追いかける。`step`の代わりになる。
- `Step Over`：プログラムを行単位で追いかけるときの操作の一つ。今いる行にメソッドの呼び出しがあっても、その内部には入らずに一気に実行する。`Continue`の代わりになる。
- `Step Out`：メソッドの処理をすぐに抜けて（メソッドの処理を終えて次のところで止まって）くれる。`finish`の代わりになる。
- `Stop`：デバッグをやめたい時に押すボタン。


---


## ✍🏻 感想
### ✅ 今のところは順調！
久し振りに VSCode のデバッガを使ってみましたが、ターミナルに比べて操作がずっと簡単ですね。たまに挙動が不自然になる点は気にはなりますが......個人的には、ターミナルでのデバッグをメインにしつつも、VSCode のデバッガも自在に使いこなせるようになりたいです。あとは実践あるのみ！

次回はチェリー本の第9章・第11章を復習してから、課題に取り組みます。


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2 hours 45 min
- Total: 1146 hours 58 min
