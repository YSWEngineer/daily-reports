# 2025/08/07(木)
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

<details><summary>📚 参考資料</summary>

<details><summary>参考</summary>

  - [ ] [lsコマンドを作る](https://bootcamp.fjord.jp/pages/380)
</details>
 

<details><summary>学習の狙い</summary>

  - [ ] [【lsコマンド】大きな問題を小さく分解してから取り組む](https://bootcamp.fjord.jp/pages/279)
</details>

<details><summary>ヒント</summary>

  - [ ] [lsコマンドの使い方と覚えたい15のオプション【Linuxコマンド集】](https://eng-entrance.com/linux_command_ls)
  - [ ] [library optparse (Ruby 2.6.0)](https://docs.ruby-lang.org/ja/latest/library/optparse.html)
  - [ ] [コマンドライン引数によるオプションに対応する (optparse) | まくまくRubyノート](https://maku77.github.io/ruby/io/optparse.html)
  - [ ] [コマンドライン引数・オプションの処理](https://bootcamp.fjord.jp/pages/251)
  - [ ] [binding.irb](https://docs.ruby-lang.org/ja/latest/method/Kernel/m/binding.html)
  - [ ] [Fileクラス](https://docs.ruby-lang.org/ja/latest/class/File.html)
  - [ ] [lsコマンドで表示されるファイルのモード(drwxr-xr-x) 〜RubyのFile::Stat#modeとは〜](https://zenn.dev/universato/articles/20201202-z-mode)
</details>

<details><summary>良いプログラムを書くための方法</summary>

  - [ ] [プログラミング初心者は変数名やメソッド名を略さない方がいいよ、という話 - give IT a try](https://blog.jnito.com/entry/2020/10/20/092724)
  - [ ] [\[RubyTips\] ハッシュテーブルによる分岐数削減](https://docs.komagata.org/5691)
  - [ ] [プログラムを書くときの考え方](https://bootcamp.fjord.jp/pages/147)
  - [ ] [rubyでコマンドを作る](https://bootcamp.fjord.jp/pages/250)
  - [ ] [RubyTips - komagataのブログ](https://docs.komagata.org/tags/rubytips/)
  - [ ] [Rubyスクリプトにもmainメソッドを定義するといいかも、という話 - Qiita](https://qiita.com/jnchito/items/4b4cae54170cc2f4377e)
  - [ ] [初心者がRailsプロジェクトへの初PRする前に見るチェックリスト - komagataのブログ](https://docs.komagata.org/5676)
  - [ ] [プログラミングでよく使う英単語のまとめ【随時更新】 - Qiita](https://qiita.com/Ted-HM/items/7dde25dcffae4cdc7923)
  - [ ] [代表的なデータ構造](https://bootcamp.fjord.jp/pages/148)
  - [ ] [配列の二人三脚を避ける](https://bootcamp.fjord.jp/pages/388)
  - [ ] [参考：lsコマンドの列幅が人によって異なるのはなぜ？ | FBC
](https://bootcamp.fjord.jp/questions/707)
</details>

 <details><summary>終了条件の確認</summary>

- [ ] [終了条件 - lsコマンドを作る](https://bootcamp.fjord.jp/pages/ls-command#requirements)
</details>
</details>


---


### 🧑🏻‍💻 本日の取り組み
#### プラクティス『lsコマンドを作る1』
- 「学習の狙い」と「修了条件」を読み直し、「自分が何をすべきか」を明確にする


---


### ⏭️ 次回
#### プラクティス『lsコマンドを作る1』
- [【lsコマンド】大きな問題を小さく分解してから取り組む](https://bootcamp.fjord.jp/pages/279)を読む


---


### 💡 本日の学び・気付き
#### 『lsコマンドを作る1』のゴール
- **ruby でオプション無しの lsコマンドを作成し、提出する。**

#### 要件を噛み砕く
- オプション（`-a`や`-r`など）を付けず、且つ引数（フォルダのパス）も指定せずに実行する
- そのまま実行すると、今いるフォルダ（カレントディレクトリ）の中身を表示する
- `gem`は使わずに Ruby の標準ライブラリだけで作ること
- 完成したコードは GitHub の Pull Request として提出すること
- `rubocop-fjord`でデバッグを実行し、全てパスさせること
- 2つ以上のメソッドを自分で定義すること
- 表示は横に最大3列になるようにレイアウトすること
  - 3, 6, 9, 12のように3の倍数の件数だけでなく、最後の列に空欄ができるケースの結果も載せる
  - 「3列から5列に仕様変更してください」または「3列から100列に変えてください」とあとから言われても必要最小限の変更で対応できるようなロジックにしておくこと


---


### ✍🏻 感想
#### 🤦🏻 無駄足を踏んだ一日
要件と修了条件は何とか理解できたものの、次にどの参考資料をどの順番で読むべきかが分からず途方に暮れてしまいました。まだ読んだことがない資料に優先順位をつけるのは難しいと頭では分かっているのに、意地で答えを見つけようとしているうちに時間だけが過ぎ、結局何も手を付けられずに終わってしまいました。

次回は、まずこちらの記事から読み進めます。
- [【lsコマンド】大きな問題を小さく分解してから取り組む](https://bootcamp.fjord.jp/pages/279)


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 5 hours 00 min
- Total: 1222 hours 57 min
