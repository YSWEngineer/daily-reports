# 2024/11/04(月)

## 🧩 タスクばらし
### プラクティス『rubygems の基本を理解する』の修了
- [ ] 各参考ページを確認
- [ ] `gem`コマンドを使用して`debug.gem`をインストールし、FizzBuzz のプログラムで使ってみること
- [ ] デバッガとデバッグを使い分けられるプログラマになる

------------

## 🐾 スモールステップ
<details><summary>各参考ページを確認</summary>

- [x] [RubyGems Guides](https://guides.rubygems.org/)
- [x] [ライブラリ（ruby-lang.org）](https://www.ruby-lang.org/ja/libraries/)
- [x] [Rubyist Magazine - シリーズパッケージマネジメント【第1回】RubyGems（1）](https://magazine.rubyist.net/articles/0006/0006-PackageManagement.html)
- [x] [RubyGems Wikipedia](https://ja.wikipedia.org/wiki/RubyGems)
- [ ] [Docs：debug.gemの使い方を学ぶ](https://bootcamp.fjord.jp/pages/how-to-use-debug-gem)
- [ ] [デバッグ？デバッガ？debug.gem?あなたが言いたいのはどれ？？|FJORD BOOT CAMP](https://bootcamp.fjord.jp/articles/75)

</details>


<details><summary>gemコマンドを使用して debug.gem をインストールし、FizzBuzz のプログラムで使ってみること</summary>

- [ ] 1. debug.gem のインストール
- [ ] 2. FizzBuzzプログラムに debug を使用する

</details>


<details><summary>デバッガとデバッグを使い分けられるプログラマになる</summary>

- [ ] [Docs：debug.gemの使い方を学ぶ](https://bootcamp.fjord.jp/pages/how-to-use-debug-gem)の内容を咀嚼し、用語を使い分けられるようになること

</details>

------------

## 🧑🏻‍💻 本日の取り組み
### プラクティス『rubygems の基本を理解する』
- 内容の確認
- タスクばらし・スモールステップの作成
- [RubyGems Guides](https://guides.rubygems.org/)
- [ライブラリ（ruby-lang.org）](https://www.ruby-lang.org/ja/libraries/)
- [Rubyist Magazine - シリーズパッケージマネジメント【第1回】RubyGems（1）](https://magazine.rubyist.net/articles/0006/0006-PackageManagement.html)
- [RubyGems Wikipedia](https://ja.wikipedia.org/wiki/RubyGems)

------------

## 💡 本日の学び・気付き
### RubyGems とは？
RubyGems は、Rubyプログラミング言語専用の**パッケージマネージャー**である。
- パッケージマネージャー：他の開発者が作ったライブラリやツール（これを「Gem」と呼んでいる）を簡単に**インストール・管理・共有**ができるシステムを指す。
- ライブラリ：プログラムを作成するときに、一般的な機能や便利なツールを提供する規制のコードの集まりのことを指す。

Ruby のライブラリは「**Gem**」と呼ばれている。Gem は RubyGems を通じてインストール・管理・共有される。

### RubyGems の主な機能
1. インストール
- `gem install <gem_name>`コマンドを使い、必要な Gem をインストールする。
- 例：`gem install rails`で Ruby on Rails をインストール。

2. アンインストール
- 不要になった Gem を削除するために`gem uninstall <gem_name>`コマンドを使う。
- 例：`gem uninstall rails`で Ruby on Rails をアンインストール。

3. 一覧表示
- インストールされている Gem の一覧を表示するために`gem list`コマンドを使う。
- 例：`gem list`で現在インストールされている Gem の一覧が表示される。

4. アップデート
- インストールされている Gem を最新バージョンに更新するために`gem update`コマンドを使う。
- 例：`gem update rails`で Ruby on Rails を最新バージョンに更新。

5. 検索
- インターネット上のGemリポジトリから特定の Gem を検索するために`gem search <gem_name>`コマンドを使う。
- 例：`gem search rails`で Ruby on Rails に関連する Gem を検索。

6. Help!
- ドキュメントをターミナルで参照することができる。
- 例：`gem help` 

7. 自分で Gem を作成
- Gem は自分で作ることができる。これは、他の開発者が作成した便利な機能を使うだけでなく、自分で新しい機能やツールを作成して共有することができる。

------------

## ⏭️ 次回
### プラクティス『rubygems の基本を理解する』
- [Docs：debug.gemの使い方を学ぶ](https://bootcamp.fjord.jp/pages/how-to-use-debug-gem)
- [デバッグ？デバッガ？debug.gem?あなたが言いたいのはどれ？？|FJORD BOOT CAMP](https://bootcamp.fjord.jp/articles/75)

------------

## ✍🏻 感想
### 🤔💭 昔を思い出す
独学時、書籍『現場で使える Ruby on Rails 5速習実践ガイド』を参考に`bundler`や`RubyGems`などを導入したことをふと思い出しました。当時は質問できる相手がいなかったため、手探りの状態が続き、常に不安が付き纏っていました......「本当に効率の悪い勉強をしていたなぁ」としみじみ。

今は学習方法がしっかり確立された FBC のプラクティスがありますので安心です。今回のプラクティスも知識を吸収します。

### 🥱 睡眠不足は敵だ🙅‍♂️
睡眠不足故に常時頭がぼーっとしていました。いつも学んだ内容はできるだけ自分の言葉に変換してまとめているのですが、本日はとっても怪しいです。今夜は早寝しようね、自分。

------------

## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 5 hours 01 min
- Total: 603 hours 10 min
