# 2024/11/01(金)

## 🧩 タスクばらし
### プラクティス『カレンダーのプログラム(Ruby)』の修了
- [x] 各参考ページを確認
- [x] Rubyのドキュメントの読み方がわかるようになる
- [x] カレンダーのプログラムに取り組む
- [x] 課題提出前の確認
- [ ] 課題提出
- [ ] 完了したら他の方の提出物と自分の提出物を見比べる

------------

## 🐾 スモールステップ
<details><summary>各参考ページを確認</summary>

- [x] [class Enumerator](https://docs.ruby-lang.org/ja/latest/class/Enumerator.html)
- [x] [library optparse](https://docs.ruby-lang.org/ja/latest/library/optparse.html)
- [x] [class Date](https://docs.ruby-lang.org/ja/latest/class/Date.html)
- [x] [rubyでコマンドを作る](https://bootcamp.fjord.jp/articles/40)
- [x] [コマンドライン引数・オプションの処理](https://bootcamp.fjord.jp/pages/251)
- [x] [プログラミングでよく使う英単語のまとめ【随時更新】 - Qiita](https://qiita.com/Ted-HM/items/7dde25dcffae4cdc7923)
- [x] [プログラミング初心者は変数名やメソッド名を略さない方がいいよ、という話 - give IT a try](https://blog.jnito.com/entry/2020/10/20/092724)
</details>


<details><summary>Rubyのドキュメントの読み方がわかるようになる</summary>

- [x] 『[Ruby公式リファレンスの読み方](https://www.youtube.com/watch?v=5lvECnh_PCg)』
- [x] 『[Rubyの公式リファレンスが読めるようになる本](https://zenn.dev/jnchito/books/how-to-read-ruby-reference)』
   - [x] Chapter 01 はじめに
   - [x] Chapter 02 ユースケースその1：ググって公式リファレンスにたどり着いた場合
   - [x] Chapter 03 ユースケースその2：クラスのメソッド一覧から目的のメソッドを探す場合
   - [x] Chapter 04 ユースケースその3：Rubyにはどんなクラスやモジュールがあるのか知りたい場合
   - [x] Chapter 05 ユースケースその4：わからない用語を調べたい場合
   - [x] Chapter 06 ユースケースその5：記号の意味を調べたい場合
   - [x] Chapter 07 ユースケースその6：Rubyの使い方や言語仕様を学びたい場合
   - [x] Chapter 08 ユースケースその7：公式リファレンスを横断的に検索したい場合
   - [x] Chapter 09 付録：Ruby on Railsの公式リファレンスについて
</details>


<details><summary>カレンダーのプログラムに取り組む</summary>

- [x] カレンダーのプログラムを書く

**※ 分からない箇所が出てきたときは、以下のヒントを適宜参考にすること**
- [library optparse](https://docs.ruby-lang.org/ja/latest/library/optparse.html)
- [Date class](https://docs.ruby-lang.org/ja/latest/class/Date.html)
- [カレンダー課題のQ&A](https://bootcamp.fjord.jp/questions/tags/%E3%82%AB%E3%83%AC%E3%83%B3%E3%83%80%E3%83%BC?all=true)
- [【新人プログラマ応援】開発タスクをアサインされたらどういう手順で進めるべきか - Qiita](https://qiita.com/jnchito/items/017487cd882091494298)
- [セルフマネジメントの必須スキル「タスクばらし」そのポイント | Social Change!](https://kuranuki.sonicgarden.jp/archives/21981)
- [プログラミング初心者歓迎！「エラーが出ました。どうすればいいですか？」から卒業するための基本と極意（解説動画付き）](https://qiita.com/jnchito/items/056325421b7e36f02335)
- [🤔 わからないことをメンターや他の受講生に質問をする方法](https://bootcamp.fjord.jp/pages/use_the_question_room) 
</details>


<details><summary>課題提出前の確認</summary>

- [x] [RubyTips - komagataのブログ](https://docs.komagata.org/tags/rubytips/)
- [x] [初心者がRailsプロジェクトへの初PRする前に見るチェックリスト - komagataのブログ](https://docs.komagata.org/5676)
- [x] [GitHubでコードを提出するときに気をつけること](https://bootcamp.fjord.jp/pages/info-for-github)
- [x] [プログラミング初心者はgit commitする前に必ずdiffを自分でレビューするクセを付けよう](https://bootcamp.fjord.jp/pages/322)
- [x] [プルリクエスト形式で提出物を出す際の「これはやっちゃダメ」リスト](https://bootcamp.fjord.jp/pages/317)
</details>


<details><summary>課題提出</summary>

- [ ] Pull Request としてアップする
- [ ] URL と Terminal での実行結果を提出
</details>


<details><summary>完了したら他の方の提出物と自分の提出物を見比べる</summary>

- [ ] 他の方の提出物と自分の提出物を見比べる
</details>

------------

## ✍🏻 本日の取り組み
### プラクティス『カレンダーのプログラム(Ruby)』
- カレンダーのプログラムに取り組む
   - 書いたコードの見た目や構成を整える
- 課題提出前の確認
   - スクリプトの変更
   - [提出物のPRのやり方を視聴](https://www.youtube.com/watch?v=XMgLL4qIyEA&t=2s)（途中まで）

------------

## 💡 本日の学び・気付き
### 【本日の学び】
### ①後置if（if修飾子）
後置if（if修飾子）と呼ばれる、if式のちょっと便利な書き方がある。
後置ifを使うと、`if`から`end`まで複数行で書いたプログラムを1行で書くことができる。後置ifでは`end`を書く必要がない。条件を満たしたときの処理が1行に収まるときに使うと、プログラムを短く読みやすく書くことができる。
```ruby
# とちらも結果は同じ
["カフェラテ", "モカ", "コーヒー"].each do |drink|
  if drink.match?(/ラテ/)
    puts drink
  end
end


["カフェラテ", "モカ", "コーヒー"].each do |drink|
  puts drink if drink.match?(/ラテ/) # match?メソッドとifで条件判断
end
```
```shell
% ruby test1.rb
カフェラテ
```

### 【復習】
#### スクリプトの変更
1. スクリプトファイルを作成する
   - テキストエディタを開いて（VSCodeでOK）、作成したカレンダーのコードをコピーし、新しいファイルに貼り付ける。
      - 今回ディレクトリは`FBC`
      - コードの一番上には`#!/usr/bin/env ruby`を必ず書く（大事な**shebang**シバン）
   -  ファイル名を`cal.rb`として保存。

2. ファイルに実行権限を付ける
   - ターミナルを開き、`cal.rb`ファイルがあるディレクトリに移動する。
   - 次のコマンドを実行してファイルにuserでの実行権限を付ける。
```shell
% chmod u+x cal.rb
```
3. スクリプトを実行して確かめる
   - ターミナルで次のコマンドを実行する。
```shell
% ./cal.rb
      11月 2024      
日 月 火 水 木 金 土
                1  2 
 3  4  5  6  7  8  9 
10 11 12 13 14 15 16 
17 18 19 20 21 22 23 
24 25 26 27 28 29 30
```

#### 提出物の PR のやり方
[提出物のPRのやり方を視聴](https://www.youtube.com/watch?v=XMgLL4qIyEA&t=2s)（途中まで）
- 「**/tmp**」は、Unix系オペレーティングシステム（LinuxやmacOSなど）における一時ファイルを保存するためのディレクトリである。このディレクトリは、システムやアプリケーションが一時的に必要とするファイルを保存する場所として使用される。

具体的には、以下のような特徴がある

1. **一時ファイルの保存**：プログラムが一時的に必要とするファイル（例えば、インストール中の一時ファイルや一時的なデータファイル）を保存する。
2. **自動削除**：多くのシステムでは、`/tmp`ディレクトリ内のファイルは一定期間が経過すると自動的に削除される。これにより、ディスクスペースが無駄に消費されるのを防ぐ。
3. **アクセス権限**：`/tmp`ディレクトリは通常、全てのユーザーが読み書きできるように設定されている。ただし、セキュリティ上の理由から、各ユーザーが作成したファイルは他のユーザーからアクセスできないようにすることが一般的。
例えば、ターミナルで`cd /tmp`と入力すると、この一時ディレクトリに移動することができる。ここで、`ls`コマンドを使ってディレクトリの内容を確認することもできる。


------------

## 🏃🏻‍➡️ 次回
### プラクティス『カレンダーのプログラム（Ruby）』
- 課題提出前の確認
   - [提出物のPRのやり方を視聴](https://www.youtube.com/watch?v=XMgLL4qIyEA&t=2s)（途中から）
- 課題提出

------------

## ❤️‍🔥 感想
### 🤔🫥 レイアウトは難しく、提出物のPRのやり方はすっかり忘れた
完成したカレンダーのコードを整える作業を行いました。読みやすい・綺麗・シンプル・変数名......いろんなところに気を付けなければならないのが大変ですね。「もしかして、もっと読みやすい書き方があるのでは？」と悩んでいたのですが、今の実力ではここまでです。あとはメンターさんのレビューに委ねます。

提出物の PR のやり方をすっかり忘れました。前回のFizzBuzz問題ではちゃんと Notion に手順を残していたのですが読んでもよく分からず。動画を確認しながら手を動かして思い出すしかありません。

------------

## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 7 hours 03 min
- Total: 583 hours 47 min
