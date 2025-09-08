# 2025/09/08(月)
## 📚 プラクティス『lsコマンドを作る1』

:::details 🎯 学習の狙い
- 標準出力について学ぶ
- 標準ライブラリの使い方を学ぶ
- Enumeratorには、each以外に便利なメソッドがあることを学ぶ
- RailsじゃないRubyプログラミングを学ぶ
- メソッド分割を学ぶ
- わかりやすい変数名メソッド名を学ぶ
- 大きな問題を分割する力を学ぶ
:::

:::details 参考
  - [x] [lsコマンドを作る](https://bootcamp.fjord.jp/pages/380)
:::

:::details 学習の狙い
  - [x] [【lsコマンド】大きな問題を小さく分解してから取り組む](https://bootcamp.fjord.jp/pages/279)
:::

:::details ヒント

  - [x] [lsコマンドの使い方と覚えたい15のオプション【Linuxコマンド集】](https://eng-entrance.com/linux_command_ls)
  - [x] [library optparse (Ruby 2.6.0)](https://docs.ruby-lang.org/ja/latest/library/optparse.html)
  - [x] [コマンドライン引数によるオプションに対応する (optparse) | まくまくRubyノート](https://maku77.github.io/ruby/io/optparse.html)
  - [x] [コマンドライン引数・オプションの処理](https://bootcamp.fjord.jp/pages/251)
  - [x] [binding.irb](https://docs.ruby-lang.org/ja/latest/method/Kernel/m/binding.html)
  - [x] [Fileクラス](https://docs.ruby-lang.org/ja/latest/class/File.html)
  - [x] [lsコマンドで表示されるファイルのモード(drwxr-xr-x) 〜RubyのFile::Stat#modeとは〜](https://zenn.dev/universato/articles/20201202-z-mode)
:::

:::details 良いプログラムを書くための方法

  - [x] [プログラミング初心者は変数名やメソッド名を略さない方がいいよ、という話 - give IT a try](https://blog.jnito.com/entry/2020/10/20/092724)
  - [x] [\[RubyTips\] ハッシュテーブルによる分岐数削減](https://docs.komagata.org/5691)
  - [x] [プログラムを書くときの考え方](https://bootcamp.fjord.jp/pages/147)
  - [x] [rubyでコマンドを作る](https://bootcamp.fjord.jp/pages/250)
  - [x] [RubyTips - komagataのブログ](https://docs.komagata.org/tags/rubytips/)
  - [x] [Rubyスクリプトにもmainメソッドを定義するといいかも、という話 - Qiita](https://qiita.com/jnchito/items/4b4cae54170cc2f4377e)
  - [x] [初心者がRailsプロジェクトへの初PRする前に見るチェックリスト - komagataのブログ](https://docs.komagata.org/5676)
  - [x] [プログラミングでよく使う英単語のまとめ【随時更新】 - Qiita](https://qiita.com/Ted-HM/items/7dde25dcffae4cdc7923)
  - [x] [代表的なデータ構造](https://bootcamp.fjord.jp/pages/148)
  - [x] [配列の二人三脚を避ける](https://bootcamp.fjord.jp/pages/388)
  - [x] [参考：lsコマンドの列幅が人によって異なるのはなぜ？ | FBC
](https://bootcamp.fjord.jp/questions/707)
:::

:::details 終了条件の確認

- [x] [終了条件 - lsコマンドを作る](https://bootcamp.fjord.jp/pages/ls-command#requirements)
:::

:::details 📌 要件

- [ ] オプション（`-a`や`-r`など）を付けず、且つ引数（フォルダのパス）も指定せずに実行する
- [ ] そのまま実行すると、今いるフォルダ（カレントディレクトリ）の中身を表示する
- [ ] `gem`は使わずに Ruby の標準ライブラリだけで作ること
- [ ] 完成したコードは GitHub の Pull Request として提出すること
- [ ] `rubocop-fjord`でデバッグを実行し、全てパスさせること
- [ ] 2つ以上のメソッドを自分で定義すること
- [ ] 表示は横に最大3列になるようにレイアウトすること
  - 3, 6, 9, 12のように3の倍数の件数だけでなく、最後の列に空欄ができるケースの結果も載せる
  - 「3列から5列に仕様変更してください」または「3列から100列に変えてください」とあとから言われても必要最小限の変更で対応できるようなロジックにしておくこと

:::

:::details 🐾 スモールステップ ※ 随時追加・変更あり

- [x] ディレクトリやファイルの一覧を取得
- [x] ディレクトリやファイルをアルファベット順で出力
- [x] `.`から始まる隠しファイルを表示させない
- [ ] 横に最大3列で表示する（ただし、後で列数を変更できるよう柔軟にする）
  - [x] 要素数、列数、行数についての考え方を掴む
  - [x] 余りを切り上げるメソッドを調べる
  - [ ] 調べたメソッドを使い、縦に要素を置くコードの書き方を調べる
- [ ] 件数が列数で割り切れない場合も対応（最後の行に空欄が出るケース）
- [ ] コードの書き方をスッキリさせる（リファクタリング）
:::


---


### 🧑🏻‍💻 本日の取り組み
#### プラクティス『lsコマンドを作る1』🛠️💻
- lsコマンド作成
  - 要素を3列に並べる考え方について考える


---


### ⏭️ 次回
#### プラクティス『lsコマンドを作る1』🛠️💻
- lsコマンド作成
  - あるメソッドを使って横に最大3列で表示するコードを考える


---


### 💡 本日の学び・気付き
#### プラクティス『lsコマンドを作る1』🛠️💻
:::details ⚠️ ネタバレに注意
##### 要素を3列に並べるという考え方について
- 例）8個ある要素を3列に並べる場合
```shell
列1   列2   列3
 1     4     7   # 行1
 2     5     8   # 行2
 3     6         # 行3
```
要素8 ÷ 列数3 ＝ 行数2
8 ÷ 3 ＝ 2 余り2
→ 2行はきっちり埋まる
→ 余りが出た分はプラス1行（**余りを切り上げる**）
→合計 3行

- 例）10個ある要素を3列に並べる場合
```shell
列1   列2   列3
 1     5     9   # 行1
 2     6    10   # 行2
 3     7         # 行3
 4     8         # 行4
```
要素10 ÷ 列数3 ＝ 行数3
10 ÷ 3 ＝ 2 余り1
→ 3行はきっちり埋まる
→ 余りが出た分はプラス1行（**余りを切り上げる**）
→合計 4行

何となくだけど「**要素数 ÷ 列数 ＝ 行数**」という考え方は掴めた。

##### 「余りが出たら切り上げる」とは？
**1. 「割り算で余りが出たら切り上げる」とは？**
- 要素をきっちり 3列に分けたい。
- でも、数が割り切れないと最後に余りが生じる。
- その「余り」の分を入れるためにもう 1行追加する。

→ つまり「**切り上げ**」が必要。

**2. 「切り上げ」を Ruby でどのようにして表すのか？**
余りが発生するということは、**小数**である、ということ。Ruby では、整数は`Integer`クラス、小数は`Float`クラスになる（**チェリー本 P. 57 数値クラスのあれこれ 参照**）

Rubyリファレンスマニュアルで`Float`クラスを見てみると、`ceil`、`floor`、`round`のそれぞれのメソッドが小数に関するメソッドであることが分かった。

[Rubyリファレンスマニュアル：class Float](https://docs.ruby-lang.org/ja/latest/class/Float.html)

**3. irb でメソッドの動きを確認する**
```shell
# ceilメソッド
irb(main):001> p (10 / 3.0).ceil
4
=> 4

# floorメソッド
irb(main):002> p (10 / 3.0).floor
3
=> 3

# roundメソッド
irb(main):003> p (10 / 3.0).round
3
=> 3
```
- `ceil`：小数が切り上げられる。
- `floor`：小数点以下を切り捨てる。
- `round`：四捨五入する。

**4. 結論**
Ruby で「余りが出た場合に切り上げたい」状況には`ceil`メソッド（おそらく🤔）。次は、この`ceil`を実際に使って**縦に要素を並べるコード**を調べていく。
:::


---


### ✍🏻 感想
#### 🏋🏻 アドバイスを活かして
メンターの多田さんのアドバイスを参考に**配列の要素を3つに分ける考え方**のヒントを掴むことができました。次は、この考え方をコードでどう表現するかを考えていきます。

多田さん、いつもありがとうございます😊✨


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2 hours 38 min
- Total: 1277 hours 49 min
