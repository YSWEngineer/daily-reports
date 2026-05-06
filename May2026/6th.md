# 2026/05/06(水)
## 🧑🏻‍💻 本日の取り組み
### 📚 プラクティス『🌐🔀 nginx で VirtualHost を使って 1 つのサーバーで複数のサイトを立ち上げる』
- ドメイン準備
- サーバー準備
- nginx設定


---


## ⏭️ 次回
### 📚 プラクティス『🌐🔀 nginx で VirtualHost を使って 1 つのサーバーで複数のサイトを立ち上げる』
- 確認と提出


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
- [ ] 2つの独立した VirtualHost を構築する
- [ ] 各 VirtualHost は別々のディレクトリでコンテンツを公開する
  - ディレクトリの配置場所：`/var/www/`配下など、Linux のディレクトリ構造として適切な場所
  - `/var/www/site1/`と`/var/www/site2`
- [ ] 各 VirtualHost は異なる HTMLファイルを表示する
  - 1ファイルだけではなく、ディレクトリ全体を別サイトとして公開
- [ ] 各 VirtualHost は別々のログファイルに出力する
  - アクセスログとエラーログをそれぞれ分ける......🤔

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
- [ ] URL
- [ ] 設定ファイルとそのパス
- [ ] ブラウザで表示したときのスクリーンショット
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
- [ ] 設定後、反映されるまで時間がかかるため待つ（数時間〜24時間🤔）

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
- [ ] 正しく表示される確認する
### 4-2：ブラウザでサイト2にアクセスして確認する
- [ ] 正しく表示される確認する
### 4-3：スクリーンショットを撮影する
- [ ] サイト1のスクリーンショット
- [ ] サイト2のスクリーンショット
### 4-4：提出物をまとめる
- [ ] サイト1について
  - [ ] URL
  - [ ] 設定ファイルとそのパス
  - [ ] スクリーンショット
- [ ] サイト2について
  - [ ] URL
  - [ ] 設定ファイルとそのパス
  - [ ] スクリーンショット
### 4-5：メンターさんに提出する
- [ ] 提出物をフォームから提出する
</details>


---


## 💡 本日の学び・気付き
<details><summary> ⚠️ ネタバレに注意</summary>

###  1. ドメイン準備
### 1-1：ドメイン名を決める / 1-2：ドメインを購入する
**お名前.comで検索し、取得可能なドメイン名を探す。**
1. 希望の名前を決めて検索し、ドメインを選択する

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MjY3LCJwdXIiOiJibG9iX2lkIn19--ace58a2ef045a52a7cd40e03fff7a9ed920d7c89/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-04%2020.15.38.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MjY3LCJwdXIiOiJibG9iX2lkIn19--ace58a2ef045a52a7cd40e03fff7a9ed920d7c89/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-04%2020.15.38.png" width="3644" height="2360" alt="スクリーンショット 2026-05-04 20.15.38.png"></a>

2. ドメインの主な使用方法を選択
<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MjY4LCJwdXIiOiJibG9iX2lkIn19--c21ccbc45fb5e914a6fe95af3a534f1571e98d78/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-04%2020.15.51.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MjY4LCJwdXIiOiJibG9iX2lkIn19--c21ccbc45fb5e914a6fe95af3a534f1571e98d78/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-04%2020.15.51.png" width="3644" height="2360" alt="スクリーンショット 2026-05-04 20.15.51.png"></a>

3. 選択はどちらでも大丈夫だが、**興味ある**を選択すると余計なプランが契約に追加されてしまう。
**※ 追加されたプランは申し込み前の確認で削除できるのでご安心を！**
<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MjY5LCJwdXIiOiJibG9iX2lkIn19--dcd4f6bb3b9dff02fe9b706d1f269ffc8d1a5a55/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-04%2020.16.20.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MjY5LCJwdXIiOiJibG9iX2lkIn19--dcd4f6bb3b9dff02fe9b706d1f269ffc8d1a5a55/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-04%2020.16.20.png" width="3644" height="2360" alt="スクリーンショット 2026-05-04 20.16.20.png"></a>

4. 申し込み内容を確認
この画面でオプションなどの余計なプランを削除することができる。
**※ ドメイン登録は1年目は無料。2年目から料金が発生する。**
<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MjcwLCJwdXIiOiJibG9iX2lkIn19--bdd6954ce3adaef67053fdeb846d4966b347818e/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-04%2020.30.56.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MjcwLCJwdXIiOiJibG9iX2lkIn19--bdd6954ce3adaef67053fdeb846d4966b347818e/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-04%2020.30.56.png" width="3644" height="2360" alt="スクリーンショット 2026-05-04 20.30.56.png"></a>

5. メールの確認 その①
お申込み内容の確認、お支払いを終えると『ドメイン情報認証のお願い』というメールが届くので、指定の URL からアクセスしドメイン情報認証の手続きを行う。

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzA3LCJwdXIiOiJibG9iX2lkIn19--dedffa2b775e0414fb94b7e071158d312e6ed175/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-05%2018.58.58.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzA3LCJwdXIiOiJibG9iX2lkIn19--dedffa2b775e0414fb94b7e071158d312e6ed175/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-05%2018.58.58.png" width="1374" height="938" alt="スクリーンショット 2026-05-05 18.58.58.png"></a>

6. メールアドレスの有効性認証フォームが表示
この画面が出たらOK。
<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzA0LCJwdXIiOiJibG9iX2lkIn19--ba3504896d74bc04300e6814618893ce71b86465/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-04%2020.57.20.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzA0LCJwdXIiOiJibG9iX2lkIn19--ba3504896d74bc04300e6814618893ce71b86465/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-04%2020.57.20.png" width="3644" height="2360" alt="スクリーンショット 2026-05-04 20.57.20.png"></a>

7. メールの確認 その②
『ドメイン登録完了通知』のメールが届いたことを確認。

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzA1LCJwdXIiOiJibG9iX2lkIn19--a45b390367b1838f38fdacf6cc1bde75dfeea904/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-05%2018.51.51.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzA1LCJwdXIiOiJibG9iX2lkIn19--a45b390367b1838f38fdacf6cc1bde75dfeea904/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-05%2018.51.51.png" width="2726" height="1016" alt="スクリーンショット 2026-05-05 18.51.51.png"></a>

8. 契約の確認
お名前.comに改めて入り、ドメインが**契約中**であることを確認。

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzA2LCJwdXIiOiJibG9iX2lkIn19--30075484d8ab9c719e047823aac1dc669673c54f/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-05%2018.55.07.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzA2LCJwdXIiOiJibG9iX2lkIn19--30075484d8ab9c719e047823aac1dc669673c54f/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-05%2018.55.07.png" width="2082" height="498" alt="スクリーンショット 2026-05-05 18.55.07.png"></a>

---

### 1-3：さくらVPSのIPアドレスを確認する
ターミナルで VPS に SSH でログインして、以下のコマンドを実行する。
```shell
# ホストのIPアドレスを表示する
yoshiwo@tk2-262-40865:~$ hostname -I
160.16.241.119 
```
参考リンク：[【 hostname 】コマンド――ホスト名を表示する／設定する](https://atmarkit.itmedia.co.jp/ait/articles/1612/21/news033.html)

---

### 1-4：DNS設定をする
1. 設定を行う前に2つの**サブドメイン**を考える。
・シンプルで分かりやすい
・VirtualHost の仕組みを学ぶのがプラクティスの目的なので、サイトの内容は重要ではない
・設定ファイル名もシンプルに
・タイプミスしにくい

以上を考慮して以下のサブドメイン名にした。
・`site1.ysw-engineer.com`
・`site2.ysw-engineer.com`

2. お名前.comにログイン
[お名前.com](https://navi.onamae.com/login) のサイトにアクセスしてログインする。

3. DNS設定/転送設定 ドメイン一覧
『DNS設定/転送設定 ドメイン一覧』ページに移動し、**ドメインDNS**をクリック。
<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzIxLCJwdXIiOiJibG9iX2lkIn19--ac6cd38aa86e2400407598f59f870b8cd4d49d30/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-05%2020.09.05.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzIxLCJwdXIiOiJibG9iX2lkIn19--ac6cd38aa86e2400407598f59f870b8cd4d49d30/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-05%2020.09.05.png" width="2576" height="1336" alt="スクリーンショット 2026-05-05 20.09.05.png"></a>

4. DNS設定/転送設定 - 機能一覧
**DNSレコード設定**をクリック。
<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzIyLCJwdXIiOiJibG9iX2lkIn19--73e0eb6b7d4e527803a64af9e842d5444e53b669/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%208.58.52.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzIyLCJwdXIiOiJibG9iX2lkIn19--73e0eb6b7d4e527803a64af9e842d5444e53b669/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%208.58.52.png" width="2190" height="1402" alt="スクリーンショット 2026-05-06 8.58.52.png"></a>

5. Aレコードを2つ追加する
『DNSレコード設定 - 入力』ページのレコード追加タブ内にある**入力**の各フォームに**ホスト名**、**VALUE**（IPアドレス）を入力し、**追加**をクリック。
設定した Aレコードは**追加**の欄に表示されるので確認する。
**※ TYPE は A のまま、TTL は 3600 のままにする。**
<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzIzLCJwdXIiOiJibG9iX2lkIn19--3e49a290932b753114b7be18105548704220b360/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%209.05.05.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzIzLCJwdXIiOiJibG9iX2lkIn19--3e49a290932b753114b7be18105548704220b360/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%209.05.05.png" width="2086" height="1140" alt="スクリーンショット 2026-05-06 9.05.05.png"></a>

確認できたら、下部にある**確認画面へ進む**ボタンをクリック。

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzI0LCJwdXIiOiJibG9iX2lkIn19--a4954ed0d4d38060e2f14722ee6026fa3fa31ab6/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%209.14.14.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzI0LCJwdXIiOiJibG9iX2lkIn19--a4954ed0d4d38060e2f14722ee6026fa3fa31ab6/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%209.14.14.png" width="2120" height="1764" alt="スクリーンショット 2026-05-06 9.14.14.png"></a>

『意図しないDNS設定変更を防ぐために』という広告が表示されるが、**設定しない**をクリックでOK。
<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzI1LCJwdXIiOiJibG9iX2lkIn19--e7e1562d8346c9bb0722d72c52a2563e384ae191/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%209.17.25.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzI1LCJwdXIiOiJibG9iX2lkIn19--e7e1562d8346c9bb0722d72c52a2563e384ae191/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%209.17.25.png" width="1468" height="728" alt="スクリーンショット 2026-05-06 9.17.25.png"></a>

6. 最終確認
『DNSレコード 設定 - 確認』ページが表示されるので、設定した 2つの Aレコードで間違いがないか確認する。
大丈夫ならば、**設定する**ボタンをクリック。
<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzI2LCJwdXIiOiJibG9iX2lkIn19--01fbbccbcfd6a9abb3c0a3870a73c1e3c671be21/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%209.18.17.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzI2LCJwdXIiOiJibG9iX2lkIn19--01fbbccbcfd6a9abb3c0a3870a73c1e3c671be21/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%209.18.17.png" width="2100" height="1906" alt="スクリーンショット 2026-05-06 9.18.17.png"></a>

7. DNSレコード設定の完了
以下の画面が表示されればOK。
メールでも設定完了の通知が届くのでそちらも念のため確認する。
<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzI3LCJwdXIiOiJibG9iX2lkIn19--9c242129d2a03310e5da3087c94d58b44ef0d5c9/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%209.21.01.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzI3LCJwdXIiOiJibG9iX2lkIn19--9c242129d2a03310e5da3087c94d58b44ef0d5c9/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%209.21.01.png" width="2168" height="1834" alt="スクリーンショット 2026-05-06 9.21.01.png"></a>

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzI4LCJwdXIiOiJibG9iX2lkIn19--81daffb4debb735e7cc42d9c2aa69845325d8ae5/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%209.34.31.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzI4LCJwdXIiOiJibG9iX2lkIn19--81daffb4debb735e7cc42d9c2aa69845325d8ae5/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%209.34.31.png" width="1538" height="1646" alt="スクリーンショット 2026-05-06 9.34.31.png"></a>

---

## 2. サーバー準備
### 2-1：VPSにSSHでログインする
いつものように、ターミナルから VPS に SSH で接続する。
```shell
~ % ssh -p 5555 yoshiwo@160.16.241.119
# Passphraseを入力し、プロンプトが変わっていればOK
yoshiwo@tk2-262-40865:~$
```

---

### 2-2：サイト用のディレクトリを2つ作成する
2つのサイト用のディレクトリを作成する。
以下のコマンドを実行する。
```shell
sudo mkdir -p /var/www/site1
sudo mkdir -p /var/www/site2
```
```shell
# 1つ目のディレクトリを作成する
yoshiwo@tk2-262-40865:~$ sudo mkdir -p /var/www/site1
[sudo] password for yoshiwo:   # sudo専用のパスワードを入力して、returnキーを押下。Passphraseと同じように入力しても表示されないが落ち着いて一つずつキーを打つこと
# 2つ目のディレクトリを作成する
yoshiwo@tk2-262-40865:~$ sudo mkdir -p /var/www/site2 
```
ディレクトリが作成できたか確認する。
```shell
yoshiwo@tk2-262-40865:~$ ls -la /var/www/
total 20
drwxr-xr-x  5 root root 4096 May  6 10:10 .
drwxr-xr-x 12 root root 4096 Apr 29 13:53 ..
drwxr-xr-x  2 root root 4096 Apr 29 14:51 html
drwxr-xr-x  2 root root 4096 May  6 10:10 site1  # site1専用
drwxr-xr-x  2 root root 4096 May  6 10:10 site2  # site2専用
```

---

### 2-3：各ディレクトリにindex.htmlを作成する
`site1`の HTML を作成する。
以下のコマンドを実行し、HTML で表示させる内容を編集する。
```shell
yoshiwo@tk2-262-40865:~$ sudo vim /var/www/site1/index.html
```

同じ要領で、`site2`の HTML を作成する。
```shell
yoshiwo@tk2-262-40865:~$ sudo vim /var/www/site2/index.html
```

HTMLファイルの内容は自由。

---

### 2-4：ディレクトリの権限を設定する
nginx がこれらのファイルを読み取れるようにするためにディレクトリの権限設定を行う。
以下のコマンドを実行する。
```shell
yoshiwo@tk2-262-40865:~$ sudo chown -R www-data:www-data /var/www/site1
yoshiwo@tk2-262-40865:~$ sudo chown -R www-data:www-data /var/www/site2
```
権限が変更されたか確認する。
```shell
yoshiwo@tk2-262-40865:~$ ls -la /var/www/
total 20
drwxr-xr-x  5 root     root     4096 May  6 10:10 .
drwxr-xr-x 12 root     root     4096 Apr 29 13:53 ..
drwxr-xr-x  2 root     root     4096 Apr 29 14:51 html
drwxr-xr-x  2 www-data www-data 4096 May  6 10:47 site1
drwxr-xr-x  2 www-data www-data 4096 May  6 10:50 site2
```
#### 疑問：なぜwww-dataなのか？
`www-data`とは？
→ **nginx が動作するためのユーザー名**

##### 仕組み
**1. nginx は www-dataユーザーとして動く**
・Webサーバー（nginx）は、セキュリティのため、専用のユーザーで動作する
・Debian では、そのユーザー名が`www-data`
**2. ファイルを読むには所有者でないといけない**
・`www-data`が`/var/www/site1/index.html`を読もうとする
→ でも、ファイルの所有者が`root`だと、権限がなくて読めない可能性がある
→ だから、所有者を`www-data`に変更する必要がある

##### 例
レストラン（nginx）があるとする。
・オーナー（root）：レストランを作った人
・コック（www-data）：実際に料理を作る人
・食材（HTMLファイル）：料理に使う材料

食材の持ち主がオーナー（root）のままだと、コック（www-data）が使えない可能性がある。
だから「コックが使っていいよ」と食材の所有者をコック（www-data）に変更するイメージ......多分（**※ 間違っていたらご指摘ください**）。

---

## 3. nginx設定
### 3-1：site1用のnginx設定ファイルを作成する
nginx の設定ファイルを作成する。
以下のコマンドを実行する。
```shell
yoshiwo@tk2-262-40865:~$ sudo vim /etc/nginx/sites-available/site1
```
Vim が開いたら、以下の内容を入力する。
```shell
server {
    listen 80;
    server_name site1.ysw-engineer.com;

    root /var/www/site1;
    index index.html;

    access_log /var/log/nginx/site1_access.log;
    error_log /var/log/nginx/site1_error.log;

    location / {
        try_files $uri $uri/ =404;
    }
}
```
・`listen 80;`：ポート80番（HTTP）で待ち受ける
・`server_name site1.ysw-engineer.com;`：このドメインでアクセスされたときに適用する
・`root /var/www/site1;`：HTMLファイルがある場所
・`index index.html`：デフォルトで表示するファイル
・`access_log`：アクセスログの保存場所（site1専用）
・`error_log`：エラーログの保存場所（site1専用）

---

### 3-2：site2用のnginx設定ファイルを作成する
以下のコマンドを実行する。
```shell
yoshiwo@tk2-262-40865:~$ sudo vim /etc/nginx/sites-available/site2
```
Vim が開いたら、以下の内容を入力する。
```shell
server {
    listen 80;
    server_name site2.ysw-engineer.com;

    root /var/www/site2;
    index index.html;

    access_log /var/log/nginx/site2_access.log;
    error_log /var/log/nginx/site2_error.log;

    location / {
        try_files $uri $uri/ =404;
    }
}
```
#### site1と違う部分
・`server_name site2.ysw-engineer.com;` ← site2に変更
・`root /var/www/site2;` ← site2に変更
・`access_log /var/log/nginx/site2_access.log;` ← site2に変更
・`error_log /var/log/nginx/site2_error.log;` ← site2に変更

---

### 3-3：設定ファイルを有効化する（シンボリックリンク作成）
作成した設定ファイルを有効化する。
以下の2つのコマンドを実行する。
```shell
yoshiwo@tk2-262-40865:~$ sudo ln -s /etc/nginx/sites-available/site1 /etc/nginx/sites-enabled/ 
yoshiwo@tk2-262-40865:~$ sudo ln -s /etc/nginx/sites-available/site2 /etc/nginx/sites-enabled/
```
シンボリックリンクが作成されたか確認する。
```shell
yoshiwo@tk2-262-40865:~$ ls -la /etc/nginx/sites-enabled/
total 8
drwxr-xr-x 2 root root 4096 May  6 12:06 .
drwxr-xr-x 8 root root 4096 Apr 29 13:53 ..
lrwxrwxrwx 1 root root   34 Apr 29 13:53 default -> /etc/nginx/sites-available/default
lrwxrwxrwx 1 root root   32 May  6 12:05 site1 -> /etc/nginx/sites-available/site1  # シンボリックリンクを確認
lrwxrwxrwx 1 root root   32 May  6 12:06 site2 -> /etc/nginx/sites-available/site2 # シンボリックリンクを確認
```
`->`の矢印が、シンボリックリンク（ショートカット）を表している。

---

### 3-4：nginx設定ファイルの文法をチェックする
nginx設定ファイルに文法エラーがないかチェックする。
以下のコマンドを実行する。
```shell
yoshiwo@tk2-262-40865:~$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```
`ok`と`successful`がそれぞれ表示されているので大丈夫みたい。

---

### 3-5：nginxを再起動する
nginx を再起動して、設定を反映させる。
#### nginxを再起動
以下のコマンドを実行する。
```shell
yoshiwo@tk2-262-40865:~$ sudo systemctl restart nginx
```
#### 再起動が成功したか確認
以下のコマンドを実行する。
```shell
yoshiwo@tk2-262-40865:~$ sudo systemctl status nginx
* nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; preset: >
     Active: active (running) since Wed 2026-05-06 12:15:13 JST; 22s ago
       Docs: man:nginx(8)
    Process: 1174863 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; mas>
    Process: 1174864 ExecStart=/usr/sbin/nginx -g daemon on; master_proce>
   Main PID: 1174865 (nginx)
      Tasks: 2 (limit: 495)
     Memory: 1.7M
        CPU: 17ms
     CGroup: /system.slice/nginx.service
             |-1174865 "nginx: master process /usr/sbin/nginx -g daemon o>
             `-1174866 "nginx: worker process"

May 06 12:15:13 tk2-262-40865 systemd[1]: nginx.service: Deactivated succ>
May 06 12:15:13 tk2-262-40865 systemd[1]: Stopped nginx.service - A high >
May 06 12:15:13 tk2-262-40865 systemd[1]: nginx.service: Consumed 1.360s >
May 06 12:15:13 tk2-262-40865 systemd[1]: Starting nginx.service - A high>
May 06 12:15:13 tk2-262-40865 systemd[1]: Started nginx.service - A high >
lines 1-19/19 (END)
```
`active(running)`という表示があればOK。
確認できたら`Q`キーを押下して終了させる。

---

## 4. 確認と提出
### 4-1：ブラウザでsite1にアクセスして確認する
ブラウザを開いて、以下の URL にアクセスする。
```
http://site1.ysw-engineer.com
```
すると、まだ DNSが反映されていないらしく以下のページが表示された。

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzQ0LCJwdXIiOiJibG9iX2lkIn19--bbeb33b66ef5664ec1dda98ed5401fcf1d07fc30/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%2015.48.49.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjc4MzQ0LCJwdXIiOiJibG9iX2lkIn19--bbeb33b66ef5664ec1dda98ed5401fcf1d07fc30/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-05-06%2015.48.49.png" width="3644" height="2360" alt="スクリーンショット 2026-05-06 15.48.49.png"></a>

せっかくの休みの日に、いつ反映されるかわからない DNSの反映をただ待つのは非効率だと考え、DNS を経由せずに確認する方法について調査。
その結果、いくつかの方法があることが分かった。
**※ 本来の課題範囲からは逸れますが、このようなアプローチがあることが分かり、興味深かったため記録として残します。**

#### DNS反映前の確認方法
##### 方法1：curlで直接確認（VPS側）
```shell
yoshiwo@tk2-262-40865:~$ curl -H "Host: site1.ysw-engineer.com" http://160.16.241.119
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Site1</title>
</head>
<body>
    <h1>This is Site 1</h1>
    <p>site1.ysw-engineer.com</p>
</body>
</html>
```

##### 方法2：nslookupでDNS反映状況を確認
```shell
yoshiwo@tk2-262-40865:~$ nslookup site1.ysw-engineer.com
Server:		210.188.224.10
Address:	210.188.224.10#53

Non-authoritative answer:
Name:	site1.ysw-engineer.com
Address: 150.95.255.38
```
Address が`160.16.241.119`ではなく`150.95.255.38`になっている。
これはまだ DNS反映がされていない、という意味。
もし結果が設定した IPアドレス`160.16.241.119`になれば反映完了。

##### 方法3：オンラインDNSチェックツール
世界中のDNSサーバーから確認できるツールがある。
・What's My DNS：https://www.whatsmydns.net/
・DNS Checker：https://dnschecker.org/

ドメイン名を入力すると、世界中の DNSサーバーでの反映状況が分かる。

#### 補足：curlコマンドと確認方法について
##### curlコマンドとは？
`curl`（カールまたはシーユーアールエル）は、URL を使ってデータを転送するコマンドラインツール。Webページの内容を取得したり、API をテストしたりするときに使う。

##### 基本的な使い方
```shell
curl http://example.com
```
→ Webページの HTML が表示される

##### curl -Hオプションとは？
`-H`は`Header`（ヘッダー）の略。HTTPリクエストにカスタムヘッダーを追加できる。
**今回使ったコマンド**
```shell
yoshiwo@tk2-262-40865:~$ curl -H "Host: site1.ysw-engineer.com" http://160.16.241.119
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Site1</title>
</head>
<body>
    <h1>This is Site 1</h1>
    <p>site1.ysw-engineer.com</p>
</body>
</html>
```
**処理の流れ**
IPアドレス`160.16.241.119`に直接アクセス → `Host: site1.ysw-engineer.com`というヘッダーをつけて送る。
nginx の VirtualHost は、リクエストの`Host`ヘッダーを見て、どのサイトを表示するか判断する。
通常はブラウザが自動で`Host`ヘッダーを付けてくれるが、**DNS反映前はドメイン名でアクセスできない。**
そこで、`curl -H`で手動で`Host`ヘッダーを指定することで、**DNS を経由せずに直接VPS にアクセスして確認できる。**

**参考リンク**
・[curl公式サイト](https://curl.se/)
・[curl manページ](https://curl.se/docs/manpage.html)
・[curlコマンド使い方メモ](https://qiita.com/yasuhiroki/items/a569d3371a66e365316f)

---

## Tips
### プロンプトがフリーズした場合の対処方法
#### まず状況確認
・プロンプト`yoshiwo@tk2-262-40865:~$`が表示されている？
・それとも何も表示されていない？
・エラーメッセージが出ている？
#### 今回のケース
・プロンプトは表示されている
・エラーメッセージは出ていない
・プロンプトだけが表示されている
・キーを押しても反応がない
#### 対処方法
1. `control + C`を押す
2. それでもダメなら`control + D`を押す
3. それでもダメなら**ターミナルを閉じる**

---

### SSH接続を簡単に
・`ssh sakura-vps`でログインし、パスフレーズを入力

→ `~ % ssh -p 5555 yoshiwo@160.16.241.119`を入力する手間を省くことができる。
</details>


---


## ✍🏻 感想
### 🚦 待ちの姿勢
**ドメイン準備 → サーバー準備 → nginxの設定**まで順調に進めることができましたが、DNSの反映が完了しておらず、設定したHTMLの表示確認ができませんでした。
数時間〜24時間程度かかるとのことなので、明日まで様子を見ます。
次回はメンターさんへの課題提出を目標に進めます。
今回の作業の流れは、今後のために整理してまとめました。

### 🥳🙌🏻 プラクティス修了
今取り組んでいる一つ前のプラクティス『🌐🔀 nginxの基本を理解する』が無事修了しました。
これまでとは内容が変わり難しく感じることも多々ありますが、Web の仕組みについて少しずつ分かるようになるのが嬉しいです！
学習を積み重ねて理解を深めていきたいと思います🏋🏻

---


### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 6 hours 20 min
- Total: 1566 hours 55 min
