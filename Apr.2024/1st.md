# 2023/04/01(月)
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
  - [ ] 3. Commit to it ステータスを確認して、コンテンツを追加してcommitをする
  - [ ] 4. GitHubbin GitHub のアカウントを作成
  - [ ] 5. Remote Control ローカルの repository を GitHub.com の repository に接続
  - [ ] 6. Forks and Clones オープンソースの repository を fork して clone する
  - [ ] 7. Branches aren't just for Birds 新機能・修正のために branch を作成
  - [ ] 8. It's a Small World Collaborator を追加して作業を同期する
  - [ ] 9. Pull, Never Out of Date 修正を GitHub.com と同期するために push と pull を行う
  - [ ] 10. Requesting You Pull Please Pull request を作成
  - [ ] 11. Merge Tada Branch を merge して delete(削除)する


---


## ✍🏻 本日の取り組み
- git blame について
  - [Git - git-blame Documentation](https://git-scm.com/docs/git-blame)
  - [第13話 どのコミットでバグが入ったかgit blameで調べてみよう【連載】マンガでわかるGit ～コマンド編～ - itstaffing エンジニアスタイル](https://www.r-staffing.co.jp/engineer/entry/20200626_1)
  - [ファイルの表示 - GitHub Docs - ファイルの行ごとのリビジョン履歴の表示](https://docs.github.com/ja/repositories/working-with-files/using-files/viewing-a-file#viewing-the-line-by-line-revision-history-for-a-file)

- Git-it

---


## 💡 本日の学び・気付き
<details><summary>Git - git-blame Documentation</summary>

- `git blame`：特定のファイルの各行が誰によって、いつ作成または最後に変更されたかを表示するコマンド。このコマンドは、バグを見つけた時やコードの理解を深めるために、そのコードがどのコミットで追加または変更されたかを知るのに役立つ。
- 基本的な使い方
```
git blame ファイル名
```
このコマンドを実行すると指定したファイルの各行について、その行を最後に変更したコミットのハッシュ、そのコミットを行った人の名前、そのコミットが行われた日時、その行の内容が表示される。 
</details>

<details><summary>第13話 どのコミットでバグが入ったかgit blameで調べてみよう【連載】マンガでわかるGit ～コマンド編～ - itstaffing エンジニアスタイル</summary>
### git blame の使い方
以下のコマンドで、いつ誰のコミットでその行が変更されたのかを調べられる。
```
git blame [ファイル名]
```
- Gitリポジトリ直下にあるファイルを調べたい場合
例）リポジトリ直下にある「config.yml」というファイルを調べる
```
git blame config.yml
```
- 階層がある場合
例）appフォルダの中にある「app.component.ts」というファイルを調べる
```
git blame src/app/app.component.ts
```
### コミットの先頭にある「^」は......
- コミットIDの先頭に付いている`^`は、そのコミットがイニシャルコミット（最初のコミット）を表している。
</details>

<details><summary>ファイルの表示 - GitHub Docs - ファイルの行ごとのリビジョン履歴の表示</summary>
### ファイルの行ごとのリビジョン履歴の表示
1. GitHub.com でリポジトリのメインページに移動する。
2. 表示したい行の履歴のファイルを開く。
3. ファイルの内容の上にある [Blame] をクリックする。
以上の操作により、ファイル全体のリビジョン履歴を1行ずつ表示できる。このビューには、各コミットによって区切られたファイル内のコードが表示され、各コミットには作成者、コミットの説明、コミットした日が一覧表示される。

また、特定のコミットの前にあるファイルのバージョンを表示するには、特定のアイコンをクリックする。特定のコミットの詳細を表示するには、コミットメッセージをクリックする。

さらに、`.git-blame-ignore-revs`というファイルを使用して、特定のリビジョンを [変更履歴] ビューから除外することも可能。
</details>

<details><summary>Git-it</summary>
### Repositories
- リポジトリとは本質的にはプロジェクト（企画・事業）のこと。

### バージョン管理システム
- ファイルを追加したり、削除したり、ファイルの中に一行足しただけでも、そのようなすべての変更は Git によって追跡され、いつそれを行ったのか記録してくれる仕組み（システム）のこと。

### git init
- `git init`は新しいGitリポジトリを初期化するためのコマンド。このコマンドを実行すると、現在のディレクトリに`.git`という名前の隠しディレクトリが作成される。この`.git`ディレクトリは、リポジトリのメタデータ（他のデータを説明するためのデータのことでここでは、ブランチ、コミット、設定などを指す）を格納する場所で、これがあることでそのディレクトリはGitリポジトリとして機能する。
```
# 新しいリポジトリを初期化する
git init
```
- このコマンドを実行すると、現在のディレクトリが新しいGitリポジトリとして初期化される。これにより、そのディレクトリ内で Git の各種コマンド（`git add`, `git commit`, `git push`など）を使用することができるようになる。
</details>

---


## 📍 次回
-  Git-it
    - 3. Commit to it ステータスを確認して、コンテンツを追加してcommitをする

---


## ❤️‍🔥 感想
#### 🐙🐈‍⬛ 知識を浴びよう
:@betachelsea: さんが教えてくださったサイトがとても分かりやすかったので、理解を深めるためにプラクティスと並行して学ぶことにしました。今は「知識をシャワーのように浴びて吸収したい」ただそれだけです。明日も一歩前へ✨

---

## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 3 hours 08 min
- Total: 246 hours 20 min
