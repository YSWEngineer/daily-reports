# 2023/08/09(水) 日報

## 取り組んだ課題
### 『pecoとghqを導入する』
- 「pecoとghqで今より2倍速くコーディングしよう」を視聴

---

## 分かったこと・気付き
### 『ghp』の導入、『peco』 と 『ghp』との組み合わせ
#### 作業手順
※[x-motemen/ghq](https://github.com/x-motemen/ghq) 、[zshにpeco + ghqを導入したメモ](https://qiita.com/ysk_1031/items/8cde9ce8b4d0870a129d) 2つのサイトを参考に行いました。
1. （peco と ghq は Go製のツールなので）ターミナルでGoをインストールする（数十秒で完了）　`% brew install go`
2. （シェルが zsh の場合） ~/.zshrcファイルにパスを設定する
    - ターミナルで `vi ~/.zshrc` を入力して `~/.zshrc` ファイルを表示 → 下記のコマンドを追記 → ファイルの保存・終了
```zsh
# 下記を追記する
export GOPATH=$HOME
export PATH=$PATH:$GOPATH/bin
```
3. ターミナルで `% source ~/.zshrc` を入力・実行、または、ターミナルを再起動
4. ghqのインストール `% brew install ghq` （数十秒で完了）
5. （続けてターミナルで） ghqで管理するrootディレクトリを設定（ [x-motemen/ghq](https://github.com/x-motemen/ghq) では ~/src とする） 下記のコードを入力 → return
```zsh
% git config --global ghq.root '~/src'
```

6. peco と ghq とを組み合わせる
    - ghqの管理下にあるリポジトリを一覧表示するキーバインドを設定する
      - `vi ~/.zshrc` で `~/.zshrc` ファイルを表示して、下記のコードを追記 → ファイルの保存・終了
```zsh
# 下記を追記する
function peco-src () {
  local selected_dir=$(ghq list -p | peco --query "$LBUFFER")
  if [ -n "$selected_dir" ]; then
    BUFFER="cd ${selected_dir}"
    zle accept-line
  fi
  zle clear-screen
}
zle -N peco-src
bindkey '^]' peco-src
```     

7. 念のため、ターミナルで `% source ~/.zshrc` を入力・実行、または、ターミナルを再起動

---

## 次の目標
- 『VSCodeの使い方を学ぶ』
- 『最強WEB問題集　LinuC Lv1-101(Ver10.0)』
- 『gitの基本を身につける』

---

## 感じたこと
昨日に引き続き、tomoyaさんの動画を繰り返し視聴してghqの概要を知り、エラーなく無事に導入とpecoの組み合わせを行いました。
次の『Git & GitHub』の学習では、新しく更新された『VSCodeの使い方を学ぶ』と以前の課題にありました『最強WEB問題集　LinuC Lv1-101(Ver10.0)』にも着手したいと考えています。

---

## 学習時間
- Today:&nbsp;&nbsp; 6 hours 07 min
- Total: 441 hours 22 min
