# 2023/04/03(水)
## 🕺 日頃からの意識
- 成長スピードを早めよう。
- 自分の考えや気持ちを簡潔に言語化したり、相手にわかりやすく伝える話し方ができるようになろう。
- 心と身体の状態を把握しながら行動しよう。
- 腕立て・スクワット・腹筋・ストレッチを継続しよう。
- 説明文をよく読もう。ここでの「読む」は内容を認識・把握すること。
- 体調の回復に努めて、行動の範囲を元に戻そう。
- Git & GitHub とお友達になろう。
- 5月の RubyKaigi までにプラクティスを Ruby まで進めよう。

---


## 🌞 3つの目標
#### 🌝 大目標：4月の中旬までに Ruby に取り組む
#### 🌜 中目標：Git & GitHub 修了
#### 🌚 小目標：プラクティス『GitHub の基本を理解する』に着手

---


## 🗓️ プラクティス『GitHub の基本を理解する』の段取り
- [x] 各参考ページを確認
  - [x] [こちらの日報](https://bootcamp.fjord.jp/reports/24447#comment_48036)
  - [x] [こちらの issue](https://github.com/jlord/patchwork/issues/27932)
  - [x] [GitHubを使ってみよう！導入と簡単な流れ、よく使うコマンドなど](https://wp.yat-net.com/?p=3874)
  - [x] [git pull と git pull –rebase の違いって？図を交えて説明します！](https://kray.jp/blog/git-pull-rebase/)
  - [x] [初心者でも分かる！git rebaseの使い方を解説します](https://liginc.co.jp/web/tool/79390)
  - [x] [「今度こそ理解する Git reset」 （LT会での masuyama13さんの発表 ）](https://speakerdeck.com/masuyama13/git-reset-200822)
  - [x] [tigを入れておくと便利。](https://qiita.com/suino/items/b0dae7e00bd7165f79ea)
  - [x] [gitignore_globalでgit管理するファイルをグローバルで設定する](https://qiita.com/miyarappo/items/66d6212d312a68fa3b99)
  - [x] [GitHub、これから作成するリポジトリのデフォルトブランチ名が「main」に。「master」から「main」へ変更 － Publickey](https://www.publickey1.jp/blog/20/githubmainmastermain.html)
  - [x] [自分がGitHubへプッシュしたのにコミットのアイコンが自分じゃない - Just do IT](https://k-koh.hatenablog.com/entry/2020/02/01/160119)
- [x] Git-it に取り組む
- [ ] 提出物の作成
- [ ] 提出物の提出


---


## 🗓️ 今週の ToDo
- [x] Git-it に取り組む
  - [x] 1. Get Git Git をインストールして設定をする
  - [x] 2. Repository ローカルの repository を作成
  - [x] 3. Commit to it ステータスを確認して、コンテンツを追加してcommitをする
  - [x] 4. GitHubbin GitHub のアカウントを作成
  - [x] 5. Remote Control ローカルの repository を GitHub.com の repository に接続
  - [ ] 6. Forks and Clones オープンソースの repository を fork して clone する
  - [ ] 7. Branches aren't just for Birds 新機能・修正のために branch を作成
  - [ ] 8. It's a Small World Collaborator を追加して作業を同期する
  - [ ] 9. Pull, Never Out of Date 修正を GitHub.com と同期するために push と pull を行う
  - [ ] 10. Requesting You Pull Please Pull request を作成
  - [ ] 11. Merge Tada Branch を merge して delete(削除)する


---


## ✍🏻 本日の取り組み
- 【連載】マンガでわかるGit ～コマンド編～
   - 第1話 リポジトリを作ってコミットしてみよう
- Git-it
   - 5. Remote Control：ローカルの repository を GitHub.com の repository に接続（途中まで）
---


## 💡 本日の学び・気付き
:::details 第1話 リポジトリを作ってコミットしてみよう【連載】マンガでわかるGit ～コマンド編～
### GUI と CLI の違い
- GUI（Graphical User Interface）：GUI は、グラフィカルユーザーインターフェースの略で、視覚的な要素（アイコン、ウィンドウ、ボタンなど）を使用してユーザーとコンピューターが対話する方法。基本的にマウスやタッチスクリーンを使い操作を行う。
- CLI（Command Line Interface）：CLIは、コマンドラインインターフェースの略で、テキストベースのインターフェースを提供する。ユーザーはキーボードを使ってコマンドを入力し、コンピューターに指示を出す。

### GUI ソフトの種類
- SourceTree
- GitKraken
- GitHub Deskop

### CLI のメリット
- 操作がシンプル。
- CLI にしかできない操作がある。

### Git がインストール済みか確認
以下のコマンドを入力して Git がインストール済みかどうか確認できる。
```
git --version
```

### 基本的なコマンド
- pwd：「Print Working Directory」の略。自分が今いるディレクトリ（階層）を表示。
- ls：「List Segments」の略。自分が今いるディレクトリ（階層）の直下にあるものが表示。
- cd：「Change Directory」の略。ディレクトリへの移動。
- mkdir：「MaKe DIRectory」の略。新しいディレクトリを作成。
- git status：状況を確認。
- git add：ステージする（ファイルをステージングエリアに乗せる）。
- git commit：コミットする。
- git log：履歴を見る。

### git add と git commit のイメージの言語化
- git add：作成したファイルを撮影台の上で記録されるのを待っている状態にする（ファイルをステージングエリアに乗せる）。
- git commit：撮影台に乗っているものをカメラで撮って、アルバム（＝リポジトリ）に記録する。
:::

:::details Git-it
### Remote（リモート）と Local（ローカル）
- Remote：Remote はネットワークを通じてアクセスする他のコンピューター上のリソースやデータを指す。GitHub ではGitHub のサーバー上に存在しているデータ（リポジトリ）のこと。
- Local：Local は自分のコンピューター上のリソースやデータのこと。
:::

---


## 📍 次回
- GitHub
   - パーソナルアクセストークンとSSHキーの設定
-  Git-it
   - 5. Remote Control：ローカルの repository を GitHub.com の repository に接続（途中から）

---


## ❤️‍🔥 感想
#### ✍🏻 コツコツを続ける
学習中に「 手堅く着実に物事を進めることが大事なんだよね」と、ふと思い出しました。何故そのように思い出したのかは分かりませんが、コツコツを続けていくことが目標達成の近道なのかもしれませんね。

#### 🐙🐈‍⬛ パーソナルアクセストークンと SSHキーどちら？
GitHubにおいてパスワード認証が廃止されたため、パーソナルアクセストークンまたは SSHキーが必要になりました。次回はこの2つの設定を行います。

---

## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 2 hours 48 min
- Total: 250 hours 27 min
