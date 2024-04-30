# 2023/04/04(木)
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
- [ ] ターミナルからリモートリポジトリを push できるようにする **←New**✨

---


## ✍🏻 本日の取り組み
- GitHub Docs
   - [About remote repositories](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories)
---


## 💡 本日の学び・気付き
<details><summary>About remote repositories</summary>
### リモートリポジトリに push できない
ターミナルで`git push origin main`を入力すると以下の内容が表示。
```
git push origin main
Username for 'https://github.com':
Password for 'https://YSWEngineer@github.com': 
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
```
- 2021年8月13日にパスワード認証のサポートがなくなった。
- リモートリポジトリにおいて、現在推奨されている認証モードについての情報は GitHub Docs を参照すること。

とあったので、[About remote repositories](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories)でリモートリポジトリと現在推奨されている認証モードについて調べることになりました。

### push できるアドレス
`push`ができるのは2種類のアドレスだけ
- HTTPS の URL (例: https://github.com/user/repo.git)
- SSH の URL (例: git@github.com:user/repo.git)

### HTTPS の URL の場合
リモートリポジトリに`git clone`, `git fetch`, `git pull`, `git push`を実行した場合、Git では GitHub のユーザー名とパスワードが要求される。 Git からパスワードの入力するダイアログが表示されたら、personal access token（PAT） を入力すること。そして、より安全な認証方法を優先し Git のパスワード認証はなくなったとのこと。

### SSH の URL の場合
コンピューターに SSH キーの組を生成し、GitHub.comのアカウントに公開キーを追加する必要がある。 リモートリポジトリに`git clone`, `git fetch`, `git pull`, `git push`を実行した場合、パスワードの入力を求めるダイアログが表示され、SSH キーのパスフレーズを指定する必要がある。だが、SSHキーを使用するたびにパスフレーズを入力する必要がないように、SSHキーを保護し、認証エージェントを設定することができる。

### GitHub CLI をインストールの場合
GitHub CLI は GitHub の機能をコマンドラインから操作するためのツールで、これによりターミナルから直接、リポジトリの管理、issue  の作成、pull request の作成、merge など、GitHub の主要な機能を利用することができる。

</details>

---


## 📍 次回
- GitHub
   - push できるようになるためのいくつかの方法について詳細に調べる。

---


## ❤️‍🔥 感想
#### 🐙🐈‍⬛ push できるようになるための幾つかの方法
リモートリポジトリに`push`できるようになる方法が幾つかある、ということがわかったので次回はその詳細について調べていきます。Git-it を進められないのは歯痒いですが、一つずつやっていきます。

---

## ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp; 2 hours 11 min
- Total: 252 hours 38 min
