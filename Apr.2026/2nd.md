# 2026/04/02(木)
## 🧑🏻‍💻 本日の取り組み
### 📚 プラクティス『🛠️💻 wcコマンドを作る』 
- 複数ファイルとtotal行に対応する


---


## ⏭️ 次回
- オプション -l / -w / -c に対応する


---


## 🗺️ 要件定義・処理の流れ・タスクばらし
<details><summary>📌 要件定義 ※ 随時、追加・変更あり</summary>

## 何を作るのか？（目的）
・ Unixコマンド`wc`を Ruby で再現するスクリプト（`wc.rb`）を作る
・テキストの「行数・単語数・バイト数」を集計して表示する

## 入力パターン（2種類に対応する）
### パターン1：ファイル指定
→ 引数にファイル名を渡す方法。ファイルが一つでも複数でも動く。
```shell
% ruby wc.rb 1.txt
% ruby wc.rb 1.txt 2.txt
```
### パターン2：パイプ（標準入力）
→ パイプで前のコマンドの出力を受け取る方法。
```shell
% ls -l | ruby wc.rb
% ruby ls.rb | ruby wc.rb
```

## オプション（6パターンすべてに対応する）
### 対応が必要なオプション一覧
- [x] オプションなし → 行数・単語数・バイト数をすべて表示
- [ ] `-l`のみ → 行数だけ表示
- [ ] `-w`のみ → 単語数だけ表示
- [ ] `-c`のみ → バイト数だけ表示
- [ ] `-lw` / `-wc` / `-lc` → 指定した二つを表示
- [ ] `-lwc` → 全部表示（オプションなしと同じ）

表示順は「行数 → 単語数 → バイト数」で固定（本物の`wc`と同じ挙動で）。
オプションの指定順は関係ない。 

## 複数ファイルのときの動き
### total行を追加する
- [x] ファイルが一つだけのときは、`total`行は不要
- [x] ファイルが二つ以上のときは、各ファイルの結果の下に`total`（合計）行を表示する
```shell
# ファイルが一つだけのとき
~/wc_practice % wc 1.txt      
       3       9      45 1.txt

# ファイルが二つ以上のとき
~/wc_practice % wc 1.txt 2.txt 
       3       9      45 1.txt
       4       7      43 2.txt
       7      16      88 total
```

## やらなくていいこと
### 対応不要な項目
❌ 日本語（マルチバイト文字）への対応は必須ではない
❌ 特殊な入力ケースへの対応は不要
❌ `gem`の使用は禁止（標準ライブラリのみ）
❌ クラス定義は不要（トップレベルに処理を書く）
</details>

<details><summary>📍 処理の流れ（フローチャート） ※ 随時、追加・変更あり</summary>

```
スタート
　│
　▼
① オプションを解析する
　　ARGVを見て、- で始まるものをオプション、それ以外をファイル名に分ける
　│
　▼
② ファイル名の引数はあるか？
　　├─ YES → ファイルを開いて内容を読み込む
　　└─ NO  → $stdin からパイプ入力を読み込む
　│
　▼（合流）
③ 行数・単語数・バイト数を数える
　　テキストから lines / words / bytes をそれぞれ集計する
　│
　▼
④ ファイルがまだ残っているか？（複数ファイルのとき）
　　├─ YES → ③に戻って次のファイルを処理する
　　└─ NO  → 次へ進む
　│
　▼
⑤ ファイルは2つ以上だったか？
　　├─ YES → total 行を追加する
　　└─ NO  → そのまま次へ
　│
　▼（合流）
⑥ オプションに応じて表示する列を決める
　　-l / -w / -c の指定がなければ行数・単語数・バイト数を全部表示
　│
　▼
⑦ 結果を画面に出力する
　│
　▼
終了
```
</details>

<details><summary> 🧩 タスクばらし ※ 随時、追加・変更あり</summary>

- [x] Step1：テスト用に作業場所を作成
- [x] Step2：1ファイルの行数・単語数・バイト数を表示する
  - [x] まずはオプションなし・1ファイルだけのシンプルな状態を動かす
```shell
% ruby wc.rb 1.txt
```
- [x] Step3：パイプ（標準入力）にも対応する
  - [x] ファイル名の引数がないとき、パイプで渡されたデータを`$stdin`から読み込むように切り替える
```shell
% cat 1.txt | ruby wc.rb
```
- [x] Step4：複数ファイルとtotal行に対応する
  - [x] ファイルを二つ以上渡したとき、各ファイルの結果を表示してから`total`（合計）行を追加する
```shell
% ruby wc.rb 1.txt 2.txt
```
- [ ] Step5：オプション -l / -w / -c に対応する
  - [ ] オプションの指定に応じて、表示する列を切り替える。各組み合わせ（`-lw`や`-wc`など）にも対応する
```shell
% ruby wc.rb -lw 1.txt
% ruby wc.rb -wc 1.txt
% ruby wc.rb -lwc 1.txt
```
- [ ] Step6：自作 ls.rb との連携を確認する
  - [ ] 自作の`ls.rb`の出力を`wc.rb`に渡して動く確認する
  - [ ] オプション付きでも動くか確認する
```shell
% ruby ls.rb | ruby wc.rb
% ruby ls.rb | ruby wc.rb -l
% ruby ls.rb | ruby wc.rb -w
% ruby ls.rb | ruby wc.rb -c
```
- [ ] Step7：rubocop-fjordを通す
  - [ ] コードのスタイルチェックを行い、警告が全て消えるまで修正する
- [ ] Step8：提出前の最終チェック
  - [ ] 全ての動作パターンをもう一度最初から通して確認する
  - [ ] 修正によって壊れた箇所がないかもチェックする
    - [ ] 1ファイル
    - [ ] 複数ファイル
    - [ ] パイプ入力
    - [ ] オプション単体
    - [ ] オプション組み合わせ
    - [ ] ls.rbとの連携
    - [ ] rubocop-fjordをパス
</details>


---


## 💡 本日の学び・気付き
### Step4：複数ファイルとtotal行に対応する
#### 考え方の流れ
① `ARGV`の中にファイルが何個あるか確認する
② ファイルの数だけ繰り返し処理をする → 各ファイルの行数・単語数・バイト数を数えて表示する
③ ファイルが2つ以上のときだけ`total`行を追加する → ここは分岐
#### イメージ
```
# ② 繰り返し処理
ARGV.each do |filename|
  # 各ファイルの処理
end

# ③ 分岐
if ARGV.size > 1
  # total行を表示する
end
```
#### 考え方の道筋
こういう順番で考えてみた......
```
「each の中で何をしたいか？」
  ↓
「各ファイルの中身を読み込みたい」
  ↓
「ファイルを読み込むには File.read を使う」
  ↓
「filename にファイル名が入っている」
  ↓
「File.read(filename) と書けばいい！」
```
#### eachの中に行数・単語数・バイト数を数えて表示するコードを書いてみる
```ruby
ARGV.each do |filename|
  content = File.read(filename)
  lines = content.lines.count
  words = content.split.size
  bytes = content.bytesize

  print lines.to_s.rjust(8)
  print words.to_s.rjust(8)
  print bytes.to_s.rjust(8)
  print " #{filename}"
  print "\n"
end

# 実行結果と本物のwcコマンド
~/wc_practice % ruby wc.rb 1.txt 2.txt
       3       9      45 1.txt
       4       7      43 2.txt

~/wc_practice % wc 1.txt 2.txt
       3       9      45 1.txt
       4       7      43 2.txt
       7      16      88 total
```
#### total行を追加する
`total`行には各ファイルの合計を表示する必要がある。
```
1.txt：3行・9単語・45バイト
2.txt：4行・7単語・43バイト
  ↓ 足し合わせる
total：7行・16単語・88バイト
```
#### 外で宣言し、中で足す
行数・単語数・バイト数の合計を表示するためには`each`メソッドの外で宣言し、`each`メソッドの中で足し合わせていく必要がある。
```ruby
total_lines = 0  # eachの「外」で初期値を宣言する

ARGV.each do |filename|
  lines = content.lines.count
  total_lines += lines  # eachの「中」で足し合わせる
end

# eachの「外」でtotalを表示する
```
#### 復習：なぜ外で宣言する必要があるのか？
結論：`each`の中だけで宣言すると、毎回リセットされてしまうから！
```ruby
# ❌ 中で宣言するとリセットされる
ARGV.each do |filename|
  total_lines = 0  # 毎回 0 にリセットされる
  total_lines += lines  # 結果は常に各ファイルの行数だけ（加算されない）
end

# ⭕️ 外で宣言すると値が積み上がる
total_lines = 0  # 最初は 0（初期値の宣言）
# 1回目：total_lines = 0 + 3 = 3
# 2回目：total_lines = 3 + 4 = 7  ← 値が積み上がっていく
```
まとめると......
- 外で宣言：値を保持するための箱を用意する
- 中で足す：繰り返すたびに箱に値を追加する
- 外で表示：全部終わったら箱の中身を表示する
#### 復習：演算子 "+="
`+=`は「今の値に足して代入する」という意味。
```ruby
total_lines += lines
# total_lines = total_lines + lines と同じ意味
```
#### total行を表示する条件を書いてみる
`total`行を表示する条件は......
```
ファイルが2つ以上のときだけ total行を表示する
```
↑この条件と、`total_lines`, `total_words`, `total_bytes`を使い`each`の後に追加してみる。
```ruby
# ファイルが2つ以上のとき total行を表示する
if ARGV.size > 1  # 配列ARGVの要素数（ファイルの数）が2つ以上なら以下の処理を行う
  print total_lines.to_s.rjust(8)
  print total_words.to_s.rjust(8)
  print total_bytes.to_s.rjust(8)
  print " total"
  print "\n"
end
```
#### Step3で書いたコードと合わせてみる
```ruby
total_lines = 0  # 合計行数の初期値
total_words = 0  # 合計単語数の初期値
total_bytes = 0  # 合計バイト数の初期値

if ARGV.empty?
  content = $stdin.read
  lines = content.lines.count
  words = content.split.size
  bytes = content.bytesize

  print lines.to_s.rjust(8)
  print words.to_s.rjust(8)
  print bytes.to_s.rjust(8)
  print "\n"
else
  ARGV.each do |filename|
    content = File.read(filename)
    lines = content.lines.count
    total_lines += lines

    words = content.split.size
    total_words += words

    bytes = content.bytesize
    total_bytes += bytes

    print lines.to_s.rjust(8)
    print words.to_s.rjust(8)
    print bytes.to_s.rjust(8)
    print " #{filename}"
    print "\n"
  end

  if ARGV.size > 1
    print total_lines.to_s.rjust(8)
    print total_words.to_s.rjust(8)
    print total_bytes.to_s.rjust(8)
    print " total"
    print "\n"
  end
end
```
#### 動作確認
```shell
# 自作のwcコマンド
~/wc_practice % ruby wc.rb 1.txt  # 1ファイル
       3       9      45 1.txt
~/wc_practice % ruby wc.rb 1.txt 2.txt  # 複数ファイル
       3       9      45 1.txt
       4       7      43 2.txt
       7      16      88 total
~/wc_practice % cat 1.txt | ruby wc.rb  # パイプ
       3       9      45

# 本物のwcコマンド
~/wc_practice % wc 1.txt 
       3       9      45 1.txt
~/wc_practice % wc 1.txt 2.txt
       3       9      45 1.txt
       4       7      43 2.txt
       7      16      88 total
~/wc_practice % cat 1.txt | wc        
       3       9      45
```
本物の`wc`コマンドと一致している！

---


## ✍🏻 感想
### 🤔 考え方の道筋を考える
複数ファイルと`total`行に対応するコードを書くために「**やりたいことを条件にする**」を意識しました。

- ① やりたいことを日本語で書く
- ② 必要な部品（メソッド）を探し
- ③ 部品を繋げる

時間はかかりましたが、以上の流れを意識することで「自然と読みやすいコードになるなぁ」と書いていて感じました。


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3 hours 52 min
- Total: 1535 hours 20 min
