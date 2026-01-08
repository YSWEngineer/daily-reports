# 2026/01/08(木)
## 📚 プラクティス『🛠️💻 lsコマンドを作る2』

<details><summary>🎯 学習の狙い</summary>

- 標準出力について学ぶ
- 標準ライブラリの使い方を学ぶ
- Enumeratorには、each以外にも便利なメソッドがあることを学ぶ
- RailsじゃないRubyプログラミングを学ぶ
- メソッド分割を学ぶ
- わかりやすい変数名・メソッド名を学ぶ
- 大きな問題を分割する力を学ぶ
</details>

<details><summary>📌 要件（Docs：lsコマンドを作る 参照）</summary>

- [x] `-a`オプションを付けたとき、`.`で始まる隠しファイルも表示対象にする
- [x] ⚠️ 注意事項：`..`は表示されなくてもよい
- [x] そのまま実行すると、今いるフォルダ（カレントディレクトリ）の中身を表示する
- [x] `gem`は使わずに Ruby の標準ライブラリだけで作ること
- [x] 完成したコードは GitHub の Pull Request として提出すること
- [x] `rubocop-fjord`でデバッグを実行し、全てパスさせること
- [x] 表示は横に最大3列になるようにレイアウトすること
  - 3, 6, 9, 12のように3の倍数の件数だけでなく、最後の列に空欄ができるケースの結果も載せる
  - 「3列から5列に仕様変更してください」または「3列から100列に変えてください」とあとから言われても必要最小限の変更で対応できるようなロジックにしておくこと
</details>

<details><summary>📍 処理の流れ ※ 随時、追加・変更あり</summary>

**1. オプションの有無を判定**

**2. ファイル一覧取得**

**3. 出力するファイルを選別（隠しファイルを含む or 含まない）**

**4. 表示するための整形**

**5. 1 〜 4 を踏まえた上での出力**
</details>

<details><summary> 🧩 タスクばらし ※ 随時、追加・変更あり</summary>

- [x] タスク1：前提の整理
  - [x] `ls`コマンド、`-a`オプションについて確認

- [x] タスク2：`-a`オプションを受け取れる状態にする
  - [x] `OptionParser`を使用して引数を確認する
  - [x] `-a`オプションを含む処理 / 含まない処理を分けて考える（条件分岐🤔）

- [x] タスク3：ディレクトリの中身を取得

- [x] タスク4：隠しファイルの扱いを決める
  - [x] `-a`オプションが付いているなら`.`から始まるファイルを表示させる
  - [x] `-a`オプションが付いていないなら隠しファイルは表示させない

- [x] タスク5：レイアウトの調整
  - [x] 『lsコマンドを作る1』で作成したレイアウトの処理をそのまま使用🤔
  - [x] `-a`オプションを使ったときに隠しファイルが表示されるようにする

- [x] タスク6：rubocop-fjord に通す

- [x] タスク7：提出
  - [x] 作成した lsコマンドを Pull Request として提出
  - [x] 提出物にlsコマンドの実行結果とOS標準（macなど自分の使ってるOS）のlsコマンドをのスクリーンショットを併記して貼る
  - [x] rubocop-fjord のチェックが全てパスした画面をスクショして添付
</details>


---


## 🧑🏻‍💻 本日の取り組み
### 📚 プラクティス『🛠️💻 lsコマンドを作る2』 
- 模範解答を読み解く


---


## ⏭️ 次回
### 📚 プラクティス『lsコマンドを作る3』
- プラクティスの内容を確認から着手する


---


### 💡 本日の学び・気付き
<div class="message warning">
    <p>warning：プラクティス『lsコマンドを作る2』の模範解答を載せています。未修了の方は決して開かず、スルーしてください！</p>
</div>

<details><summary> 『🛠️💻 lsコマンドを作る2』の模範解答を読み解く （⚠️ ネタバレに注意）</summary>

今回は`-a`オプションの実装部分を中心に読み解く。
```ruby
#!/usr/bin/env ruby
# frozen_string_literal: true

require 'optparse'

def main
  file_list = make_list
  return if file_list.size.zero?

  display(file_list)
end

def make_list
  options = ARGV.getopts('a')
  Dir.glob('*', options['a'] ? File::FNM_DOTMATCH : 0).sort
end

def display(file_list)
  display_width = `tput cols`.to_i

  max_columns = 3
  longest_name_size = file_list.max_by(&:size).size
  minus_columns = (0...max_columns).find { longest_name_size < display_width / (max_columns - _1) } || max_columns - 1
  columns_number = max_columns - minus_columns

  columns_width = display_width / columns_number

  vertical = (file_list.size / columns_number.to_f).ceil

  slice = file_list.map { |d| d.ljust(columns_width) }.each_slice(vertical).to_a

  slice.map { |element| element.values_at(0...vertical) }.transpose.each { |display| puts display.join('') }
end

main
```
### 宣言・設定
```ruby
#!/usr/bin/env ruby
```
- このファイルを Ruby で実行するための宣言。
```ruby
# frozen_string_literal: true
```
- 文字列リテラルを変更不可（`frozen`）にする設定。

### ライブラリの読み込み
```ruby
require 'optparse'
```
- コマンドライン引数（今回の場合は`-a`オプション）を扱うためのライブラリ。
- 後述の`ARGV.getopts('a')`を使用するために必要。
- `ls`のオプション機能を実装するための準備。

### mainメソッド（処理の入り口）
```ruby
def main
```
- プログラム全体の処理をまとめるメソッド。
- 「このプログラムはここから処理が始まる」と読み手にわかりやすくする役割。

```ruby
file_list = make_list
```
- `make_list`メソッドを呼び出し、ファイル一覧を配列をして取得。
- 取得した配列を`file_list`に代入。

```ruby
return if file_list.size.zero?
```
- もしファイルが1つもなければ処理を終了する。
- `size.zero?`：「配列の要素数が`0`か？」を判定している......🤔

```ruby
display(file_list)
```
- ファイル一覧を表示するメソッドに渡す。
- ファイルの「取得」と「表示」を別々にしている......🤔

### make_listメソッド（ファイル一覧を作成）
```ruby
def make_list
```
- ファイル一覧を作成するためのメソッド。

```ruby
options = ARGV.getopts('a')
```
- `ARGV`：コマンドライン引数の配列。
- `getopts('a')`：`-a`オプションが指定されたかを調べる。

```ruby
Dir.glob('*', options['a'] ? File::FNM_DOTMATCH : 0 ).sort
```
- `options['a'] ? A : B`
  - **三項演算子**。
  - 「`-a`オプションがあれば `A`、なければ`B`」
- `File::FNM_DOTMATCH`
  - `.git`などの**隠しファイル**も含める。
- `Dir.glob('*', flags)`
  - `*`：カレントディレクトリのファイル一覧。
  - `flags`
    - `File::FNM_DOTMATCH`→ 隠しファイルを含む。
    - `0` → 隠しファイルを含まない。
- `sort`
  - ファイル名をアルファベット順に並べ替える。

言語化すると、
> 「`-a`オプションが指定されていれば隠しファイルを含め、`-a`オプションが指定されていなければ通常のファイルだけを取得し、それらをアルファベット順に並び替える」
</details>


---


## ✍🏻 感想
### 🙌🏻 『lsコマンドを作る2』修了！
メンターさんから OK をいただきました！
とても嬉しいです🥹✨

今回は、恒例となっている模範解答の読み解きを行いました。
分からない箇所はその都度調べ、言語化しながら、一行ずつ丁寧に考えて取り組みました。

次回は`-r`オプションを実装する『lsコマンドを作る3』に進みます。


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3 hours 23 min
- Total: 1463 hours 32 min
