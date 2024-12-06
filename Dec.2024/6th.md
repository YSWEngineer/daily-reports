# 2024/12/05(金)

## 📚 プラクティス『rubocop の使い方を知る』


### 🧩 タスクばらし
- [x] 各参考ページを確認
- [x] rubocop の使い方を知る（rubocop-fjordの使い方も）


### 🐾 スモールステップ
<details><summary>各参考ページを確認</summary>

- [x] [bbatsov/rubocop: A Ruby static code analyzer, based on the community Ruby style guide.](https://github.com/rubocop/rubocop)
- [x] [【Rails】RuboCopの基本的な使用方法と出力の見方 - Qiita](https://qiita.com/terufumi1122/items/ad55bf8713c0df053f58)
- [x] [rubocop-fjordの使い方](https://bootcamp.fjord.jp/pages/292)
- [x] [盲目的にRubocopを適用しない | FBC](https://bootcamp.fjord.jp/pages/rubocop-is-not-perfect)

</details>


------------


### 🧑🏻‍💻 本日の取り組み

#### プラクティス『rubocop の使い方を知る』
- 各参考ページを確認
   - [bbatsov/rubocop: A Ruby static code analyzer, based on the community Ruby style guide.](https://github.com/rubocop/rubocop)
   - [【Rails】RuboCopの基本的な使用方法と出力の見方 - Qiita](https://qiita.com/terufumi1122/items/ad55bf8713c0df053f58)
   - [rubocop-fjordの使い方](https://bootcamp.fjord.jp/pages/292)
   - [盲目的にRubocopを適用しない | FBC](https://bootcamp.fjord.jp/pages/rubocop-is-not-perfect)


### 🎯 次回
#### プラクティス『ボウリングのスコア計算プログラム』
- プラクティスの内容を確認
- タスクばらし、スモールステップの作成


------------


### 💡 本日の学び・気付き
### bbatsov/rubocop: A Ruby static code analyzer, based on the community Ruby style guide.
- RuboCop は、Rubyプログラムのコード品質を向上させるための静的コード解析ツール。
   - **静的コード**：プログラムが実行される前の状態、つまりソースコードそのものを指す。
   - **静的コード解析**：プログラムを実行することなくソースコードをチェックし、潜在的な問題を検出する手法。
- RuboCop は、コミュニティRubyスタイルガイドで概説されているガイドラインの多くが適用される。
- コード内で発見された問題を報告するだけでなく、自動的に修正することもできる。

##### インストール
```shell
gem install rubocop
```
- bundler を使って RuboCop をインストールしたい場合は、Gemfile に RuboCop の行を追加（ただし、スタンドアローンツールなので requireオプションは false にする）
```ruby
gem 'rubocop', require: false
```
- RuboCop は、マイナーアップデート（小規模なバージョン更新）で API や Cop の設定の互換性を保つように設計されている。
- RuboCop の拡張機能のメンテナンスと RuboCop のリリース間のアップグレードを容易にすることを目指している。
- 大きな変更はメジャーリリースで行われる。
- RuboCopの予期しないアップデートを避けるために、保守的なバージョンロックをGemfileで使用することを推奨している。それが以下のコード。
```ruby
gem 'rubocop', '~> 1.69', require: false
```

##### クイックスタート
- Rubyプロジェクトのフォルダに rubocop と入力するだけで、マジックが起こるのを見ることができる。
```shell
$ cd my/cool/ruby/project
$ rubocop
```

##### ドキュメント
- RuboCop については、公式ドキュメントで詳しく読むことができる。


### 【Rails】RuboCopの基本的な使用方法と出力の見方 - Qiita
- Linterツール：プログラムのソースコードを解析して、コーディング規約の違反や潜在的なバグ、スタイルの問題を検出するツール。主に、ソースコードの品質を保ち、一貫したコーディングスタイルを維持するために使用される。

##### インストール方法
- Gemfile に記述する方法
```ruby
gem 'rubocop', require: false
gem 'rubocop-rails', require: false
```
```shell
$ bundle install
```

##### 使用方法
`$ rubocop`
- チェックがスタートし、結果が表示される。

`$ rubocop -a`
- 自動的に修正してほしいときは`-a`を付ける。

`$ rubocop --help`
- その他オプションを確認できる。

##### 出力の基本構文
- 一箇所の違反に対し、三行でワンセットになっている。
```ruby
Gemfile:44:25: C: Layout/SpaceAfterColon: Space missing after colon.
  gem 'rubocop', require:false
                        ^
```

##### 違反のレベル
- 重要なものから順に記載。`W`以上は要修正。

`F` Fatal
`E` Error
`W` Warning

↑ 修正すべき
--- 壁 ---
↓ 修正の余地あり

`C` Convention
`R` Refactor


### rubocop-fjordの使い方
#### Installation（インストール）
- 以下の行をアプリケーションの Gemfile に追加する。
```ruby
# For plain Ruby scripts
group :development do
  gem 'rubocop-fjord', require: false
end
```
```ruby
# For Rails projects
group :development do
  gem 'rubocop-fjord', require: false
  gem 'rubocop-rails', require: false
end
```
- 実行
```shell
$ bundle
```
- あるいは、自分でインストールを行う
```shell
$ gem install rubocop-fjord
```

#### Usage（使用方法）
- `.rubocop.yml`に`inherit_gem:`設定を追加
```ruby
# For plain Ruby scripts
inherit_gem:
  rubocop-fjord:
    - "config/rubocop.yml"
```
```ruby
# For Rails projects
inherit_gem:
  rubocop-fjord:
    - "config/rubocop.yml"
    - "config/rails.yml"
```
- `rubocop`コマンドを実行
```shell
$ rubocop
```

#### Development（開発）
- レポをチェックアウトしたのち、bin/setup を実行して依存関係をインストールする。それから、rake test を実行してテストを行う。また、bin/consle を実行すると対話側のプロンプトが表示され、実験を行える。
- この gem をローカルマシンにインストールするには、`bundle exec rake install`を実行する。新しいバージョンをリリースするためには`version.rb`のバージョン番号をアップデートし、`bundle exec rake release`を実行する。これにより、そのバージョンの gitタグが作成され、git commit とタグが`.gem`ファイルが`rubygems.org`にプッシュされる。


### 盲目的にRuboCopを適用しない
- `Lint/UnusedMethodArgument`の警告が出たときはほぼ間違いなく、「**不要な引数があるから削除せよ**」が正しい対処法になる。
- RuboCop の自動修正はいつでも正しいとは限らない。
- もし、`rubocop -A`を使ったあとは、コミット前のセルフレビューを習慣づけること。


------------


### ✍🏻 感想
#### 🤔 RuboCop の一長一短
RuboCop について学びました。RuboCop は、Rubyのコードをチェックし、コーディングに誤りがないかどうかを教えてくれる便利なツールです。ただし、RuboCop の指摘に過信して盲目的に従うのではなく、自分自身の判断や理解を大切にしながら、バランスよく使っていくことが重要です。やはり、コードを読むことは大事ですね。

------------


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 5 hours 31 min
- Total: 744 hours 36 min
