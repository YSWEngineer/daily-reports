# 2024/11/09(土)

## 🧩 タスクばらし
### プラクティス『rubygems の基本を理解する』の修了
- [ ] 各参考ページを確認
- [x] `gem`コマンドを使用して`debug.gem`をインストールし、FizzBuzz のプログラムで使ってみること
- [ ] デバッガとデバッグを使い分けられるプログラマになる

------------

## 🐾 スモールステップ
<details><summary>各参考ページを確認</summary>

- [x] [RubyGems Guides](https://guides.rubygems.org/)
- [x] [ライブラリ（ruby-lang.org）](https://www.ruby-lang.org/ja/libraries/)
- [x] [Rubyist Magazine - シリーズパッケージマネジメント【第1回】RubyGems（1）](https://magazine.rubyist.net/articles/0006/0006-PackageManagement.html)
- [x] [RubyGems Wikipedia](https://ja.wikipedia.org/wiki/RubyGems)
- [ ] [Docs：debug.gemの使い方を学ぶ](https://bootcamp.fjord.jp/pages/how-to-use-debug-gem)
   - [x] [rubygems (debug.gem)の使い方 - YouTube](https://www.youtube.com/watch?v=4r7-uN3RvNA)
   - [ ] [byebugの良さを教えてください！ | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/questions/1162)
   - [ ] [Ruby 3.1 の debug.gem を自慢したい - クックパッド開発者ブログ](https://techlife.cookpad.com/entry/2021/12/27/202133)
   - [ ] [VS Codeでターミナルからの入力を伴うRubyプログラムをデバッグ実行する方法 - Qiita](https://qiita.com/jnchito/items/3254118d666ef1ea2923)
   - [ ] [Railsをステップ実行する方法を学ぶ（VS CodeとRubyMine） | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/pages/how-to-debug-rails)
- [ ] [デバッグ？デバッガ？debug.gem?あなたが言いたいのはどれ？？|FJORD BOOT CAMP](https://bootcamp.fjord.jp/articles/75)

</details>


<details><summary>gemコマンドを使用して debug.gem をインストールし、FizzBuzz のプログラムで使ってみること</summary>

- [x] 1. debug.gem のインストール
- [x] 2. FizzBuzzプログラムに debug を使用する

</details>


<details><summary>デバッガとデバッグを使い分けられるプログラマになる</summary>

- [ ] [Docs：debug.gemの使い方を学ぶ](https://bootcamp.fjord.jp/pages/how-to-use-debug-gem)の内容を咀嚼し、用語を使い分けられるようになること

</details>

------------

## 🧑🏻‍💻 本日の取り組み
### カレンダーのプログラム（Ruby）
- ファイルに実行権限を付与して再提出

------------

## 💡 本日の学び・気付き
### 【復習】
#### ファイルのパーミッション
- 1つ1つのファイルには「**誰に、どのような操作を許可するか？**」という権限を規定する情報が設定されている。この情報のことを**パーミッション**と呼ぶ。
- ファイルのパーミッションは、`ls`コマンドに`-l`オプションを付けることで確認できる。
- `-l`オプションで表示される先頭の1文字はファイルタイプで`-`は通常ファイル、`d`はディレクトリ、`l`はシンボリックリンクを表す。
   - シンボリックリンク：ファイルやディレクトリのリンクを作成するファイルのことで、ファイルやディレクトリの代理人ファイルのようなもの。
- ファイルタイプの後ろの9文字は、**ファイルモード**と呼ばれ、これによってファイルのパーミッションを表している。この9文字は、3文字ごとに1つのブロックになっていて、それぞれが左から**user：オーナー、group：グループ、others：その他のユーザ**に対するパーミッションを意味している。
- `r`、`w`、`x`といった記号は、許可されるファイルへの操作を意味している。操作は**read：読み取り、write：書き込み、execute：実行**の3種類あり、それぞれ`r`、`w`、`x`の記号でパーミッションが表現されている。
- `ls`コマンドの`-l`オプションでは、操作が許可されているときは`r`、`w`、`x`という記号が表示され、逆に許可されていないときは`-`が表示される。

##### chmodコマンドでファイルモードを変更する
- ファイルやディレクトリのパーミッションを設定するには、ファイルモードを変更する`chmod`コマンドを使用する。
- `chmod`コマンドには「**シンボルモード**」による指定と「**数値モード**」による指定の2種類の方法があり、どちらもよく使われる。
###### シンボルモード
書式：シンボルモードによるパーミッションの変更
```shell
chmod [ugoa][+-=][rwx] <ファイル名>
```
- シンボルモードの指定は、「誰に、どのような権限を追加（もしくは禁止）するのか」というのが分かりやすくなっている。
- `a`：`u`、`g`、`o`全て（**a**ll）、という意味。
- なお、ユーザ指定を省略すると、`a`を指定したものとみなされる。
- 例：シンボルモードでの指定
```shell
#「file.txtファイルにオーナーが書き込み権限を追加せよ」という意味
% chmod u+w file.txt
```
- 例：複数のユーザの権限をまとめて指定
```shell
# file.txtファイルにグループとその他のユーザの権限を読み込み権限だけにせよ」という意味
% chmod go=r file.txt
```
- シンボルモードは相対的な指定方法、つまり、指定したパーミッション以外は変化しないということ。これは、「オーナーの権限のみ」など**パーミッションの一部だけを変更したいときに便利**。

###### 数値モード
書式：数値モードによるパーミッションの変更
```shell
chmod <8進数の数値> <ファイル名>
```
- 数値モードは**元のパーミッションに関わらず新しいパーミッションの値へと変更する**、絶対指定の方法。
- パーミッションを数値で表現するには、rwxのうち許可する操作を以下の表のとおりの数字に置き換えて、それを足し算する。足した値を、「オーナー」「グループ」「そのほかのユーザ」の順に3つ並べて指定する。この3桁の数字がパーミッションを指定するための値となる。例えば、`rwxr-xr-x`というパーミッションは、数値に変換すると「**755**」となる。

| 意味 | 数字 |
|:---------|:---------:|
| 読み取り（r）  | 4 |
| 書き込み（w）  | 2 |
| 実行（x）  | 1 |

- オーナー：`rwx`=> 4 + 2 + 1 = **7**
- グループ：`r-x` => 4 + 0 + 1 = **5**
- そのほかのユーザ：`r-x` => 4 + 0 + 1 = **5**

- 例：`chmod`コマンドに**755**を指定することで、元のパーミッションが何であれ、`rwxr-xr-x`というパーミッションに変更される。
```shell
desktop % chmod 755 newfile.txt
desktop % ls -l newfile.txt
-rwxr-xr-x  1 yoshiwo  staff  31 11  9 15:34 newfile.txt
```

------------

## ⏭️ 次回
### Advent Calendar
- 記事の草稿作成

### プラクティス『rubygems の基本を理解する』
- [Docs：debug.gemの使い方を学ぶ](https://bootcamp.fjord.jp/pages/how-to-use-debug-gem)
   - [byebugの良さを教えてください！ | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/questions/1162)
   - [Ruby 3.1 の debug.gem を自慢したい - クックパッド開発者ブログ](https://techlife.cookpad.com/entry/2021/12/27/202133)
   - [VS Codeでターミナルからの入力を伴うRubyプログラムをデバッグ実行する方法 - Qiita](https://qiita.com/jnchito/items/3254118d666ef1ea2923)
   - [Railsをステップ実行する方法を学ぶ（VS CodeとRubyMine） | FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/pages/how-to-debug-rails)

------------

## ✍🏻 感想
### 🏋🏻 何事も経験
ファイルに実行権限を付与して再提出を行いました。今回はファイルの消失が分からなかったとしても、Gitの実践は、繰り返し経験することで理解を深めたり慣れていくものだと感じました。GitHub では好きにリポジトリを作れますので、練習用のリポジトリを作成して試行錯誤を重ねていこうと思います。

------------

## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 5 hours 47 min
- Total: 631 hours 15 min
