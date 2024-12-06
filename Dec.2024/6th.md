# 2024/12/05(金)

## 📚 プラクティス『rubocop の使い方を知る』


### 🧩 タスクばらし
- [ ] 各参考ページを確認
- [ ] rubocop の使い方を知る（rubocop-fjordの使い方も）


### 🐾 スモールステップ
<details><summary>各参考ページを確認</summary>

- [x] [bbatsov/rubocop: A Ruby static code analyzer, based on the community Ruby style guide.](https://github.com/rubocop/rubocop)
- [ ] [【Rails】RuboCopの基本的な使用方法と出力の見方 - Qiita](https://qiita.com/terufumi1122/items/ad55bf8713c0df053f58)
- [ ] [rubocop-fjordの使い方](https://bootcamp.fjord.jp/pages/292)
- [ ] [盲目的にRubocopを適用しない | FBC](https://bootcamp.fjord.jp/pages/rubocop-is-not-perfect)

</details>


------------


### 🧑🏻‍💻 本日の取り組み

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
#### bbatsov/rubocop: A Ruby static code analyzer, based on the community Ruby style guide.
- RuboCop は、Rubyプログラムのコード品質を向上させるための静的コード解析ツール。
   - 静的コード：プログラムが実行される前の状態、つまりソースコードそのものを指す。
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

#### 【Rails】RuboCopの基本的な使用方法と出力の見方 - Qiita





------------


### ✍🏻 感想
#### 💬 Bundler への印象
Bundler の基本を学んでみて、とても便利なツールだと感じました。Gem の依存関係を一元管理できるので、プロジェクトの環境が一貫して保たれることが素晴らしいです。特に複数のプロジェクトを扱う際に、依存関係が混ざらないような仕組みになっているのが Bundler の良さであり特徴だなと認識しました。

#### 🧑🏻‍💻 第4回 ゆるっとCSSカフェ☕️
皆さんが冷静にコードを一つずつ書いていく様子を眺めながら、分からないメソッドや単語ができたら逐一調べて Discord のスレッドにまとめています。今は羨望の眼差しで拝見していますが、いつか私も積極的に手を動かして書けるようになりたいです！


------------


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;  hours  min
- Total: 739 hours 05 min
