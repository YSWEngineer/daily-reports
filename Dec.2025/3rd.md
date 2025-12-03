# 2025/12/03(水)
## 📚 プラクティス『lsコマンドを作る1』

<details><summary>🎯 学習の狙い</summary>

- 標準出力について学ぶ
- 標準ライブラリの使い方を学ぶ
- Enumeratorには、each以外に便利なメソッドがあることを学ぶ
- RailsじゃないRubyプログラミングを学ぶ
- メソッド分割を学ぶ
- わかりやすい変数名メソッド名を学ぶ
- 大きな問題を分割する力を学ぶ
</details>

<details><summary>📌 要件（Docs：lsコマンドを作る 参照）</summary>

- [x] オプション（`-a`や`-r`など）を付けず、且つ引数（フォルダのパス）も指定せずに実行する
- [x] そのまま実行すると、今いるフォルダ（カレントディレクトリ）の中身を表示する
- [x] `gem`は使わずに Ruby の標準ライブラリだけで作ること
- [x] 完成したコードは GitHub の Pull Request として提出すること
- [x] `rubocop-fjord`でデバッグを実行し、全てパスさせること
- [x] 2つ以上のメソッドを自分で定義すること
- [x] 表示は横に最大3列になるようにレイアウトすること
  - 3, 6, 9, 12のように3の倍数の件数だけでなく、最後の列に空欄ができるケースの結果も載せる
  - 「3列から5列に仕様変更してください」または「3列から100列に変えてください」とあとから言われても必要最小限の変更で対応できるようなロジックにしておくこと
</details>

<details><summary>📑 全体の設計 （⚠️ ネタバレに注意）</summary>

### 1. ファイルの取得（ソート含む）
- 入力：検索パターン
- 処理：`Dir.glob`で指定パターンに合うファイルやディレクトリを取得し、並び替え
- 出力：ファイル・ディレクトリ一覧（配列でまとめたもの）

### 2. 行数の計算
- 入力：ファイル（要素）を配列でまとめたものと列数
- 処理：`行数 = (要素の数 ÷ 列数).ceil`で余りを切り上げる
- 出力：行数（Integer = 整数）

### 3. 要素一つ一つを縦に配置
- 入力：ファイル（要素）を配列でまとめたもの、行数・列数
- 処理：①行ごとの配列を作る　②各列に要素を縦に配置　③インデックス計算：`index = row + column * rows`
- 出力：縦詰めに並んだ配列

### 4. 配置を整える
- 入力：縦詰めに並んだ要素
- 処理：タブ文字（`join("\t")`）を使用して見やすく整える
- 出力：整えられた文字列
</details>

<details><summary> 🧩 タスクばらし ※ 随時、追加・変更あり</summary>

- [x] タスク1：開発の準備（テストフォルダ）
  - [x] ToDo：作業用フォルダを用意し、その中にダミーファイルをいくつか置く
  - [x] 作業時間： 30分
  - [x] 終了条件：テストフォルダにファイルがある

- [x] タスク2：全体設計
  - [x] ToDo：「主要な処理」を列挙する
  - [x] 作業時間：60分
  - [x] 終了条件：主要な処理（要件）を一つずつ列挙すること

- [x] タスク3：ファイルの取得とソート（並び替え）
  - [x] ToDo：`.`や`..`から始まるファイルや隠しファイルは出力させないようにする
  - [x] 作業時間：60分
  - [x] 終了条件：期待している並び順になっていること

- [x] タスク4：行数・列数のロジックを考える（余りの切り上げを用いる）
  - [x] ToDo：先ずは列数を3列に決め、行数が切り上げになること
  - [x] 作業時間：60分
  - [x] 終了条件：列数や要素の数を変更しても期待どおりになっていること

- [x] タスク5：縦詰めにロジックをメソッド化
  - [x] ToDo：縦詰めに変換するメソッドを実装し、期待どおりなっていること
  - [x] 作業時間：90分
  - [x] 終了条件：縦詰めの出力が期待どおりであること

- [x] タスク6：列幅を揃える
  - [x] ToDo：タブ文字を用いて文字列同志の幅を整える
  - [x] 作業時間：90分
  - [x] 終了条件：実際に見て読みやすくなっていること

- [x] タスク7：2つ以上のメソッドを自分で定義する
  - [x] ToDo：「何をやるか」に名前を付けて、後で呼び出せるようにする
  - [x] 作業時間：240分
  - [x] 終了条件：メソッドを2つ定義すること

- [x] タスク8：rubocop-fjord に通す
  - [x] ToDo：rubocop-fjord 通して出力されたエラーを一つずつ直していく
  - [x] 作業時間：数時間？エラーの内容によりけり
  - [x] 終了条件：rubocop-fjord の警告・エラーが発生していないこと

- [x] タスク9：提出
  - [x] ToDo：作成した lsコマンドを Pull Request として提出
  - [x] ToDo：提出物にlsコマンドの実行結果とOS標準（macなど自分の使ってるOS）のlsコマンドをのスクリーンショットを併記して貼る
  - [x] ToDo：rubocop-fjord のチェックが全てパスした画面をスクショして添付
  - [x] 作業時間：60分
  - [x] 終了条件：メンターさんに課題を提出すること

- [x] タスク10：一歩前へ
  - [x] 模範解答を読み解く！
</details>


---


## 🧑🏻‍💻 本日の取り組み
### 📚 プラクティス『🛠️💻 lsコマンドを作る1』 
- 模範解答を読み解く


---


## ⏭️ 次回
### 📚 プラクティス『🛠️💻 lsコマンドを作る2』
- 着手

### 🎄📆 フィヨルドブートキャンプ Advent Calendar 2025
- 投稿当日までブラッシュアップ


---


## 💡 本日の学び・気付き
<div class="message warning">
    <p>warning：プラクティス『lsコマンドを作る1』の模範解答を載せています。未修了の方は決して開かず、スルーしてください！</p>
</div>


<details><summary> 『🛠️💻 lsコマンドを作る1』の模範解答を読み解く （⚠️ ネタバレに注意）</summary>

```ruby
#!/usr/bin/env ruby
# frozen_string_literal: true

def make_list
  Dir.glob('*').sort
end

def display_width
  `tput cols`
end

def columns_number
  max_columns = 3

  longest_name_size = make_list.max_by(&:size).size

  minus_columns = (0...max_columns).find { longest_name_size < display_width.to_i / (max_columns - _1) } || max_columns - 1
  max_columns - minus_columns
end

def columns_width
  display_width.to_i / columns_number
end

def vertical
  n = make_list.size
  (n / columns_number.to_f).ceil
end

def display_result
  left_alignment = make_list.map { |d| d.ljust(columns_width) }
  slice = left_alignment.each_slice(vertical).to_a
  add_nil = slice.map { |element| element.values_at(0...vertical) }
  add_nil.transpose.each { |display| puts display.join('') }
end

display_result
```

### 1. ファイル全体の先頭
```ruby
#!/usr/bin/env ruby
```
- このファイルをターミナルから直接実行したときに、Ruby で実行されることを指定している。
```ruby
# frozen_string_literal: true
```
- 文字列リテラル（`""`で書いた文字列）が変更不可になる設定。

### 2. ファイル一覧を作るメソッド
```ruby
def make_list
  Dir.glob('*').sort
end
```
- メソッド名`make_list`：「一覧を作る」
- 役割：カレントディレクトリのファイルやフォルダを全て取得して、アルファベット順に並べる。
- 動作：`Dir.glob('*')`はカレントディレクトリのファイル・フォルダ全てを配列で返す。
- `sort`メソッド：アルファベット順に並べ替え。
- 返り値：並べ替え済みのファイル名の配列。

### 3. ターミナルの幅を取得するメソッド
```ruby
def display_width
  `tput cols`
end
```
- メソッド名`display_width`：「表示幅」
- 役割：ターミナルの横幅を取得する。
- 動作：シェルコマンドを実行。
- `tput cols`：ターミナルの横幅を取得する。
- ``（バッククォート）：Ruby からシェルと実行する......🤔（よく分かっていない）

### 4. 列の数を決めるメソッド
```ruby
def columns_number
  max_columns = 3

  longest_name_size = make_list.max_by(&:size).size

  minus_columns = (0...max_columns).find { longest_name_size < display_width.to_i / (max_columns - _1) } || max_columns - 1
  max_columns - minus_columns
end
```
- メソッド名`columns_number`：「列の数」
- 役割：ターミナルの幅とファイル名の長さから、表示する列の数を決定する。
#### 中身を分解して考える
① `max_columnx = 3`
→最大で 3列に分ける。
② `longest_name_size = make_list.max_by(&: size).size`
→最も長い名前のファイル名の文字数を取得
③ `(0...max_columns).find { longest_name_size < display_width.to_i / (max_columns - _1) } || max_columns - 1`
→ループで、ファイル名が列幅に収まるか確認
→`_1`は**番号指定パラメータ**（numbered parameter）というもので、Ruby2.7 で導入された。番号指定パラメータを使うとブロックパラメータを使う分かりに、`_1`から`_9`までの番号をパラメータの順で使うことができる。
④ `max_columns - minus_columns`
→実際に使う列数を計算して返す。

### 5. 列ごとの幅を計算するメソッド
```ruby
def columns_width
  display_width.to_i / columns_number
end
```
- メソッド名`columns_width`：「列の幅」
- 役割：1列あたりに割り当てる幅（文字数）を計算。
- `display_width.to_i`：ターミナルの列数を整数に変換。
- `/ columns_number`：列数で割る。
- 返り値：1列の幅（文字列）。

### 6. 縦方向の行数を計算するメソッド
```ruby
def vertical
  n = make_list.size
  ( n / columns_number.to_f).ceil
end
```
- メソッド名`vertical`：「縦の行数」。vertical = 垂直、縦方向。
- 役割：ターミナルに収めるため、1列に入れる行数を計算。
- `n = make_list.size`：ファイルの総数。
- `(n / columns_number.to_f).ceil`：列数で割った結果を切り上げ、1列に入る行数を決める。

### 7. 実際に表示するメソッド
```ruby
def display_result
  left_alignment = make_list.map { |d| d.ljust(columns_width) }
  slice = left_alignment.each_slice(vertical).to_a
  add_nil = slice.map { |element| element.values_at(0...vertical) }
  add_nil.transpose.each { |display| puts display.join('') }
end
```
- メソッド名`desplay_result`：「結果を表示」
- 役割：ファイル名を列ごとに整列させて表示。
#### 中身を分解
① `left_alignment = make_list.map { |d| d.ljust(columns_width) }`
→一列分の幅に合わせて、左寄せで文字列を整形。
② `slice = left_alignment.each_slice(vertical).to_a`
→一列分の要素をまとめる。
③ `add_nil = slice.map { |element| element.values_at(0...vertical) }`
→行数に収まらない場合、空の要素（`nil`）を充てる。だから`add_nil`と命名されている。
→`values_at(0...vertical)`：`vertical = 3`なら、`0, 1,2`を指定し、足りない箇所には`nil`を入れる。
④ `add_nil.transpose.each { |display| puts display.join('') }`
→配列の行と列を入れ替える。
→`transpose`：配列の行と列を入れ替えるメソッド。

### 8. 最後に呼び出す
```ruby
display_result
```
- `display_result`メソッドを実行して、画面にファイル一覧を出力。
</details>


---


## ✍🏻 感想
### 模範解答、めっちゃ難しい......🫠
『lsコマンドを作る1』を修了したので、模範解答のコードを読み解く作業を行いました。メソッド化の仕方、メソッドの命名、メソッドの挙動、コードの型、英単語の意味合いなどを注視しながら一行ずつ言語化していったのですが、「**難しい**」の一言に尽きます。

全く理解できていない箇所も幾つかあり、「こういうふうに書くのか......いや、どうやって思いつくんだい！」と、終始セルフツッコミでした。

『lsコマンドを作る1』の取り組みは本日で終了です。
次回からは『lsコマンドを作る2』に進みます🏋🏻


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3 hours 08 min
- Total: 1435 hours 13 min
