# 2023/03/05(火)
## 🕺今の気持ち
- どんどんプラクティスを進ませよう
- 成長スピードを早めよう
- 自分の考えや気持ちを簡潔に言語化したり、相手にわかりやすく伝える話し方ができるようになろう
- 心と身体の状態を把握しながら行動しよう
- 腕立て・スクワット・腹筋・ストレッチを再開しよう
---


## ✍🏻本日の取り組み
#### プラクティス『SSH の基本を理解する』

---


## 💡学んだこと
<details><summary>表示されたエラーメッセージの対処</summary>

### 表示されたエラーメッセージについて
`ssh-copy-id -i ~/.ssh/id_ed25519.pub -p5555 yoshiwo@160.16.241.119` と入力すると以下の内容が表示されました。
```
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/yoshiwo/.ssh/id_ed25519.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are aleady installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed - - if you are prompted now it is to install the new keys
yoshiwo@160.16.241.119: Permission denied (publickey).
```
`Permission denied(publickey)`（パーミッションは拒否された（公開鍵））とあるので、公開鍵認証がうまくいっていないのかな？パスが間違っているのかな？と推測しました。そこで、問題を解決するための方法を一つずつ試みました。

1. リモートサーバーにパスワード認証でログイン
```
ssh yoshiwo@160.16.241.119 -p5555
yoshiwo@160.16.241.119: Permission denied (publickey).
```
本来ならばパスワードの入力を求められるのですが、エラーメッセージが表示されました。
次に、SSHの設定内容を確認します。

2. SSH設定を確認
このプラクティスの解説にもありますが、確認する場所は2箇所です。
-  PubkeyAuthentication 
-  PasswordAuthentication 
以上の2つが`yes`と（有効に）なっているかどうか確認を行います。
ファイルを開いてみると`PasswordAuthentication`の項目が`no`になっていましたので`yes`に書き直して（設定ファイルの）保存を行います。

3. SSHサーバーの再起動とステータスの確認
以下のコマンドを入力して設定変更した内容の検証と確認を行います。
`sudo service ssh restart`
`sudo service ssh status`

4. 再度、公開鍵をサーバーに登録する作業を行う
パスにも注意して`ssh-copy-id -i /home/yoshiwo/.ssh/id_ed25519.pub -p5555 yoshiwo@160.16.241.119`と入力します。
```
ssh-copy-id -i ~/.ssh/id_ed25519.pub -p5555 yoshiwo@160.16.241.119
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/yoshiwo/.ssh/id_ed25519.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are aleady installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed - - if you are prompted now it is to install the new keys
yoshiwo@160.16.241.119's password:

Number of key(s) added: 1

Now try logging into the machne, with:    "ssh -p '5555' 'yoshiwo@160.16.241.119'"
and check to make sure that only the key(s) you wanted were added.

Yoshiwo@tk2-262-40865:~$ ssh -p5555 yoshiwo@160.16.241.119
# パスフレーズの入力を求められるので設定したパスフレーズを入力
Enter passphrase for key '/home/yoshiwo/.ssh/id_ed25519':
（中略）
Last login: Tue Fed 27 20:33:48 2024 from 160.16.241.119
```
パスワードなしでログインができたことを確認しました。

5. サーバー側で公開鍵が登録されていることを確認
以下の2つのコマンドを入力して確認を行います。
`ls -l <登録された公開鍵のパス>`
`less <登録された公開鍵のパス>`
```
ls -l /home/yoshiwo/.ssh/id_ed25519.pub
-rw-r--r-- 1 yoshiwo yoshiwo 103 Mar    1 14:10 /home/yoshiwo/.ssh/id_ed25519.pub
less /home/yoshiwo/.ssh/id_ed25519.pub
（中略）
/home/yoshiwo/.ssh/id_ed25519.pub (END)
```

6. 公開鍵認証方式で SSH 接続を行う
以下のコマンドを入力してSSH接続を行います。
`ssh <公開鍵認証方式の指定> <22 番以外のポートの指定> <一般ユーザー>@<IP アドレス>`
`hostname`

```
ssh -i /home/yoshiwo/.ssh/id_ed25519.pub -p 5555 yoshiwo@160.16.241.119
（中略）
Last login: Tue Mar  5 15:20:05 2024 from 160.16.241.119
hostname
tk2-262-40865
```

7. パスワード認証方式でも引き続きログインできることを確認
以下のコマンドを入力してログインできることを確認します。
`ssh <パスワード認証方式の指定> <22 番以外のポートの指定> <一般ユーザー>@<IP アドレス>`
`hostname`

```
ssh -p5555 yoshiwo@160.16.241.119
# パスフレーズの入力を求められるので設定したパスフレーズを入力
Enter passphrase for key '/home/yoshiwo/.ssh/id_ed25519':
Linux tk2-262-40865 6.1.0-18-amd64 #1 SMP PREEMPT_DYNAMIC Debin 6.1.76-1 (2024-02-01) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Tue Mar  5 13:02:42 2024 from 160.16.241.119
hostname
tk2-262-40865
```

</details>


<details><summary>パスワード認証方式でのログインを禁止</summary>

##### ①sshコマンドを使用してサーバーにログインします
`ssh -p 5555 yoshiwo@160.16.241.119`

##### ②SSH設定ファイルを開きます
`sudo vim etc/ssh/sshd_config`

##### ③パスワード認証を無効にします
`PasswordAuthentication no`に書き換えて、設定内容を保存してファイルを閉じます。

##### ④サービスの再起動と確認を行います
設定ファイルを変更したら、サービスの再起動を忘れずに行います。サービスの再起動を行ったら、サービスが起動していることも合わせて確認します。
`sudo service ssh restart`
`sudo service ssh status`

</details>


<details><summary>課題提出について</summary>

### 1. パスワード無し・鍵認証・22 番ポート以外でログインに成功したときのスクリーンショット
- パスワード無しは、SSH設定ファイル内の`PasswordAuthentication`を`no`に設定
- 鍵認証は、生成した秘密鍵を使用してSSH接続を行う
- 新たに設定したポート番号を指定してログインを試みる

### 2. root でログインしようとして失敗したときのスクリーンショット
- rootユーザー（スーパーユーザー）でのログインを試みる
`ssh -p ポート番号 root@IPアドレス`

### 3. 22 番ポートでログインしようとして失敗したときのスクリーンショット
- ポート番号を22番に指定してログインを試みる
`ssh -i ~/.ssh/id_ed25519 -p 22 yoshiwo@160.16.241.119`

</details>


---


## 🌞次の目標
-  プラクティス『SSH の基本を理解する』をコツコツと進める

---


## ❤️‍🔥感想
#### ✍🏻 エラーメッセージから解決方法を探ること
表示されたエラーメッセージを元に原因を調べて調べてとにかく調べて、解決に導く立ち回りを行いました。例えば今回のエラーメッセージ`Permission denied (publickey)`には公開鍵認証に失敗したときに表示されます。これは、以下のいずれかの理由による可能性があります。
- 公開鍵がリモートサーバーに登録されていない
- 秘密鍵がクライアントマシンに存在しない、またはSSHクライアントが秘密鍵を見つけられない
- 秘密鍵と公開鍵が一致しない
- リモートサーバーがrootユーザーとしてのSSHログインを許可していない
紙に箇条書きで記入して一つずつ確かめていくアプローチを取りました。運良く一つ目でエラーの原因を突き止めることができましたが、頭の中だけで作業を行うのではなく文字に書き表すことでエラーの把握ができたように思います。

#### 💻 久しぶりの課題提出
提出物の提出を行いました。今までのプラクティスの中で最も難しい内容でした。どうか無事に「OK」をもらえますように。

---


## ⏰学習時間
- Today:&nbsp;&nbsp; 5 hours 49 min
- Total: 194 hours 20 min
