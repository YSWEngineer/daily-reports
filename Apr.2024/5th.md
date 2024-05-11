# 2023/04/05(金)
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
- [x] ターミナルからリモートリポジトリを push できるようにする

---


## ✍🏻 本日の取り組み
- GitHub CLI をインストール
- 【連載】マンガでわかるGit ～コマンド編～
   - 第2話 ブランチとは？ポインタってどういう意味？作成・確認・切り替え方法
- Git-it
  - 5. Remote Control：ローカルの repository を GitHub.com の repository に接続（途中から）
---


## 💡 本日の学び・気付き
<details><summary> GitHub CLI をインストール</summary>
  
### GitHub CLI を使う方法を選択
前回の学習ではリモートリポジトリに push できるようになるには

1. Personal Access Token(PAT) を使った認証
2. GitHub に SSH 接続する方法
3. GitHub CLI をインストールする方法

以上の3つ方法があることがわかりました。
その中から「GitHub CLI をインストールする方法」を選択し、受講生の[Q&A](https://bootcamp.fjord.jp/questions/1654#answer_6059)を参考にGitHub CLI をインストールし、無事にリモートリポジトリに push することができました。
```
git push origin main
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (6/6), 497 bytes | 497.00 KiB/s, done.
Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/YSWEngineer/hello-world.git
 * [new branch]      main -> main
```

</details>

<details><summary>第2話 ブランチとは？ポインタってどういう意味？作成・確認・切り替え方法【連載】マンガでわかるGit ～コマンド編～</summary>
### mainブランチ
- mainブランチ：`git init`でリポジトリを作ったときから存在しているブランチのこと。

### ブランチの正体
mainブランチの正体は、mainファイルのこと。このmainファイルの中身は英数字の羅列ある。この羅列は「**コミットID**」「**コミットハッシュ値**」と呼ばれる。コミットIDは、コミットによって生成された「**コミットオブジェクト**」に対して割り当てられる。つまり、ブランチは`main` → `コミットID` → `コミットオブジェクト`と、単に特定のコミットIDを指差しているだけ。

### コミットIDは何を元に作られているのか？
コミットID（コミットハッシュ値）は、コミットオブジェクトのバイト数と中身を使い、計算されて作られている。

### 基本的なコマンド
- git branch：今、存在するブランチの一覧が表示される。
- git branch [ファイル名]：新しいブランチを作る。
- git chackout [ブランチ名]：任意のブランチへ移動する。
   - git checkout -b [ブランチ名]：ブランチの作成とチェックアウトを同時に行う。
   - git checkout -f [ブランチ名]：ブランチを強制的に切り替えることができる（コミットしていない作業データは消えるので注意）。
</details>

:::details Git-it
### remote の設定を追加する
`git remote add <REMOTENAME> <URL>`

### すでにある remote に URL を設定する
`git remote set-url <REMOTENAME> <URL>`

### 変更を pull する
`git pull <REMOTENAME> <BRANCHNAME>`

### remote の設定を確認する
` git remote -v`

### 変更を push する
`git push <REMOTENAME> <BRANCH>`
:::

---


## 📍 次回
- 【連載】マンガでわかるGit ～コマンド編～
   - 第3話 マージの仕組みを見てみよう
- Git-it
   - 6. Forks and Clones オープンソースの repository を fork して clone する

---


## ❤️‍🔥 感想
#### 🐙🐈‍⬛ 小さな一歩
「push できるようになった」という小さな一歩でしたが、前に進められてよかったです。ちゃんと調べて、調べた内容を精査して、その内容を分かりやすくまとめたことが功を奏したのかなと思います。

---

## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 2 hours 35 min
- Total: 255 hours 13 min
