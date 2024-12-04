# 2024/12/04(水)
## プラクティス『Bundler の基本を理解する』

## 🧩 タスクばらし
- [ ] 各参考ページを確認
- [ ] bundler を使って必要な gem がインストールできる


------------


## 🐾 スモールステップ
<details><summary>各参考ページを確認</summary>

- [x] [Bundlerの使い方 - Qiita](https://qiita.com/oshou/items/6283c2315dc7dd244aef)
   - [x] [Rubygemsのススメ | Rubyに慣れていない初心者さんへ](https://qiita.com/sumyapp/items/5ec58bf3567e557c24d7)
   - [x] [Bundler概要](https://qiita.com/hisonl/items/162f70e612e8e96dba50)
   - [x] [Bundlerとは](http://shokai.org/blog/archives/7262)
- [ ] [bundle install時に--path vendor/bundleを付ける必要性は本当にあるのか、もう一度よく考えてみよう](https://qiita.com/jnchito/items/99b1dbea1767a5095d85)
   - [ ] [bundle installするときはpathを指定しよう](https://blog.dakatsuka.jp/2010/11/09/bundle-install.html)
   - [ ] [https://github.com/heroku/legacy-cli](https://github.com/heroku/legacy-cli)
   - [ ] [https://github.com/flavorjones/chromedriver-helper](https://github.com/flavorjones/chromedriver-helper)
   - [ ] [bundle install --path vendor/bundleと、bundle listとgem listの違いについて](https://qiita.com/okuramasafumi/items/1aea3ed27763315328a3)
- [ ] [Bundler: The best way to manage a Ruby application's gems](https://bundler.io/)
- [ ] [https://www.ruby-lang.org/ja/news/2018/12/25/ruby-2-6-0-released/](https://www.ruby-lang.org/ja/news/2018/12/25/ruby-2-6-0-released/)

</details>


------------


## 🧑🏻‍💻 本日の取り組み
### プラクティス『Bundler の基本を理解する』
- 参考URL の内容を咀嚼
   - [Bundlerの使い方 - Qiita](https://qiita.com/oshou/items/6283c2315dc7dd244aef)
      - [Rubygemsのススメ | Rubyに慣れていない初心者さんへ](https://qiita.com/sumyapp/items/5ec58bf3567e557c24d7)
      - [Bundler概要](https://qiita.com/hisonl/items/162f70e612e8e96dba50)
      - [Bundlerとは](http://shokai.org/blog/archives/7262)


------------


## ⏭️ 次回
### プラクティス『Bundler の基本を理解する』
- 参考URL の内容を咀嚼
   - [bundle install時に--path vendor/bundleを付ける必要性は本当にあるのか、もう一度よく考えてみよう](https://qiita.com/jnchito/items/99b1dbea1767a5095d85)
      - [bundle installするときはpathを指定しよう](https://blog.dakatsuka.jp/2010/11/09/bundle-install.html)
      - [https://github.com/heroku/legacy-cli](https://github.com/heroku/legacy-cli)
      - [https://github.com/flavorjones/chromedriver-helper](https://github.com/flavorjones/chromedriver-helper)
      - [bundle install --path vendor/bundleと、bundle listとgem listの違いについて](https://qiita.com/okuramasafumi/items/1aea3ed27763315328a3)
   - [Bundler: The best way to manage a Ruby application's gems](https://bundler.io/)
   - [https://www.ruby-lang.org/ja/news/2018/12/25/ruby-2-6-0-released/](https://www.ruby-lang.org/ja/news/2018/12/25/ruby-2-6-0-released/)


------------


## 💡 本日の学び・気付き
### Bundlerの使い方 - Qiita
##### Bundler とはなんぞや
- Gem は以下のように個別に手動インストールすることが可能。
   - gem install "sinatra"
   - gem install "unicorn"
   - gem install "omniauth"
- 様々な Gem を組み合わせて使っていると互換性の問題が出てくる場合がある。
- 複数人、複数環境で開発を行う場合は、各環境で使うライブラリの名前、バージョンを合わせる必要がある。
- ↑こういった場合に、Gem 同士の互換性を保ちながら各 Gem の導入、管理を行ってくれるのが Bundler 。
- Gemfile というファイルにインストールしたい Gem を記述し、それを元に Bundler を使用してインストールを行う。
- Bundler 本体以外の Gem は基本的に Bundler 経由でインストールを行うのがお勧め。

##### Bundler インストールの仕方
- Bundler も Gem の1つ。
- 手動ダウンロード
   - `gem install bundler`
- Bundler 導入後はバージョンが表示されることを確認すること。
   - `bundler -v`

### Rubygemsのススメ | Rubyに慣れていない初心者さんへ
##### Rubygems とは？
- Ruby言語で書かれたプログラムをより便利にするためのツール（ライブラリ）が簡単に使えるように配布されている場所、機能のこと。

##### Ruby on Rails は Rubygems を沢山使っている Framework
- ActiveSupport は Rubygems 上で配布されている、Ruby言語用のライブラリ。Ruby on Rails といった Framework では ActiveSupport が標準で require されている。

##### Rubygems には他にも便利なツールがたくさんある
- Ruby on Rails に標準装備されていない、RubyGem もたくさんある。
- 一応、ライセンスが「自由に使って良い」ものでないかどうかだけ、ホームページなどで確認すること。殆どは

> Active Record is released under the MIT license.

と書いてあるとのこと。MITライセンスは自由に使ってもOK。

### Bundler 概要
##### 特徴
- Gemパッケージの種類やバージョンの管理
- 複数PCで必要なGemパッケージをインストールする仕組みを提供 => チーム間で同一の開発環境を簡単に構築することが可能に。

##### 運用方針
基本的に、gemコマンドでインストールするのは Bundler のみで、その他のgemパッケージは、 Bundler 経由でインストールするという方針。
```shell
gem install bundler
```

##### Gemインストールの流れ
- Gemfile にインストールするGemパッケージを記述し、
```shell
bundle install
```
を実行してインストールする。
※ 「Gemfile」に書かれたGemパッケージと、そのGemパッケージが依存しているGemパッケージを自動的に調べて全てインストールしてくれる。

##### よく使う Bundler のサブコマンド
| コマンド | 概要 |
|:---|:---|
| bundle init | Gemfile を生成 |
| bundle install | Gemfile に書かれたGemパッケージをインストール |
| bundle exec | Bundler でインストールされたGemパッケージを使用してコマンドを実行 |
| bundle list | インストール済みのGemパッケージの一覧を表示 |
| bundle update | インストール済みのGemパッケージのバージョンを更新 |

##### Gemパッケージの保存先
- `bundle install`が実行されると、rbenv利用可の場合、`/Users/ユーザー名/.rbenv/versions/バージョン名/lib/ruby/gems/...`以下にインストールされる。
- `bundle install --path <フォルダ名>`とすれば、指定のフォルダにインストール先を指定できる。例えば、
```shell
bundle install --path vendor/bundle
```
と記述すると、railsアプリのルートディレクトリの下の vendor/bundleディレクトリにインストールされ、そのアプリケーションの中だけにインストールされる。一度上のコマンドを実行すれば、Bundler はインストール先を記憶するので次回以降は、
```shell
bundle install
```
を実行するだけで毎回vendor/bundleディレクトリにインストールされる。
- 個別のRailsアプリにインストールされている Gem の一覧を見るには以下のコマンドを使うとよい。
```shell
bundle list
```

##### Gemfile とは
- インストールするGemパッケージの名前とバージョンを記述するファイル。

##### Gemfile.lock とは
- インストールされたGemパッケージの名前とバージョンが記録されたファイル。他の環境で同じアプリケーションの開発を行う場合は、プログラムファイルに加えてこの「Gemfile.lock」ファイルを配布する。そして、他の環境で「bundle install」を実行すると、今度は「Gemfile.lock」ファイルが参照され、指定されたバージョンのGemパッケージがインストールされるようになる。

### 橋本商会 >> Ruby 書くなら Bundler 使え
##### Bundler とは
- プロジェクト内で使う Rubygems を管理するしくみ。プロジェクトの一番上のディレクトリに「Gemfile」というテキストファイルを置き、その中に Gem の名前（と必要あればバージョンも）書く。以下のコマンドで、Gem が一括インストールできる。
```shell
bundle install
```
- プログラム内で以下のコードを書くと、Gem が一括 require できる。
```ruby
require 'bundler'
Bundler.require
```

##### どんな時に便利なの？
- **使用する Gem のバージョンを指定できる**。
- 開発環境とデプロイ環境で完全に同じバージョンの Gem を使えると、無駄なバグが起こらない。

##### プロジェクトのディレクトリに Gem をインストールできる
```shell
bundle install --path （ディレクトリ名）
```
- Gem そのものをちょっと修正して使うときや、Gem のバグ探しなどに便利。

##### Gem をインストール
```shell
bundle install
```
- Gemfile.lock がない場合（初めて bundle install したとき）、Gemfile.lock というファイルが生成される。

##### Gem のアップデート
```shell
bundle update
```
- rubygems.org から最新版を取得し、Gemfile.lock を更新する。

##### bundler で指定した Gem を使う
これをやらないと、システムに入っている最新版の Gem を使ってしまう。
- **bundler で指定した Gem を使う（実行時に指定）。**
今まで
```shell
ruby foo.rb
rackup config.ru
```
等で実行していたのを、
```shell
bundle exec ruby foo.rb
bundle exec rackup config.ru
```
とする。

- **bundler で指定した Gem を使う（プログラム内で指定）。**
```shell
require 'bundler/setup'
```
これを書けば使用バージョンが Gemfile.lock に書かれているものに固定される。

##### Gem のテンプレも作れる
```shell
bundle gem 名前
```
これで Gem の雛形が作れる。


------------


## ✍🏻 感想
### 💡 Bundler の詳細を知る
Bundler、Bundlerインストールの仕方、Gemパッケージの保存先、Gemfile.lock を中心に学びました。まだ座学の段階ではありますが、これらがチーム開発において非常に重要な役割を果たしている、ということが分かりました。次回は「bundle install時に--path vendor/bundleを付ける必要性」について学びます。

### 🏆 受賞おめでとうございます！
株式会社ロッカ（フィヨルドブートキャンプ）がRuby biz Grand prixにおいてクリエイティブ賞を受賞されましたこと、誠におめでとうございます🎉

日頃より、惜しみないサポートとご指導をいただき、心より感謝しております。これからも、フィヨルドブートキャンプで成長し続けられるよう励んでまいります。本当におめでとうございます✨


------------


## ⏰ 学習時間
- Today:&nbsp;&nbsp; 4 hours 38 min
- Total: 733 hours 11 min
