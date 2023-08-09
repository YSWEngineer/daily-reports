# 2023/08/09(水) 日報

## 取り組んだ課題
### 『pecoとghqを導入する』
- 「pecoとghqで今より2倍速くコーディングしよう」を視聴

---

## 分かったこと・気付き
### 『ghp』の導入、『peco』 と 『ghp』との組み合わせ
※　[x-motemen/ghq](https://github.com/x-motemen/ghq) 、[zshにpeco + ghqを導入したメモ](https://qiita.com/ysk_1031/items/8cde9ce8b4d0870a129d) 、[ghqとpecoでリポジトリの管理を便利にする](https://zenn.dev/obregonia1/articles/e82868e8f66793) 3つのサイトを参考に行いました。
#### 作業手順
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
- 

---

## 感じたこと
tomoyaさんの動画を繰り返し視聴して、先ず peco と ghq とは何なのかを知り、理解することに努めました。
次に peco を導入するための過程を一つずつ丁寧に行いました。この時、意識していたのは「何をどうするのか?」「今の作業がどのように変化して、次に繋がるのか?」の2点です。

独学時は「何となくこんな感じかな」とキーボードを叩いていたのですが、HCの学習のお陰で英文の説明を一文ずつできるだけ正確に訳し、自分の中で消化して、エラーを一度も出すことなく作業できました。次もこの調子で ghq の導入と peco と ghq の組み合わせを成功させたいと思います。

---

## 学習時間
- Today:&nbsp;&nbsp; 3 hours 48 min
- Total: 435 hours 15 min
