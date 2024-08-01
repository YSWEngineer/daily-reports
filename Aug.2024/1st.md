# 2024/08/01(木)
## 🧩 タスクばらし
### プラクティス『FizzBuzz問題(Ruby)』の修了
- [x] 各参考ページを確認
- [x] FizzBuzz問題に取り組む
- [ ] 課題提出
- [ ] 完了したら他の方の提出物と自分の提出物を見比べる


## 📋 段取り
<details><summary>各参考ページを確認</summary>

- [x] [rubyでコマンドを作る | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/articles/40)
- [x] [Gitで課題提出するまでの手順をまとめた（Sakiさんのブログ）](https://saki-htr.hatenablog.com/entry/2021/02/25/115930)
- [x] [Pull Requestのやり方](https://www.youtube.com/watch?v=XMgLL4qIyEA)
- [x] [GitHubでコードを提出するときに気をつけること](https://bootcamp.fjord.jp/pages/info-for-github)
- [x] [プルリクエスト形式で提出物を出す際の「これはやっちゃダメ」リスト](https://bootcamp.fjord.jp/reports/98547/edit)
</details>

<details><summary>FizzBuzz問題に取り組む</summary>

- [x] FizzBuzzプログラムを書く
</details>

<details><summary>課題提出</summary>

- [ ] Pull Request としてアップする
- [ ] URL と Terminal での実行結果を提出
</details>

<details><summary>完了したら他の方の提出物と自分の提出物を見比べる
</summary>

- [ ] 他の方の提出物と自分の提出物を見比べる
</details>


## ✍🏻 本日の取り組み
### プラクティス『FizzBuzz問題(Ruby)』
- FizzBuzz問題に取り組む


## 💡 本日の学び・気付き
### FizzBuzz問題に取り組む
#### 変数名はどれがいいのか？
- 数や数字を意味する`number`、数を数えることを意味する`count`、慣習として繰り返し処理の回数を数えるときに使われる`i`。


#### FizzBuzzプログラムには if? それとも case?
- `if`文でも`case`文でも、どちらでも書ける。
- `if`文の利点
   - シンプルで直感的な条件分岐を示すことができる。
- `case`文の利点
   - 複数の条件を評価する際に見やすいコードを書くことができる。
- 著書『ゼロからわかるRuby超入門』P.94には
> 「**if**は2つに分岐、**case**は3つ以上に分岐」と考えることです。
YES or NO や A or B と二択のときは**if**から、A or B or C と三択以上になったら**case**から考えてみてください。
また、**if**を書いていて、同じ変数で何回も判定させているな、と感じたときは**case**を試してみてください。うまく書き換えられてスッキリ読みやすいプログラムになると良い気分になります！

- ちなみに`if`文で書くと11行、`case`文で書くと12行。
```ruby
# if文でFizzBuzzを書く
(1..20).each do |number|
  if number % 15 == 0
    puts "FizzBuzz"
  elsif number % 3 == 0
    puts "Fizz"
  elsif number % 5 == 0
    puts "Buzz"
  else
    puts number
  end
end

# case文でFizzBuzzを書く
(1..20).each do |number|
  case
  when number % 15 == 0
    puts "FizzBuzz"
  when number % 3 == 0
    puts "Fizz"
  when number % 5 == 0
    puts "Buzz"
  else
    puts number
  end
end
```

#### FizzBuzzになる条件の書き方について
- `if number % 15 == 0`と`if number % 3 == 0 && number % 5 == 0`の違いについて
   - `if number % 15 == 0`
      - 15 は 3 と 5 の最小公倍数で、3 と 5 の両方で割り切れることを意味する。
      - 条件が短くて、シンプル。
   - `if number % 3 == 0 && number % 5 == 0`
      - 変数`number`が 3 で割り切れて、且つ、5 で割り切れる場合に真となる。
      - 3 と 5 の両方で割り切れることを分かりやすく示している。


## 📍 次回
### プラクティス『FizzBuzz問題(Ruby)』
- 課題提出


## ❤️‍🔥 感想
### 🤔 コードの書き方に悩む
なんとか FizzBuzz 問題のプログラムを書き終えました。コードを書くためにプラクティスで読んだテキストを読み直して、書いて、挙動を確かめて、書き直して......を繰り返しました。何度も書き直すうちに、「たった数行のコードだけど、読みやすい（可読性の高い）コードってどういう書き方なんだろう？」と悩むようになりました。

とりあえず完成はしたので、次回は「課題提出」です。今回のプラクティスの中でうまくできるかどうか個人的に気がかりな工程なのですが、参考動画を視聴しながら一つずつ取り組みます。


## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 1 hours 39 min
- Total: 446 hours 10 min
