# 2024/12/05(木)
## 📚 プラクティス『Bundler の基本を理解する』


### 🧩 タスクばらし
- [x] 各参考ページを確認
- [x] bundler を使って必要な gem がインストールできる


### 🐾 スモールステップ
<details><summary>各参考ページを確認</summary>

- [x] [Bundlerの使い方 - Qiita](https://qiita.com/oshou/items/6283c2315dc7dd244aef)
   - [x] [Rubygemsのススメ | Rubyに慣れていない初心者さんへ](https://qiita.com/sumyapp/items/5ec58bf3567e557c24d7)
   - [x] [Bundler概要](https://qiita.com/hisonl/items/162f70e612e8e96dba50)
   - [x] [Bundlerとは](http://shokai.org/blog/archives/7262)
- [x] [bundle install時に--path vendor/bundleを付ける必要性は本当にあるのか、もう一度よく考えてみよう](https://qiita.com/jnchito/items/99b1dbea1767a5095d85)
   - [x] [bundle installするときはpathを指定しよう](https://blog.dakatsuka.jp/2010/11/09/bundle-install.html)
   - [x] [https://github.com/heroku/legacy-cli](https://github.com/heroku/legacy-cli)
   - [x] [https://github.com/flavorjones/chromedriver-helper](https://github.com/flavorjones/chromedriver-helper)
   - [x] [bundle install --path vendor/bundleと、bundle listとgem listの違いについて](https://qiita.com/okuramasafumi/items/1aea3ed27763315328a3)
- [x] [Bundler: The best way to manage a Ruby application's gems](https://bundler.io/)
- [x] [https://www.ruby-lang.org/ja/news/2018/12/25/ruby-2-6-0-released/](https://www.ruby-lang.org/ja/news/2018/12/25/ruby-2-6-0-released/)

</details>


------------


## 📚 プラクティス『rubocop の使い方を知る』


### 🧩 タスクばらし
- [ ] 各参考ページを確認
- [ ] rubocop の使い方を知る（rubocop-fjordの使い方も）


### 🐾 スモールステップ
<details><summary>各参考ページを確認</summary>

- [ ] [bbatsov/rubocop: A Ruby static code analyzer, based on the community Ruby style guide.](https://github.com/rubocop/rubocop)
- [ ] [【Rails】RuboCopの基本的な使用方法と出力の見方 - Qiita](https://qiita.com/terufumi1122/items/ad55bf8713c0df053f58)
- [ ] [rubocop-fjordの使い方](https://bootcamp.fjord.jp/pages/292)
- [ ] [盲目的にRubocopを適用しない | FBC](https://bootcamp.fjord.jp/pages/rubocop-is-not-perfect)

</details>


------------


### 🧑🏻‍💻 本日の取り組み
#### プラクティス『Bundler の基本を理解する』
- 参考URL の内容を咀嚼
   - [bundle install時に--path vendor/bundleを付ける必要性は本当にあるのか、もう一度よく考えてみよう](https://qiita.com/jnchito/items/99b1dbea1767a5095d85)
      - [bundle installするときはpathを指定しよう](https://blog.dakatsuka.jp/2010/11/09/bundle-install.html)
      - [https://github.com/heroku/legacy-cli](https://github.com/heroku/legacy-cli)
      - [https://github.com/flavorjones/chromedriver-helper](https://github.com/flavorjones/chromedriver-helper)
      - [bundle install --path vendor/bundleと、bundle listとgem listの違いについて](https://qiita.com/okuramasafumi/items/1aea3ed27763315328a3)
   - [Bundler: The best way to manage a Ruby application's gems](https://bundler.io/)
   - [https://www.ruby-lang.org/ja/news/2018/12/25/ruby-2-6-0-released/](https://www.ruby-lang.org/ja/news/2018/12/25/ruby-2-6-0-released/)

#### プラクティス『rubocop の使い方を知る』
- プラクティスの内容を確認
- タスクばらし、スモールステップを作成


### ⏭️ 次回
#### プラクティス『rubocop の使い方を知る』
- 各参考ページを確認
   - [bbatsov/rubocop: A Ruby static code analyzer, based on the community Ruby style guide.](https://github.com/rubocop/rubocop)
   - [【Rails】RuboCopの基本的な使用方法と出力の見方 - Qiita](https://qiita.com/terufumi1122/items/ad55bf8713c0df053f58)
   - [rubocop-fjordの使い方](https://bootcamp.fjord.jp/pages/292)
   - [盲目的にRubocopを適用しない | FBC](https://bootcamp.fjord.jp/pages/rubocop-is-not-perfect)


------------


### 💡 本日の学び・気付き
#### bundle install時に--path vendor/bundleを付ける必要性は本当にあるのか、もう一度よく考えてみよう
- `bundle install`コマンドを実行するとき、「`--path vendor/bundle`を付ける派」と「付かない派」の流派がある。
- 今から Ruby を始める人や、新しくチームに参加してきた人に対しては、「（致命的な問題が出ない限り）」デフォルトのまま使う」とした方が習得のコストが少ないはず。よって`bundle install`の path指定は「オプトイン方式（デフォルトはオフで、利用する意思がある人だけがオンにする）」の方が良い。
- 既存のRailsプロジェクトですでに`--path vendor/bundle`をつけてしまった場合は、以下のコマンドでデフォルト(システムにインストール）に変更できる。
```shell
bundle config unset path
bundle install

# この状態でも問題なく動作することを確認する

# vendor/bundleは不要なので削除
rm -rf vendor/bundle

# 念のためもう一度動作確認する。問題なく動けば設定変更完了
```

#### bundle install --path vendor/bundleと、bundle listとgem listの違いについて
##### 結論
- `--path`オプションを付けるのは開発時においては必要ないが、異なるバージョンの gem が混ざるのが嫌な人は付けること。

##### 目的
- `--path`オプションを付ける目的としては、プロジェクト下のディレクトリ（例えばvendor/bundle）に gem をインストールすることで、グローバルにインストールされた gem と bundler が管理する gem を分離することが挙げられる。他にも、ctags などを利用する際にgemがプロジェクト下にインストールされていると便利である可能性があります。
   - **ctags**：ソースコードを効率的にナビゲートするための便利なツール。

##### bundle list と gem list の違いについて
`bundle list`
- `bundle list`コマンドは、「あるプロジェクトが bundler によって管理されている場合に、そこで使用されている gem を一覧表示するコマンド」。

`gem list`
- `gem list`コマンドは、「グローバルにインストールされたgemを一覧表示するコマンド」。

- 使い分けとしては、基本的にRailsアプリケーションの開発においては`bundle list`コマンドを使用することが多いと思われる。


------------


### ✍🏻 感想
#### 💬 Bundler への印象
Bundler の基本を学んでみて、とても便利なツールだと感じました。Gem の依存関係を一元管理できるので、プロジェクトの環境が一貫して保たれることが素晴らしいです。特に複数のプロジェクトを扱う際に、依存関係が混ざらないような仕組みになっているのが Bundler の良さであり特徴だなと認識しました。

#### 🧑🏻‍💻 第4回 ゆるっとCSSカフェ☕️
皆さんが冷静にコードを一つずつ書いていく様子を眺めながら、分からないメソッドや単語ができたら逐一調べて Discord のスレッドにまとめています。今は羨望の眼差しで拝見していますが、いつか私も積極的に手を動かして書けるようになりたいです！


------------


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 5 hours 54 min
- Total: 739 hours 05 min
