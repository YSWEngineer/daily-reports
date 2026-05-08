# 2026/05/07(木)
## 🧑🏻‍💻 本日の取り組み
### 📚 プラクティス『🌐🔀 nginx で VirtualHost を使って 1 つのサーバーで複数のサイトを立ち上げる』
- 確認と提出


---


## ⏭️ 次回
### 📚 プラクティス『🌐🔀 nginx で SSL 対応サイトを作る』
- 内容の把握
- 要件定義・フローチャート・タスクばらしの作成


---


## 🗺️ 要件定義・処理の流れ・タスクばらし
<details><summary>📌 要件定義 ※ 随時、追加・変更あり</summary>

## 🎯 このプラクティスで何をするのか？
**・1台のサーバー（さくらVPS上のDebian）で、nginx の VirtualHost機能を使って2つの異なる Webサイトを公開する**
**・ドメイン取得から DNS設定、Webサーバー構築まで、本格的な Webサイト立ち上げの一連の流れを習得する**

## ⚙️ 機能要件
### ドメイン関連
- [x] 独自ドメインを1つ取得する（有料：[お名前.com](https://www.onamae.com/)、または無料：[tkドメイン](http://www.dot.tk/en/index.html?lang=en)）
- [x] 取得したドメインに対して2つのサブドメインを設定する
  - `site1.ysw-engineer.com`と`site2.ysw-engineer.com`

#### 注意事項
> 参考記事に www ありと www なしを同じサイトにするように書かれていますが、今回は対応する必要はないです。ドメインを 1 つだけ取得し、1 つのドメインについて 2 つのサイトを立ち上げるようにしてください。

- [x] DNSレコード（Aレコード）を設定し、サブドメインを VPS の IPアドレスに紐付ける
### Webサーバー関連（nginx）
- [x] 2つの独立した VirtualHost を構築する
- [x] 各 VirtualHost は別々のディレクトリでコンテンツを公開する
  - ディレクトリの配置場所：`/var/www/`配下など、Linux のディレクトリ構造として適切な場所
  - `/var/www/site1/`と`/var/www/site2`
- [x] 各 VirtualHost は異なる HTMLファイルを表示する
  - 1ファイルだけではなく、ディレクトリ全体を別サイトとして公開

### 設定ファイル
- [x] nginx の設定ファイルを作成する
  - 設定ファイルの保存場所：`/etc/nginx/sites-available/`
  - シンボリックリンクの作成：`/etc/nginx/sites-enabled/`
- [x] インデントを整えた読みやすい設定ファイルにする

### 非機能要件
- [x] セキュリティ：不要な PHPコードは記述しない
- [x] ログ管理：エラー発生時にログを確認できる状態にする
- [x] ファイル配置：Linux のディレクトリ構造に従った適切な場所に配置

### 制約条件
- [x] さくらVPSのお試し期間中は、さくらVPSのネームサーバーは使用不可
  - → [お名前.com](https://www.onamae.com/)などのネームサーバーを使用する
- [x] nginx は Debian上で動作させる

### 提出物
各 VirtualHost について、以下を提出。
- [x] URL
- [x] 設定ファイルとそのパス
- [x] ブラウザで表示したときのスクリーンショット
</details>

<details><summary>📍 処理の流れ（フローチャート） ※ 随時、追加・変更あり</summary>

## 💬 テキストベースで整理してみる
```
━━━━━━━━
①：ドメイン準備
━━━━━━━━
  ↓
ドメイン名を決めて購入
  ↓
DNS設定(AレコードでVPSのIPアドレスを登録)
  - サブドメイン1 → VPSのIP
  - サブドメイン2 → VPSのIP
  ↓
━━━━━━━━
②：サーバー準備
━━━━━━━━
  ↓
VPSにログイン
  ↓
2つのディレクトリを作成
  - /var/www/サイト1/
  - /var/www/サイト2/
  ↓
各ディレクトリにHTMLファイルを作成
(それぞれ異なる内容)
  ↓
━━━━━━━━
 ③：nginx設定
━━━━━━━━
  ↓
nginx設定ファイルを2つ作成
  - サイト1用
  - サイト2用
  ↓
シンボリックリンクで有効化
  ↓
設定チェック
  $ sudo nginx -t
  ↓
  OK? → No → 修正して再チェック
  ↓Yes
  ↓
nginxを再起動
  $ sudo systemctl restart nginx
  ↓
━━━━━━━
④：確認と提出
━━━━━━━
  ↓
ブラウザで2つのサイトにアクセス
  ↓
  表示OK? → No → ログ確認して修正
  ↓Yes
  ↓
スクリーンショット撮影
  ↓
提出物をまとめて提出
```
大きく分けると4つのフェーズ
1. **ドメインの準備**：ドメインを購入して、DNSに設定
2. **サーバーの準備**：ディレクトリと HTMLファイルを作成
3. **nginx設定**：設定ファイルを作成し、有効化し、再起動？
4. **確認と提出**：動作確認して、スクリーンショットを撮り、提出へ
</details>

<details><summary> 🧩 タスクばらし ※ 随時、追加・変更あり</summary>

## 1. ドメイン準備
### 1-1：ドメイン名を決める
- [x] お名前.comで検索して、取得可能なドメイン名を探す
### 1-2：ドメインを購入する
- [x] お名前.comでドメインを購入・登録する
### 1-3：さくらVPSのIPアドレスを確認する
- [x] VPS にログインして、IPアドレスをメモする
### 1-4：DNS設定をする
- [x] お名前.comの DNS設定画面を開く
- [x] レコードを2つ追加する
  - [x] サブドメイン1（site1） → VPS の IPアドレス
  - [x] サブドメイン2（site2） → VPS の IPアドレス
- [x] 設定後、反映されるまで時間がかかるため待つ（数時間〜24時間🤔）

## 2. サーバー準備
### 2-1：VPSにSSHでログインする
- [x] ターミナルから VPS に接続する
### 2-2：サイト用のディレクトリを2つ作成する
- [x] ディレクトリを作成する
  - [x] `sudo mkdir -p /var/www/site1`
  - [x] `sudo mkdir -p /var/www/site2`
### 2-3：各ディレクトリにindex.htmlを作成する
- [x] site1の HTML 作成
  - [x] `sudo vim /var/www/site1/index.html`
- [x] site2の HTML 作成
  - [x] `sudo vim /var/www/site2/index.html`
### 2-4：ディレクトリの権限を設定する
- [x] nginx が読み取れるように権限を設定する

## 3. nginx設定
### 3-1：サイト1用のnginx設定ファイルを作成する
- [x] ファイルを作成する
  - [x] 場所：`/etc/nginx/sites-available/site1
  - [x] コマンド：`sudo vim /etc/nginx/sites-available/site1`
- [x] 設定内容を記述する
  - [x] `server_name`：サブドメイン1（例：blog.example.com）
  - [x] `root`：`/var/www/site1`
  - [x] `access_log`：`/var/log/nginx/site1_access.log`アクセスログの保存場所（site1専用）
  - [x] `error_log`：`/var/log/nginx/site1_error.log`エラーログの保存場所（site1専用）
### 3-2：サイト2用のnginx設定ファイルを作成する
- [x] ファイルを作成する
  - [x] 場所：`/etc/nginx/sites-available/site2
  - [x] コマンド：`sudo vim /etc/nginx/sites-available/site2`
- [x] 設定内容を記述する
  - [x] `server_name`：サブドメイン1（例：blog.example.com）
  - [x] `root`：`/var/www/site2`
  - [x] `access_log`：`/var/log/nginx/site2_access.log`アクセスログの保存場所（site2専用）
  - [x] `error_log`：`/var/log/nginx/site2_error.log`エラーログの保存場所（site2専用）
### 3-3：設定ファイルを有効化する（シンボリックリンク作成）
- [x] site1の設定を有効化
- [x] site2の設定を有効化
### 3-4：nginx設定ファイルの文法をチェックする
- [x] コマンド：`sudo nginx -t`
### 3-5：nginxを再起動する
- [x] コマンド：`sudo systemctl restart nginx`

## 4. 確認と提出
### 4-1：ブラウザでサイト1にアクセスして確認する
- [x] 正しく表示されることを確認する
### 4-2：ブラウザでサイト2にアクセスして確認する
- [x] 正しく表示されることを確認する
### 4-3：スクリーンショットを撮影する
- [x] サイト1のスクリーンショット
- [x] サイト2のスクリーンショット
### 4-4：提出物をまとめる
- [x] サイト1について
  - [x] URL
  - [x] 設定ファイルとそのパス
  - [x] スクリーンショット
- [x] サイト2について
  - [x] URL
  - [x] 設定ファイルとそのパス
  - [x] スクリーンショット
### 4-5：メンターさんに提出する
- [x] 提出物をフォームから提出する
</details>


---


## 💡 本日の学び・気付き
### nginx + DNS設定で表示が切り替わらなかった原因を整理
作成した`site1.ysw-engineer.com`にアクセスすると、お名前.comのデフォルトページが表示されていたが、最終的に以下の内容が正しく表示されることを確認できた。

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4NTA3LCJwdXIiOiJibG9iX2lkIn19--4d607dcff070a2bcc9cbbb767f12b0f8d0191610/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-07%2020.43.17.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4NTA3LCJwdXIiOiJibG9iX2lkIn19--4d607dcff070a2bcc9cbbb767f12b0f8d0191610/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-07%2020.43.17.png" width="3644" height="2360" alt="スクリーンショット 2026-05-07 20.43.17.png"></a>

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4NTA4LCJwdXIiOiJibG9iX2lkIn19--8c8fd9ec1d5907117c73491e34a0307d264cedde/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-07%2020.43.30.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4NTA4LCJwdXIiOiJibG9iX2lkIn19--8c8fd9ec1d5907117c73491e34a0307d264cedde/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-07%2020.43.30.png" width="3644" height="2360" alt="スクリーンショット 2026-05-07 20.43.30.png"></a>

結果として、niginx や VPS側の設定ミスではなく、「DNSキャッシュ」と「ブラウザキャッシュ」が原因だった。

#### 先ず結論
今回行った作業自体は問題なく、以下はすべて正常に設定できていた。
- ドメイン取得
- DNS設定（Aレコードの追加）
- VPS側のディレクトリ作成
- HTMLファイル作成
- nginx設定ファイル作成
- nginx再起動

つまり、サーバー側の設定は最初から正しかった。
しかし、ブラウザや DNSサーバー側に「**古い情報**」が残っていいたため、新しい設定が反映されていないように見えていた。

#### 疑問① なぜ設定が正しいのに古いページが表示されたのか？
##### 原因：ブラウザキャッシュ
ブラウザは、一度アクセスした Webページの情報を保存（キャッシュ）している。
これは毎回サーバーへアクセスせず、高速で表示するための仕組み。
##### 今回起きていたこと
1. `site1.ysw-engineer.com`に最初にアクセス
2. その時点では「お名前.comのデフォルトのページ」が表示されていた
3. ブラウザがその内容を記憶
4. VPS側の設定完了後、本来は新しい HTML が表示される状態になった
5. しかし、ブラウザは、保存していた古いページを表示し続けた

##### 解決方法
**スーパーリロードを実行**
```
# macOSの場合
command + shift + R
```
**何をしているのか？**
- 保存済みの古いページを破棄する
- サーバーから最新の情報を再取得

これにより、新しい HTML が表示されるようになった。

---

#### 疑問② なぜDNS設定後直ぐに反映されなかったのか？
##### 原因：DNSキャッシュ
DNSサーバーも、ドメイン名と IPアドレスの対応をキャッシュ（保存）している。
##### 今回起きていたこと
最初、DNSサーバー側には以下のような古い情報が残っていた。
```nginx
site1.ysw-engineer.com
↓
150.95.255.38（お名前.com側）
```
その後、Aレコードを変更して本来は以下になるはずだった。
```nginx
site1.ysw-engineer.com
↓
160.16.241.119（VPS）
```
しかし、DNSサーバーが古い情報を保持していたため、変更後もしばらくは古い IPアドレスへアクセスしてしまっていた。
##### 解決方法
**hostsファイルを編集**
```nginx
160.16.241.119 site1.ysw-engineer.com
```
**hostsファイルの役割**
Mac に対して、「**DNSサーバーに確認しなくていい。このドメインはこのIPアドレスだ！**」と直接教える仕組み。
これにより、DNS反映を待たずに VPS へ直接アクセスできるようになった。

---

#### 疑問③ curlコマンドでは正しく表示されたのはなぜか？
##### 理由：curlはブラウザキャッシュを使わないため
ブラウザはキャッシュを保持するため、古いページが表示されることがある。
一方で`curl`は毎回サーバーへ直接アクセスする。
つまり、
```nginx
curl http://site1.ysw-engineer.com
```
で正しく表示された時点で、
- nginx設定
- HTML配置
- VirtualHost設定

など、サーバー側は正常に動いていることを確認できた。

---

#### 学んだことのまとめ
|作業内容   |目的   |
|---|---|
|ドメイン取得・DNS設定   |インターネットからアクセス可能にする   |
|nginx設定   |VPS上でWebサイトを公開する   |
|hostsファイル編集   |DNS反映を待たずに動作確認する   |
|スーパーリロード   |ブラウザの古いキャッシュ（保存されていたもの）を破棄する   |
|curl確認   |サーバー側が正常か確認する   |

---

### 参考リンク
#### ブラウザキャッシュ・スーパーリロード関連
- [キャッシュを無視したブラウザの再読み込み](https://help.jenka.jp/portal/ja/kb/articles/super-reload?utm_source=chatgpt.com)
- [スーパーリロード](https://puzz.jp/tips/%E3%82%B9%E3%83%BC%E3%83%91%E3%83%BC%E3%83%AA%E3%83%AD%E3%83%BC%E3%83%89/?utm_source=chatgpt.com)
- [Q.ブラウザの「スーパーリロード」とは？](https://wasabi-inc.biz/help/faq/superreload/?utm_source=chatgpt.com)
- [各種ブラウザでのスーパーリロード方法（Windows/Mac対応）](https://webspot.info/browser_super_reload/?utm_source=chatgpt.com)
#### DNS・DNSキャッシュ関連
- [キャッシュDNSサーバとは](https://www.nic.ad.jp/ja/basics/terms/cache-dns-server.html) 
- [DNSの仕組み徹底解説【高校情報１・情報処理技術者試験】FQDN、ドメイン、再帰問合せ](https://www.youtube.com/watch?v=CY3-Ua4M_f0&pp=ygVzRE5T44Gu5LuV57WE44G_5b655bqV6Kej6Kqs44CQ6auY5qCh5oOF5aCx77yR44O75oOF5aCx5Yem55CG5oqA6KGT6ICF6Kmm6aiT44CRRlFETuOAgeODieODoeOCpOODs-OAgeWGjeW4sOWVj-WQiOOBmw%3D%3D)
- [【高校情報Ⅰ】DNSの仕組みとは｜権威DNSサーバ、キャッシュDNS｜情報ネットワークとデータの活用｜共通テスト完全攻略勉強法_147
](https://www.youtube.com/watch?v=MYjQvJjVTUE&pp=ygWvAeOAkOmrmOagoeaDheWgseKFoOOAkUROU-OBruS7lee1hOOBv-OBqOOBr--9nOaoqeWogUROU-OCteODvOODkOOAgeOCreODo-ODg-OCt-ODpUROU--9nOaDheWgseODjeODg-ODiOODr-ODvOOCr-OBqOODh-ODvOOCv-OBrua0u-eUqO-9nOWFsemAmuODhuOCueODiOWujOWFqOaUu-eVpeWLieW8t-azlV8xNDc%3D)
#### hostsファイル関連
- [hostsファイル（/etc/hosts）とは？IPアドレスとホスト名の対応関係を解説
](https://the-simple.jp/what-is-the-hosts-file-etc-hosts-explanation-of-correspondence-between-ip-addresses-and-host-names?utm_source=chatgpt.com)


---


## ✍🏻 感想
### 😭🙌🏻 HTML表示できました！
HTMLが表示されない問題は「DNS反映待ち」や「設定ミス」ではなく、「キャッシュ（保存されていた情報）による表示のズレ」が原因でした。
作成したフローチャートとタスクばらしを一つずつ照らし合わせながら作業を進めていたため、「設定ミスの可能性は低そう」と考え、設定以外の原因について調べました。
その結果、実際には以下が原因であることが分かりました。
- DNSキャッシュ
- ブラウザキャッシュ

また、hostsファイルや`curl`を使うことで「DNS反映待ち」をせずにサーバー確認できることも理解できました。

課題提出も無事に終えたので、レビューを待つ間は次のプラクティスに進みます。


---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1 hours 41 min
- Total: 1568 hours 36 min
