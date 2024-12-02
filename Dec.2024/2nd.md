# 2024/12/02(月)
## プラクティス『プログラムの修正』

## 🧩 タスクばらし
- [x] 各参考ページを確認
- [x] 参考書籍を読む
- [ ] ソースコードを修正
- [ ] 課題提出


------------


## 🐾 スモールステップ
<details><summary>各参考ページを確認</summary>

- [x] [Docs：debug.gemの使い方を学ぶ](https://bootcamp.fjord.jp/pages/how-to-use-debug-gem)
   - [x] [rubygems (debug.gem)の使い方 - YouTube](https://www.youtube.com/watch?v=4r7-uN3RvNA)
   - [x] [byebugの良さを教えてください！ | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/questions/1162)
   - [x] [Ruby 3.1 の debug.gem を自慢したい - クックパッド開発者ブログ](https://techlife.cookpad.com/entry/2021/12/27/202133)
   - [x] [VS Codeでターミナルからの入力を伴うRubyプログラムをデバッグ実行する方法 - Qiita](https://qiita.com/jnchito/items/3254118d666ef1ea2923)
   - [x] [Railsをステップ実行する方法を学ぶ（VS CodeとRubyMine） | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/pages/how-to-debug-rails)


</details>


<details><summary>参考書籍を読む</summary>

- [x] コードが動かないので帰れません！新人プログラマーのためのエラーが怖くなくなる本
   - [x] 第1章 エラーはどうして怖いのか？
   - [x] 第2章 エラーの上手な読み方
   - [x] 第3章 不具合の原因を効率的に見つけるには？
   - [x] 第4章 ツールを活用してデバッグを楽にしよう
   - [x] 第5章 どうしても解決できない時は？
   - [x] 第6章 デバッグしやすいコードを書こう

</details>


<details><summary>ソースコードを修正</summary>

- [x] ソースコードを修正

</details>


<details><summary>課題提出</summary>

- [ ] 修正したソースコードを Pull Request としてアップ
- [ ] Pull Request した URL と Terminal での実行結果をメンターさんに提出

</details>


------------


## 🕺 プラクティス終了後の姿
- **エラーの無いバグの探し方がわかる**💡
- **さらにデバッグツールに親しむ**🫂


------------


## 🧑🏻‍💻 本日の取り組み
### プラクティス『プログラムの修正』
- ソースコードを修正


------------


## ⏭️ 次回
### プラクティス『プログラムの修正』
- ソースコードを修正


------------


## 💡 本日の学び・気付き
### プログラムの修正
**※ 以下、ネタバレが含まれています！**

<details><summary>⚠️ ネタバレ注意 修正後のプログラム </summary>

```ruby
# frozen_string_literal: true

# priceの価格を文字列から数値型に変更
DRINKS = [
  { name: 'コーヒー', price: 300 },
  { name: 'カフェラテ', price: 400 },
  { name: 'チャイ', price: 460 },
  { name: 'エスプレッソ', price: 340 },
  { name: '緑茶', price: 450 }
].freeze

# priceの価格を文字列から数値型に変更
FOODS = [
  { name: 'チーズケーキ', price: 470 },
  { name: 'アップルパイ', price: 520 },
  { name: 'ホットサンド', price: 410 }
].freeze

def take_order(menus)
  menus.each.with_index(1) do |menu, i|
    puts "(#{i})#{menu[:name]}: #{menu[:price]}円"
  end
  print '>'
  # 注文番号が1から始まるのに対して、配列のインデックスは0から始まってしまうため、変数order_numberから1を引く
  order_number = gets.to_i - 1
  # ユーザーが注文番号以外の番号を入力したときに、エラーメッセージではなく、適切なメッセージを返すようにする
  if order_number < 0 || order_number >= menus.length
    puts "無効な番号です。もう一度入力してください。"
    return nil
  end
  puts "#{menus[order_number][:name]}(#{menus[order_number][:price]}円)ですね。"
  order_number
end

puts 'bugカフェへようこそ！ご注文は？ 番号でどうぞ'
order1 = take_order(DRINKS)
# order1に注文番号以外の番号が入力された場合に強制終了させる
exit if order1.nil?

puts 'フードメニューはいかがですか?'
order2 = take_order(FOODS)
# order2に注文番号以外の番号が入力された場合に強制終了させる
exit if order2.nil?

# 定数DRINKSとFOODSの位置を整える
total = DRINKS[order1][:price] + FOODS[order2][:price]
puts "お会計は#{total}円になります。ありがとうございました！"
```



#### 1. DRINKS と FOODS の価格を文字列から整数型に変更
```ruby
DRINKS = [
  { name: 'コーヒー', price: 300 },
  { name: 'カフェラテ', price: 400 },
  { name: 'チャイ', price: 460 },
  { name: 'エスプレッソ', price: 340 },
  { name: '緑茶', price: 450 }
].freeze

FOODS = [
  { name: 'チーズケーキ', price: 470 },
  { name: 'アップルパイ', price: 520 },
  { name: 'ホットサンド', price: 410 }
].freeze
```
- `price`を文字列で定義すると、数値による計算ができない。シングルクォーテーションを外して価格を数値型に変更。

#### 2. Off-by-one Error を修正
```ruby
order_number = gets.to_i - 1
```
- 注文番号が`1`から始まるのに対して、配列のインデックスは`0`から始まってしまう。そのため、変数`order_number`から 1 を引くコードを書いた。

#### 3. 注文番号以外の番号を入力した時
```ruby
if order_number < 0 || order_number >= menus.size
  puts "無効な番号です。もう一度入力してください。"
  return nil
end
```
- ユーザーが注文番号以外の番号を入力した時に、適切なメッセージを返すようにした。

`if order_number < 0`
   - 変数`order_number`が0未満、つまりマイナスの値であるかどうかを確認。
   - 配列のインデックスは`0`から始まるから。例えば、配列の最初の要素は`menu[0]`。マイナスのインデックスは存在しないため無効。
   - 例えば、変数`order_number`が-1の場合、この条件は`ture`となり、無効な値であることを示す。

`order_number >= menus.size`
   - 変数`order_number`が配列の長さ以上であるかどうかを確認。
   - 配列の有効なインデックスは`0`から`menus.size -1`まで。`menus.size`は配列の要素の個数を取得する。
   - 例えば、変数`menus`に5つの要素がある場合、配列のインデックスは`0`から`4`まで。変数`order_number`が5以上の場合、この条件は`true`となり、無効な値であることを示す。
   - sizeメソッド（エイリアスメソッドはlength）を使うと**配列の長さ（要素の個数）を取得**できる。
      - **エイリアスメソッド**：Ruby には全く同じメソッドに複数の名前がついている場合がよくある。例えば、Stringクラスのlengthメソッドとsizeメソッドは、名前が異なるだけでどちらもまったく同じメソッドである。

`||`（論理演算子）
   - `||`は論理演算子で、どちらか一方の条件が`true`であれば全体として`true`となる。
   - 例えば、変数`order_number`が-1または`menus.size`以上であれば全体の条件は`true`になる。

例えば、変数`menus`が以下のような配列だったとする
```ruby
menus = [
  { name: 'コーヒー', price: 300 },
  { name: 'カフェラテ', price: 400 },
  { name: 'チャイ', price: 460 },
  { name: 'エスプレッソ', price: 340 },
  { name: '緑茶', price: 450 }
]
```
- 有効なインデックスの範囲：`0`から`4`（`menus.length - 1`）
- 無効になる変数`order_number`の例
   - `order_number`が`-1` => `order_number` < 0`が`true`
   - `order_number`が`5` => `order_number >= menus.size`が`true`

これで、変数`order_number`が有効な範囲外であればエラーメッセージを表示し、無効な値として処理することができる。

`puts "無効な番号です。もう一度入力してください。`
   - この行は、ユーザーが**注文番号にない無効な番号を入力した場合**に、エラーメッセージとして返すためのコード。

`return nil`
   - この行は、メソッドを終了させて`nil`を返すためのもの。
   - `return`：メソッドの処理が終わる。`reture`より後に書かれた行は実行されない。
   - `nil`：無効な値や何もないことを示す特別なオブジェクト。
   - 無効な番号が入力された場合、メソッドを終了させて`nil`を返すことで、後続の処理が続行されないようにする。

#### 4. 無効な注文番号が入力された場合にプログラムを終了させる
```ruby
exit if order1.nil?
exit if order2.nil?
```
`exit if order1.nil?`
- この行は、`order1`が`nil`である場合にプログラムを終了させるという意味。
- `exit`：Rubyプログラムを終了させるメソッド。このメソッドが実行されると、プログラムの実行が直ちに止まり、後続のコードが実行されない。つまり、プログラムの途中で強制終了することができる。

`if order1.nil?`
- `if`は条件が成立する場合に後続のコードを実行するためのもの。
- **nil?メソッド**：nil?メソッドはオブジェクトが`nil`であるかどうかを判定するためのメソッドで、**オブジェクトが nil だった場合に true を返すメソッド。**

</details>





------------


## ✍🏻 感想
### 🕵🏻 真実を突き止めるような感じ
- デバッグのポイントなる場所を指定
- プログラムの実行
- 変数の値を変えて調べる
- ステップ実行
- 問題となる箇所の特定

これらの一連の流れがエラーの原因を突き止めるために大切なプロセスだと実感。`debug.gem`を使用することで、論理的なプロセスを効率的に行えることができました。初めの「デバッグのポイントとなる場所を指定」では`binding.break`の位置を見定めるのに時間がかかってしまいましたので、ここはちゃんと「**コードが読めるようになること**」と「**慣れ**」が必要ですね。

今のところですが、VS Codeよりも Terminal でデバッグを行うのが好きみたいです。
難しかったですが、面白かったです。次回はプログラムの修正に着手します。


------------


## ⏰ 学習時間
- Today:&nbsp;&nbsp;  hours  min
- Total: 716 hours 33 min
