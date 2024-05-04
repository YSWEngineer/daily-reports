# 2023/05/03(金)
## 🕺 日頃からの意識
<details><summary>日頃からの意識</summary>

- 成長スピードを早めよう。
- 自分の考えや気持ちを簡潔に言語化したり、相手にわかりやすく伝える話し方ができるようになろう。
- 心と身体の状態を把握しながら行動しよう。
- 腕立て・スクワット・腹筋・ストレッチを継続しよう。
- 説明文をよく読もう。ここでの「読む」は内容を認識・把握すること。
- 体調の回復に努めて、行動の範囲を元に戻そう。
- Git & GitHub とお友達になろう。
- RubyKaigi 当日まで Ruby についてできる限り学ぶこと。
- 「何を、どうするのか」という意識を常に持ちながらプラクティスに臨むこと。
</details>

---


## 📝 プラクティス『rbenv』の段取り
<details><summary>段取り</summary>

- [x] 各参考ページを確認
  - [x] [rbenv](https://github.com/rbenv/rbenv)
  - [x] [Rails Girls インストール・レシピ](https://railsgirls.jp/install)
  - [x] [Rubyist Hotlinks](https://magazine.rubyist.net/articles/0001/0001-Hotlinks.html#rubyist-hotlinks-%E9%80%A3%E8%BC%89%E4%B8%80%E8%A6%A7)
  - [x] [参考](https://twitter.com/yhara/status/1004335849377431552)
  - [x] [ruby-jp](https://ruby-jp.github.io/)
  - [x] [Rubyコミュニティの魅力は「大人力の高さ」](https://logmi.jp/tech/articles/321632)
  - [x] [公式サイト](https://www.ruby-lang.org/ja/downloads/)
  - [x] [他の人の提出物](https://bootcamp.fjord.jp/practices/24/products)
- [x] 課題に取り組む
   - [ ] Rubyの安定版の最新バージョンをインストールする。
      - [ ] 公式サイトを見て安定版の最新バージョンのバージョン番号を確認をすること。
   - [ ] system 以外の複数のバージョンのRubyを切り替えることができる。
   - [ ] ruby -vコマンドでバージョンが切り替わっていることが確認できる。
   - [x] rbenvの設定状況を確認する。
</details>

---


## 🗓️ 今週の ToDo
<details><summary>今週の ToDo</summary>

- [x] プラクティスの内容を確認
- [x] プラクティスの段取りを作成
- [x] 各参考ページを確認
  - [x] [rbenv](https://github.com/rbenv/rbenv)
  - [x] [Rails Girls インストール・レシピ](https://railsgirls.jp/install)
  - [x] [Rubyist Hotlinks](https://magazine.rubyist.net/articles/0001/0001-Hotlinks.html#rubyist-hotlinks-%E9%80%A3%E8%BC%89%E4%B8%80%E8%A6%A7)
  - [x] [参考](https://twitter.com/yhara/status/1004335849377431552)
  - [x] [ruby-jp](https://ruby-jp.github.io/)
  - [x] [Rubyコミュニティの魅力は「大人力の高さ」](https://logmi.jp/tech/articles/321632)
  - [x] [公式サイト](https://www.ruby-lang.org/ja/downloads/)
  - [x] [他の人の提出物](https://bootcamp.fjord.jp/practices/24/products)
- [x] 課題に取り組む
   - [ ] Rubyの安定版の最新バージョンをインストールする。
      - [ ] 公式サイトを見て安定版の最新バージョンのバージョン番号を確認をすること。
   - [ ] system 以外の複数のバージョンのRubyを切り替えることができる。
   - [ ] ruby -vコマンドでバージョンが切り替わっていることが確認できる。
   - [x] rbenvの設定状況を確認する。
</details>

---


## ✍🏻 本日の取り組み
- プラクティス『rbenv』
   - 各参考ページの確認
      - [ruby-jp](https://ruby-jp.github.io/)
      - [公式サイト](https://www.ruby-lang.org/ja/downloads/)
      - [他の人の提出物](https://bootcamp.fjord.jp/practices/24/products)
   - rbenv の設定状況を確認
      - brew doctor コマンドで表示された Warning を対処

---


## 💡 本日の学び・気付き
<details><summary>brew docter</summary>

`brew docter`を入力したところ
```shell
Your system is ready to brew.
```
ではなく、
```shell
Warning: A newer Command Line Tools release is available.
Update them from Software Update in System Settings.

If that doesn't show you any updates, run:
  sudo rm -rf /Library/Developer/CommandLineTools
  sudo xcode-select --install

Alternatively, manually download them from:
  https://developer.apple.com/download/all/.
You should download the Command Line Tools for Xcode 15.1.

Warning: Some installed formulae are missing dependencies.
You should `brew install` the missing dependencies:
  brew install openssl@1.1

Run `brew missing` for more details.
```
2つの`Warning（警告）`が表示されました。

## 1つ目の ⚠️Warning
```shell
Warning: A newer Command Line Tools release is available.
Update them from Software Update in System Settings.

If that doesn't show you any updates, run:
  sudo rm -rf /Library/Developer/CommandLineTools
  sudo xcode-select --install

Alternatively, manually download them from:
  https://developer.apple.com/download/all/.
You should download the Command Line Tools for Xcode 15.1.
```
「警告：新しくリリースされた Command Line Tools が利用可能です。
システム設定のソフトウェアアップデートからアップデートしてください。

もしどのアップデートも表示されなかったら、以下を実行してください。
sudo rm -rf /Library/Developer/CommandLineTools
sudo xcode-select --install

あるいは、以下から手動でダウンロードが可能です：
https://developer.apple.com/download/all/.
あなたは Command Line Tools for Xcode 15.1. をダウンロードすべきです」

### 対処方法
今回のプラクティスの内容に`無闇にsudoは使うべからず`と載っていたので [https://developer.apple.com/download/all/](https://developer.apple.com/download/all/) から「Command Line Tools for Xcode 15.1」をダウンロードしました。

![スクリーンショット 2024-05-04 7.54.26.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMXFKQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--356cc44b77e0002c6d02855a9a99372b4f060bd1/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-05-04%207.54.26.png)

## 2つ目の ⚠️Warning
```shell
Warning: Some installed formulae are missing dependencies.
You should `brew install` the missing dependencies:
  brew install openssl@1.1

Run `brew missing` for more details.
```
「警告：あるインストールしたフォーミュラが依存状態（正確には**一部依存状態**）ではありません。
依存（状態）を『brew install』すべきです：
brew install opennssl@1.1

詳細は『brew missing』を実行してください」

### 対処方法
`brew missing`を入力。以下の内容が表示されたので調べてみると`iproute2mac`と`python@3.10`が`openssl@1.1`に依存している（けれど、`openssl@1.1`が一部不足している）ことがわかります。

ですが現在`openssl@1.1`は非推奨で、代わりに最新バージョンの`poenssl`を使用することが推奨されています。そのため一度`openssl@1.1`をアンインストールし、新たに`openssl`を再インストールします。

さらに`openssl@1.1`パッケージをアンインストールし、再インストールすることで新しいバージョンの`openssl`に依存（状態に）するようにできるようになります。
```shell
brew missing
iproute2mac: openssl@1.1
python@3.10: openssl@1.1
```

#### 手順 1
以下のコマンドを入力して`openssl@1.1`をアンインストール。
```shell
brew uninstall --ignore-dependencies openssl@1.1
```

#### 手順 2
`iproute2mac`と`python@3.10`をアンインストール。
```shell
# iproute2macとpythonを一度にまとめてアンインストールすることが可能
brew uninstall --ignore-dependencies iproute2mac python@3.10
``` 

#### 手順 3
`iproute2mac`と`ptyhon@3.10`を再インストール。
```shell
# iproute2macとpythonを一度にまとめて再インストールすることが可能
brew install iproute2mac python@3.10
```

#### 確認
`brew doctor`を入力。無事に`Your system is ready to brew.`が表示されました。
![スクリーンショット 2024-05-04 8.44.15.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMStKQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--92375cb2a22a6151b11307a6b2eaa4de53693113/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-05-04%208.44.15.png)
</details>

---


## 📍 次回
- プラクティス『rbenv』
   - 提出物の作成、提出。

---


## ❤️‍🔥 感想
### 🧑🏻‍⚕️🩺 brew doctor にハマる
まさかの ⚠️Warning。しかも2つ。とりあえず気持ちを落ち着かせ「**黒い画面が教えてくれている`Warning`を訳して、意味を知り、理解する → 解決方法をググる → 得た情報を精査する → 実際に行う**」という流れで無事に解決できましたが「**解決方法をググる → 得た情報を精査する**」作業に時間が掛かってしまいました。

そのやり方としては「**①Qiita、Zenn、ブログ、Copilot GPTから情報を入手 → ②得た情報を一つずつ箇条書きでレポート用紙に書く → ③共通項を見つけてピックアップ → ④ピックアップした内容をまとめてそれを検索ワードとしてググったり、Copilot GPTで確かめる**」という方法です。

検索して出てきた情報を鵜呑みすることに留意しながら慎重に行いました。「Ruby の安定版の最新バージョンをインストールして、提出物を提出してどんどん行くぞ」と息巻いていた私にとって思わぬ躓きではありましたがとても良い経験を積み重ねることができました。「何事も経験」をモットーにしているので、むしろ躓いて良かったです。

---


## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 2 hours 33 min
- Total: 298 hours 38 min
