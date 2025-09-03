# 2025/09/03(水)
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

<details><summary>📚 参考資料</summary>

<details><summary>参考</summary>

  - [x] [lsコマンドを作る](https://bootcamp.fjord.jp/pages/380)
</details>
 

<details><summary>学習の狙い</summary>

  - [x] [【lsコマンド】大きな問題を小さく分解してから取り組む](https://bootcamp.fjord.jp/pages/279)
</details>

<details><summary>ヒント</summary>

  - [x] [lsコマンドの使い方と覚えたい15のオプション【Linuxコマンド集】](https://eng-entrance.com/linux_command_ls)
  - [x] [library optparse (Ruby 2.6.0)](https://docs.ruby-lang.org/ja/latest/library/optparse.html)
  - [x] [コマンドライン引数によるオプションに対応する (optparse) | まくまくRubyノート](https://maku77.github.io/ruby/io/optparse.html)
  - [x] [コマンドライン引数・オプションの処理](https://bootcamp.fjord.jp/pages/251)
  - [x] [binding.irb](https://docs.ruby-lang.org/ja/latest/method/Kernel/m/binding.html)
  - [x] [Fileクラス](https://docs.ruby-lang.org/ja/latest/class/File.html)
  - [x] [lsコマンドで表示されるファイルのモード(drwxr-xr-x) 〜RubyのFile::Stat#modeとは〜](https://zenn.dev/universato/articles/20201202-z-mode)
</details>

<details><summary>良いプログラムを書くための方法</summary>

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
</details>

 <details><summary>終了条件の確認</summary>

- [x] [終了条件 - lsコマンドを作る](https://bootcamp.fjord.jp/pages/ls-command#requirements)
</details>
</details>

<details><summary>📌 要件</summary>

- [ ] オプション（`-a`や`-r`など）を付けず、且つ引数（フォルダのパス）も指定せずに実行する
- [ ] そのまま実行すると、今いるフォルダ（カレントディレクトリ）の中身を表示する
- [ ] `gem`は使わずに Ruby の標準ライブラリだけで作ること
- [ ] 完成したコードは GitHub の Pull Request として提出すること
- [ ] `rubocop-fjord`でデバッグを実行し、全てパスさせること
- [ ] 2つ以上のメソッドを自分で定義すること
- [ ] 表示は横に最大3列になるようにレイアウトすること
  - 3, 6, 9, 12のように3の倍数の件数だけでなく、最後の列に空欄ができるケースの結果も載せる
  - 「3列から5列に仕様変更してください」または「3列から100列に変えてください」とあとから言われても必要最小限の変更で対応できるようなロジックにしておくこと

</details>

<details><summary>🐾 スモールステップ ※ 随時追加・変更あり</summary>

- [x] ディレクトリやファイルの一覧を取得
- [x] ディレクトリやファイルをアルファベット順で出力
- [x] `.`から始まる隠しファイルを表示させない
- [ ] 横に最大3列で表示する（ただし、後で列数を変更できるよう柔軟にする）
- [ ] 件数が列数で割り切れない場合も対応（最後の行に空欄が出るケース）
- [ ] コードの書き方をスッキリさせる（リファクタリング）
</details>


---


### 🧑🏻‍💻 本日の取り組み
#### プラクティス『lsコマンドを作る1』🛠️💻
- lsコマンド作成
  - 横に最大3列で表示するための書き方を調べる

#### 質問・雑談タイム
- MacBook Air のスペックについて


---


### ⏭️ 次回
#### プラクティス『lsコマンドを作る1』🛠️💻
- lsコマンド作成
  - 横に最大3列で表示するための書き方を調べる


---


### 💡 本日の学び・気付き
#### プラクティス『lsコマンドを作る1』🛠️💻
<details><summary>⚠️ ネタバレに注意</summary>

### :@ayu-0505:Ayuさんからいただいたアドバイスで気付いたこと。 
- 「横に最大3列を維持して表示する」には、1つのメソッドだけでなく複数のメソッドを組み合わせる必要がある。
- 自分は`Dir`クラスに答えがあるだろうと決めつけてしまっていた。
- 「`Dir.glob`が配列を返すことに目を向け、`Array`クラスも調べる」という発想が足りなかった。

### 同じミスをしないために
- **先入観を捨てる（勝手な思い込み禁止）**
  - `Dir`クラスに答えがあると思い込む > 見つからない > 停滞、という流れを断つ。
- **Rubyリファレンスマニュアルを読むとき、調べる対象の幅を広げる**
  - `Dir`クラス単体で考えるのではなく、`Dir`クラスに関係する返り値にも視野を広げる。
</details>


#### 質問・雑談タイム
##### MacBook Air のスペックについて
###### メモリ
- **24GB あれば十分**
  - RubyMine の使用はだいたい 12GB 程度使う印象。16GMでも大丈夫だが、やや心許ない。
  - RubyMine の使用、チーム開発、自作サービス開発でも 32GB まで増やす必要は基本的にない。
  - intelチップと Appleシリコンでは性能差が大きい（Appleシリコンの方が高効率）。

###### ストレージ
- **512GBが安心**
  - 普段使いだと 256GB でも足りる場合があるが、余裕を持ちたいなら 512GB。
  - 動画や写真を頻繁に扱うのなら 1TB を検討。

###### オプションの Final Cut Pro は？
- **必須ではない**
  - メンターの伊藤さん曰く、動画撮影は Quick Time Player を使用。ごく稀に i Movie を使う程度とのこと。

---


### ✍🏻 感想
#### 読むだけの学習
ひたすら Rubyリファレンスマニュアルを読むだけの一日でしたが、「もしかしてこのメソッドがヒントになるかも」と思える発見がありました。考察の種が見つかって良かったです。


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 6 hours 46 min
- Total: 1273 hours 32 min
