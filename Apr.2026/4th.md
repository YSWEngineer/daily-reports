# 2026/04/04(土)
## 🧑🏻‍💻 本日の取り組み
### 📚 プラクティス『🛠️💻 wcコマンドを作る』 
- オプション -l / -w / -c に対応する


---


## ⏭️ 次回
- 自作 ls.rb との連携を確認する


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
- [x] `-l`のみ → 行数だけ表示
- [x] `-w`のみ → 単語数だけ表示
- [x] `-c`のみ → バイト数だけ表示
- [x] `-lw` / `-wc` / `-lc` → 指定した二つを表示
- [x] `-lwc` → 全部表示（オプションなしと同じ）

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
- [x] Step5：オプション -l / -w / -c に対応する
  - [x] オプションの指定に応じて、表示する列を切り替える。各組み合わせ（`-lw`や`-wc`など）にも対応する
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
### Step5：オプション -l / -w / -c に対応する
#### エラーを確認する
オプション`-l`, `-w`, `-c`がまだ対応されていない状態で,
たとえば`-lw`を入力すると以下のエラー内容が表示される。
```shell
~/wc_practice % ruby wc.rb -lw 1.txt
Traceback (most recent call last):
        3: from wc.rb:221:in `<main>'
        2: from wc.rb:221:in `each'
        1: from wc.rb:222:in `block in <main>'
wc.rb:222:in `read': No such file or directory @ rb_sysopen - -lw (Errno::ENOENT)
```
```
No such file or directory @ rb_sysopen - -lw
```
日本語にすると → `-lw`という名前のファイルやディレクトリは見つかりません
つまり、`-lw`がオプションではなく、ファイル名として扱われている。
```ruby
ARGV.each do |filename|
  content = File.read(filename)  # -lwをファイル名として読み込もうとする
end
```

#### ARGVの中身をファイルとオプションに分ける
```ruby
ARGV = ["-lw", "1.txt"]
  ↓ 分ける
オプション = ["-lw"]
ファイル名 = ["1.txt"]
```
オプションとファイル名の違いは`-`があるかないか。
##### partitionメソッド
`partition`メソッドは、条件によって配列を2つに分けるメソッド。
```ruby
["-lw", "1.txt"].partition { |arg| arg.start_with?("-") }
#=> [["-lw"], ["1.txt"]]
      ↑オプション  ↑ファイル名
```
|   |意味   |
|---|---|
|partiton   |配列を2つに分けるメソッド   |
|arg   |ARGVの各要素   |
|start_with("-")   |- で始まるか？   |

Ruby の`partition`は「ブロックの条件が合うもの（`true`）は**左**、合わないもの（`false`）は**右**」という決まりになっている。

参考リンク：[instance method Enumerable#partition](https://rurema.clear-code.com/4.0/method/Enumerable/i/partition.html)

実際に書いてみると......
```ruby
options, filenames = ARGV.partition { |arg| arg.start_with?("-") }
p options
p filenames

# 実行結果
~/wc_practice % ruby wc.rb -lw 1.txt
["-lw"]
["1.txt"]
```
↑オプションとファイル名が分けられていることが確認できた！
#### 復習：多重代入
2つ以上の値を同時に代入することを**多重代入**という。
```ruby
# 配列を使って多重代入する
a, b = [1, 2]
a #=> 1
b #=> 2
```

#### optionsの中に-l, -w, -cが含まれているか判断する
```
["-lw"] の中に "l" が含まれているか？ → true → 行数を表示する
["-lw"] の中に "w" が含まれているか？ → true → 単語数を表示する
["-lw"] の中に "c" が含まれているか？ → false → バイト数は表示しない
```
`options`は配列なので、**文字列に変換**してから`include?`メソッドで`"l"`, `"w"`, `"c"`それぞれが含まれているか確認する。
```ruby
options.join  #=> "-lw"（配列を文字列に変換）
"-lw".include?("l")  #=> true
"-lw".include?("w")  #=> true
"-lw".include?("c")  #=> false
```

試してみると......
```ruby
options, filenames = ARGV.partition { |arg| arg.start_with?("-") }
option_str = options.join
p option_str
p option_str.include?("l")
p option_str.include?("w")
p option_str.include?("c")

# 実行結果
~/wc_practice % ruby wc.rb -lw 1.txt
"-lw"
true
true
false
```
↑確認できた！
#### 復習：joinメソッドとinclude?メソッド
`join`メソッド：配列を文字列に変換するメソッド。
```ruby
# 基本の使い方
["-lw", "-c"].join  #=> "-lw-c"（区切りなし）
["-lw", "-c"].join(" ")  #=> "-lw -c"（スペース区切り）
["-lw", "-c"].join(",")  #=> "-lw,-c"（カンマ区切り）

# 今回の使い方
options = ["-lw"]
options.join  #=> "-lw"
```
`include?`メソッド：文字列や配列に特定の値が含まれているか確認するメソッド。
```ruby
# 文字列に使う
"-lw".include?("l")  #=> true（文字列"l"が含まれている）
"-lw".include?("w")  #=> true（文字列"w"が含まれている）
"-lw".include?("c")  #=> false（文字列"c"が含まれていない）

# 配列に使う
["1.txt", "2.txt"].include?("1.txt")  #=> true
["1.txt", "2.txt"].include?("3.txt")  #=> false
```
`?`で終わるので**述語メソッド**。`true`または`false`を返す。

|メソッド   |対象   |返すもの   |使いどころ   |
|---|---|---|---|
|join   |配列   |文字列   |配列を1つの文字列にまとめたいとき   |
|include?   |文字列・配列   |true / false   |特定の値が含まれているか確認したいとき   |

#### オプションの指定によって表示する列を切り替える
```
-lのとき → 行数だけ表示
-wのとき → 単語数だけ表示
-cのとき → バイト数だけ表示
-lwのとき → 行数と単語数を表示
-lcのとき → 行数とバイト数を表示
-wcのとき → 単語数とバイト数を表示
-lwcのとき → 全部表示
オプションなしのとき → 全部表示
```

##### 今のコードの表示部分
自分が書いたコードは今はオプション関係なく全部表示している。
```ruby
print lines.to_s.rjust(8)  #=> 常に行数を表示
print words.to_s.rjust(8)  #=> 常に単語数を表示
print bytes.to_s.rjust(8)  #=> 常にバイト数を表示
```

##### 「表示する・しない」を条件で切り替える
```ruby
# 行数：オプションなし、または -l が含まれているときに表示
print lines.to_s.rjust(8) if option_str.empty? || option_str.include?("l")

# 単語数：オプションなし、または -w が含まれているときに表示
print words.to_s.rjust(8) if option_str.empty? || option_str.include?("w")

# バイト数：オプションなし、または -c が含まれているときに表示
print bytes.to_s.rjust(8) if option_str.empty?  || option_str.include?("c")
```

##### 具体的な動きを確認する
```shell
% ruby wc.rb 1.txt   option_str = ""
→ empty? = true → 全部表示

% ruby wc.rb -l 1.txt  option_str = "-l"
→ include?("l") = true → 行数を表示
→ include?("w") = false → 単語数は表示しない
→ include?("c") = false → バイト数は表示しない

% ruby wc.rb -lw 1.txt  option_str = "-lw"
→ include?("l") = true → 行数を表示
→ include?("w") = true → 単語数を表示
→ include?("c") = false → バイト数は表示しない
```

#### 完成したコード
<details><summary> ⚠️ 解答に近い内容のため折りたたんでいます（閲覧注意）</summary>

```ruby
# frozen_string_literal: true

# !/usr/bin/env ruby

options, filenames = ARGV.partition { |arg| arg.start_with?("-") }
option_str = options.join

total_lines = 0
total_words = 0
total_bytes = 0

if filenames.empty?
  content = $stdin.read
  lines = content.lines.count
  words = content.split.size
  bytes = content.bytesize

  print lines.to_s.rjust(8) if option_str.empty? || option_str.include?("l")
  print words.to_s.rjust(8) if option_str.empty? || option_str.include?("w")
  print bytes.to_s.rjust(8) if option_str.empty? || option_str.include?("c")
  print "\n"
else
  filenames.each do |filename|
    content = File.read(filename)
    lines = content.lines.count
    total_lines += lines

    words = content.split.size
    total_words += words

    bytes = content.bytesize
    total_bytes += bytes

    print lines.to_s.rjust(8) if option_str.empty? || option_str.include?("l")
    print words.to_s.rjust(8) if option_str.empty? || option_str.include?("w")
    print bytes.to_s.rjust(8) if option_str.empty? || option_str.include?("c")
    print " #{filename}"
    print "\n"
  end

  if filenames.size > 1
    print total_lines.to_s.rjust(8) if option_str.empty? || option_str.include?("l")
    print total_words.to_s.rjust(8) if option_str.empty? || option_str.include?("w")
    print total_bytes.to_s.rjust(8) if option_str.empty? || option_str.include?("c")
    print " total"
    print "\n"
  end
end
```
### 各パターンの確認
```shell
# オプションなし
~/wc_practice % ruby wc.rb 1.txt
       3       9      45 1.txt
~/wc_practice % wc 1.txt
       3       9      45 1.txt

# 行数だけ
~/wc_practice % ruby wc.rb -l 1.txt
       3 1.txt
~/wc_practice % wc -l 1.txt 
       3 1.txt

# 単語数だけ
~/wc_practice % ruby wc.rb -w 1.txt 
       9 1.txt
~/wc_practice % wc -w 1.txt 
       9 1.txt

# バイト数だけ
~/wc_practice % ruby wc.rb -c 1.txt 
      45 1.txt
~/wc_practice % wc -c 1.txt
      45 1.txt

# 行数と単語数
~/wc_practice % ruby wc.rb -lw 1.txt 
       3       9 1.txt
~/wc_practice % wc -lw 1.txt 
       3       9 1.txt

# 行数とバイト数
~/wc_practice % ruby wc.rb -lc 1.txt 
       3      45 1.txt
~/wc_practice % wc -lc 1.txt 
       3      45 1.txt

# 単語数とバイト数
~/wc_practice % ruby wc.rb -wc 1.txt 
       9      45 1.txt
~/wc_practice % wc -wc 1.txt 
       9      45 1.txt

# 全部
~/wc_practice % ruby wc.rb -lwc 1.txt 
       3       9      45 1.txt
~/wc_practice % wc -lwc 1.txt 
       3       9      45 1.txt
```
### パイプとの組み合わせ確認
```shell
# オプションなし
~/wc_practice % cat 1.txt | ruby wc.rb
       3       9      45
~/wc_practice % cat 1.txt | wc        
       3       9      45

# 行数だけ
~/wc_practice % cat 1.txt | ruby wc.rb -l
       3
~/wc_practice % cat 1.txt | wc -l        
       3

# 単語数だけ
~/wc_practice % cat 1.txt | ruby wc.rb -w
       9
~/wc_practice % cat 1.txt | wc -w        
       9

# バイト数だけ
~/wc_practice % cat 1.txt | ruby wc.rb -c
      45
~/wc_practice % cat 1.txt | wc -c        
      45

# 行数と単語数
~/wc_practice % cat 1.txt | ruby wc.rb -lw
       3       9
~/wc_practice % cat 1.txt | wc -lw        
       3       9

# 行数とバイト数
~/wc_practice % cat 1.txt | ruby wc.rb -lc
       3      45
~/wc_practice % cat 1.txt | wc -lc        
       3      45

# 単語数とバイト数
~/wc_practice % cat 1.txt | ruby wc.rb -wc
       9      45
~/wc_practice % cat 1.txt | wc -wc        
       9      45

# 全部
~/wc_practice % cat 1.txt | ruby wc.rb -lwc
       3       9      45
~/wc_practice % cat 1.txt | wc -lwc        
       3       9      45
```
全パターン、本物の`wc`コマンドと一致している😭🙌🏻

</details>

---


## ✍🏻 感想
### 🤔 基礎って本当に大事！
各オプション`-l`, `-w`, `-c`に対応できるようになりました。前回の感想にも書きましたが、「やりたいことを日本語で書き → 必要なコードとして書いていき → 繋ぎ合わせる」という流れで実装していくのが自分には合っていると感じています。

コードを書きながら、改めて基礎の大切さを実感しました。チェリー本や Rubyリファレンスマニュアルを何度も確認しましたが、基礎知識が「スッ」と頭に浮かばないのは悔しかったです。これについては繰り返し演習問題を解いて経験値を積んでいくしかありませんね。

今回のプラクティスのゴールテープがうっすらと見えてきました。このまま行こう！Yoshiwo、お前ならできる🏋🏻


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 6 hours 31 min
- Total: 1541 hours 51 min
