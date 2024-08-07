# 2024/08/07(水)
## 🧩 タスクばらし
### プラクティス『カレンダーのプログラム(Ruby)』の修了
- [x] 各参考ページを確認
- [ ] カレンダーのプログラムに取り組む
- [ ] 課題提出前の確認
- [ ] 課題提出
- [ ] 完了したら他の方の提出物と自分の提出物を見比べる

---


## 📋 段取り
<details><summary>各参考ページを確認</summary>

- [x] [class Enumerator](https://docs.ruby-lang.org/ja/latest/class/Enumerator.html)
- [x] [library optparse](https://docs.ruby-lang.org/ja/latest/library/optparse.html)
- [x] [class Date](https://docs.ruby-lang.org/ja/latest/class/Date.html)
- [x] [rubyでコマンドを作る](https://bootcamp.fjord.jp/articles/40)
- [x] [コマンドライン引数・オプションの処理](https://bootcamp.fjord.jp/pages/251)
- [x] [プログラミングでよく使う英単語のまとめ【随時更新】 - Qiita](https://qiita.com/Ted-HM/items/7dde25dcffae4cdc7923)
- [x] [プログラミング初心者は変数名やメソッド名を略さない方がいいよ、という話 - give IT a try](https://blog.jnito.com/entry/2020/10/20/092724)
</details>


<details><summary>カレンダーのプログラムに取り組む</summary>

- [ ] カレンダーのプログラムを書く

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

- [ ] [RubyTips - komagataのブログ](https://docs.komagata.org/tags/rubytips/)
- [ ] [初心者がRailsプロジェクトへの初PRする前に見るチェックリスト - komagataのブログ](https://docs.komagata.org/5676)
- [ ] [GitHubでコードを提出するときに気をつけること](https://bootcamp.fjord.jp/pages/info-for-github)
- [ ] [プログラミング初心者はgit commitする前に必ずdiffを自分でレビューするクセを付けよう](https://bootcamp.fjord.jp/pages/322)
- [ ] [プルリクエスト形式で提出物を出す際の「これはやっちゃダメ」リスト](https://bootcamp.fjord.jp/pages/317)
</details>


<details><summary>課題提出</summary>

- [ ] Pull Request としてアップする
- [ ] URL と Terminal での実行結果を提出
</details>


<details><summary>完了したら他の方の提出物と自分の提出物を見比べる</summary>

- [ ] 他の方の提出物と自分の提出物を見比べる
</details>

---


## ✍🏻 本日の取り組み
### プラクティス『カレンダーのプログラム(Ruby)』
- カレンダーのプログラムに取り組む
   - カレンダーのプログラムを書く

---


## 💡 本日の学び・気付き

### プラクティス『カレンダーのプログラム（Ruby）』

#### スクリプトの準備

##### 1. ファイルの作成
カレンダーを表示するためのプログラムを入れるためのファイルを作成。ファイル名は`cal.rb`。
1. ターミナルを開く。
2. 以下のコマンドを入力して、ファイルを作成。
```
touch cal.rb
```

##### 2. shebang の追加
cal.rb ファイルをテキストエディタ（Vim）で開き、ファイルの一番上に以下の行を追加。
```
#!/usr/bin/env ruby
```

##### 3. ファイルに実行権限を付与
作成したスクリプトファイルに実行権限を付与する必要があるため、以下のコマンドを入力。
```
chmod u+x cal.rb
```

##### 4. スクリプトの実行
最後に、スクリプトを実行させるために以下のコマンドを入力。`cal.rb`スクリプトが実行される。
```
./cal.rb
```

---


## 📍 次回
### プラクティス『カレンダーのプログラム（Ruby）』
- カレンダーのプログラムに取り組む
   - カレンダーのプログラムを書く

---


## ❤️‍🔥 感想
### 🤔❓ 何をどうすればいいのか分からないので......
スクリプトの準備として、`カレンダープログラムを入れるためのファイルを作成` → `shebang の追加` → `作成したファイルに実行権限を付与` → `スクリプトの実行`を行ったのですが、「で、カレンダープログラムを組み立てるために何をどうすればいいのだろう？」と分からず立ち止まってしまいました。プラクティスに載っているヒントをよく読み「何をどうするのか」を知ることを行います。

### 🛫 明晩は大阪へ
「大阪の親戚が倒れて緊急手術をした」という知らせが届きましたので、急遽明日のアルバイト後に大阪に行くことになりました。勉強できる時間を確保するのは難しいとは思いますが、MacBook を持参して行って参ります。

---


## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 3 hours 22 min
- Total: 461 hours 27 min
