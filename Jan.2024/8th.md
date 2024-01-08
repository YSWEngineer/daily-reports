# 2023/01/08(月)
## 🕺今の気持ち
手順のまとめをもっと上手にできなかったのかな🤔と反省です。

---

## ✍🏻本日の取り組み
- プラクティス『Linux をインストールする』の提出物の提出までの手順をまとめる
<details><summary>"Linux をインストールする"まとめ ※ ネタバレに注意!!!</summary>
※ 途中、スクリーンショットで撮れていない箇所がいくつかあります。

1. SAKURA internet の VPS 契約の流れを押さえる

![スクリーンショット 2024-01-07 11.12.39.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBK0pVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--4ef7589b906d59103af511b58716e674ea645a21/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2011.12.39.png)

![スクリーンショット 2024-01-07 11.16.25.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBK05VQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--725eb69cf321fdb0e941a8d7d03cde30af8fcb1c/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2011.16.25.png)

![スクリーンショット 2024-01-07 11.21.11.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBK1JVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--c00079cc8c357094676311e70fb37971b5542c43/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2011.21.11.png)


2. サーバーの設定
![スクリーンショット 2024-01-07 11.23.37.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBK1ZVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--e7cc7e212da3ae4d5ef5dcad882e5fb15a491007/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2011.23.37.png)
- OS は、最後に Debian を再インストールするのでどれでもよいが、選択肢の中に Debian があったのでそちらを選択
- バージョン は、最後に Debian を再インストールするのでどれでもよいが、新しいバージョンを選択
- サーバーのプラン は、「学習には一番安いプランで十分です」と、FBC のブログ『さくらの VPS で Linux を使う』に書いてあったので、512MB プラン、月額671円を選択
- 毎月払い or 12ヶ月一括は、本人の自由

![スクリーンショット 2024-01-07 11.32.48.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBK1pVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--b3aff139b4f8ba09c753f5a4fa96392cb5a17cc7/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2011.32.48.png)
- 「東京」「大阪」リージョン手数料0円キャンペーンも本人の自由
- リージョン（地域）はどこでもよいが、速度が気になるようなら自分が住んでいる地域から近い場所が良い。私の場合は住所が都内なので「東京第2」を選択
- サーバーの購入台数は「1」

![スクリーンショット 2024-01-07 12.20.44.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBK2RVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--df733996ef289fb03848a8daee5caad730a3d64d/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2012.20.44.png)

![スクリーンショット 2024-01-07 12.25.34.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBK2hVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--57d09740393f177e5f26da43dac70882f4ac9e19/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2012.25.34.png)

![スクリーンショット 2024-01-07 12.26.30.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBK2xVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--5d3fcb21b940b243ff5982fb0ad8be721702d3d3/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2012.26.30.png)
- 管理ユーザーのパスワードを自分で入力して設定。「管理ユーザーのパスワードをダウンロード」をクリックすれば設定したパスワードをファイル形式で保存できる（私の場合はテキストエディットに保存してくれた）。
- SSH キー設定、スタートアップスクリプトについてはよくわからなかったので、そのままに
- サーバーの名前はご自由に
- 「お支払い方法選択へ」をクリックすると、さくらインターネット会員認証画面に遷移するので、会員 ID を持っていればログイン、持っていなければ「新規会員登録」をクリック
- 契約の流れは表示された内容のとおりに行えば大丈夫なので割愛


3. さくらの VPS に ISO イメージインストールで Debian をインストール（OS の再インストール）

![スクリーンショット 2024-01-08 16.20.10.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBK3RVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--60c5b5e3e39aadb2108b71ae1b20c8b7b9de2589/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-08%2016.20.10.png)
- サーバー一覧から契約したサーバー（VPS）を選択

![スクリーンショット 2024-01-07 13.14.46.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBK3hVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--355f94db08e2c2ef74712b03060bcb049a490307/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2013.14.46.png)
- 「OS 再インストール」をクリック

![スクリーンショット 2024-01-07 13.17.05.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBKzFVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--bd6f76afadcf928820ba0ddb6d2f3557394a4d2b/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2013.17.05.png)
- OS インストール方法を選択してください　では、「ISO イメージ」を選択
- ISO イメージを選択してください　では、「一覧から選ぶ」を選択
- インストールする OS を選択してください　では、「Debian 12 amd64」を選択

![スクリーンショット 2024-01-07 13.20.02.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBKzVVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--e64a73ecb4dcf42d15d27ea8786723555d748f31/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2013.20.02.png)
- VirtIO を有効にする　には、チェックが入ったまま
- ネットワーク接続を保持するかを選択してください　では、「接続先を初期化」を選択したまま
- 内容確認をクリック

![スクリーンショット 2024-01-08 16.38.39.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBKzlVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--8f1028b9cea6455cae9629337d943922d77b27c6/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-08%2016.38.39.png)
- OS 再インストールをクリック

![スクリーンショット 2024-01-08 16.59.59.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBL05VQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--7ca9a6d6f5ba76496c7040a483a7b45334861653/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-08%2016.59.59.png)
- 「▽ コンソール」から VNC を選択、または右下の「VNC コンソールを起動」をクリック

![スクリーンショット 2024-01-07 13.10.11.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBK3BVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--da85e39e09300e5ab61fef9fee871cfa639c0a0a/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2013.10.11.png)
- ここからは [再インストールマニュアル](https://manual.sakura.ad.jp/vps/os-reinstall/) の ISO イメージインストールの欄から Debian をクリックし、マニュアルを見ながら設定を行う

![スクリーンショット 2024-01-07 13.26.10.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBL1JVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--4c84c7c339f89be25eee6c82b56072319709d6fa/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2013.26.10.png)
- VNC を起動すると、Debian GNU/Linux installer menu(BIOS mode)が別のウィンドウで現れる
- Install にカーソルを合わせて、returnを押下

![スクリーンショット 2024-01-07 13.35.09.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBL1ZVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--00b4aa5a99333db71fff6fbbce7b910cb45d9722/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2013.35.09.png)
- Continue を選択

![スクリーンショット 2024-01-07 13.48.09.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBL1pVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--0af575c3c4f7f011040463041bb4c200172614f6/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2013.48.09.png)

![スクリーンショット 2024-01-07 13.48.49.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBL2RVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--c88bde5cd1330f49f3e759ce561ba524cc2ef8cf/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2013.48.49.png)
- Location を設定。「Asia」 -> 「Japan」の順で設定

![スクリーンショット 2024-01-07 14.00.19.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBL2hVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--0990d839ca3421e64f756aed46d0493cab49e29f/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2014.00.19.png)
- キーボードの設定。私の場合、使用している MacBook は US キーボードなので、「American English」を選択
- Configure the network（Network の設定）は「ens3」を選択　※ スクリーンショットを撮り忘れましたので画像はありません


![スクリーンショット 2024-01-07 14.03.20.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBL2xVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--1448a6209285b5d1da73a81aa1ea4099461333dc/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2014.03.20.png)
- しばらく待つと「DHCP での IP アドレス設定の失敗」を示す画面が表示されるが、そのまま<Continue>を選択

![スクリーンショット 2024-01-07 14.05.13.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBL3BVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--4121a8946d68b4b5ad5502f4149b5f3c47c84dc2/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2014.05.13.png)
- Configure network manually を選択

![スクリーンショット 2024-01-07 14.06.57.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBL3RVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--016314dc1ee6d0734925dc3aabeb6b4fb0e87aa0/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2014.06.57.png)
- IP address は、さくらの VPS のネットワーク欄の「アドレス」を入力、<Continue>を選択

![スクリーンショット 2024-01-08 17.30.56.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBLzFVQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--0a440cd7e7c5d574d65ed8cff639f479e72196de/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-08%2017.30.56.png)
- Netmask は、さくらの VPS のネットワーク欄の「ネットマスク」を入力、<Continue>を選択
- Gateway は、さくらの VPS のネットワーク欄の「ゲートウェイ」を入力、<Continue>を選択　※ スクリーンショットを撮り忘れましたので画像はありません

![スクリーンショット 2024-01-08 18.19.05.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBd0pWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--23d2df087230b727af0189433da58532904d810f/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-08%2018.19.05.png)
- Name server addresses は、さくらの VPS のネットワーク欄の「プライマリ DNS」「セカンダリ DNS」を間にスペースを一つ入れて入力、<Continue>を選択
- Hostname は、さくらの VPS のネットワーク欄の「標準ホスト名」または基本情報欄の「ホスト名」を入力、<Continue>を選択　※ スクリーンショットを撮り忘れましたので画像はありません

![スクリーンショット 2024-01-07 14.52.38.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBd05WQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--b463ad44fe0951355cb1d07463810a76a606607f/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2014.52.38.png)
- Choose a mirror of the Debian archive（Debian アーカイブのミラーサイトを選択）は、「Japan」を選択、次に「deb.debian.org」を選択
- HTTP proxy information は、入力せずに<Continue>を選択

![スクリーンショット 2024-01-07 15.09.18.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBd1JWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--3e6e6ab59cc0005c6a761e920ec3b859226c2520/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2015.09.18.png)
- Root Password は、任意のパスワードを入力、<Continue>を選択。入力した Root password を確認したい場合は、「[ ] Show Password in Clear」にカーソルを合わせて、spaceキーを押下すると確認できる

![スクリーンショット 2024-01-07 15.12.12.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBd1ZWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--0e6d62d397af938faa39ede0ffb64bbd7804b3e2/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2015.12.12.png)
- 設定した Root password をもう一度入力、<Continue>を選択

![スクリーンショット 2024-01-07 15.18.09.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBd1pWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--38d3e0e474b1aabbca00204ae41c1697f180aaf3/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2015.18.09.png)
- Full name for the user は、任意のユーザー名をフルネームで入力、<Continue>を選択
- Username for your account は、任意のユーザー名を入力するのだが、自動的に小文字から始まる　※ スクリーンショットを撮り忘れましたので画像はありません

![スクリーンショット 2024-01-07 15.36.38.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBd2RWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--a6f0584fb4941574047e468668aa55dfaf7c775d/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2015.36.38.png)
- Choose a password for the new user は、ユーザーのパスワードを設定。任意のパスワードを入力

![スクリーンショット 2024-01-07 15.42.05.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBd2hWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--984761905e91da2c8b57f313630904e599ddb618/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2015.42.05.png)
- Partitioning method は、「Guided - use entire desk」を選択

![スクリーンショット 2024-01-07 15.44.36.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBd2xWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--47927f1af018e0914f3e5aeea8b07cf612dc157d/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2015.44.36.png)
- Select disk to partition は、「Virtual disk 1 (vda)」を選択

![スクリーンショット 2024-01-07 15.46.18.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBd3BWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--89c4b5dd8d51aa3c5aef392dee1c5cad75d24c1d/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2015.46.18.png)
- Partitioning scheme は、All file in on partition (recommended for new users)を選択

![スクリーンショット 2024-01-07 15.47.02.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBd3RWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--e9b6910c3204441c817cc2bf7e801fd69b89ab8d/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2015.47.02.png)
- Finish partitioning and write changes to disk を選択

![スクリーンショット 2024-01-07 15.48.22.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBd3hWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--27e79b07cf93a62e207c88a8ddd561aff7bd349f/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2015.48.22.png)
- Write the changes to disks? は、「Yes」を選択


![スクリーンショット 2024-01-07 15.55.51.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBdzFWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--1cb0c8703f4e91c5b8d4fb5a6116f55fafb146b3/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2015.55.51.png)
- ここから表示画面が乱れます（原因はわかりません）が、Participate in the package usage survey? は、「No」を選択

![スクリーンショット 2024-01-07 16.07.12.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBdzVWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--339528205700c4530775d7134770b6bbc54ec522/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2016.07.12.png)
- Choose software to install は、マニュアルのとおりに選択し、<Continue>を選択


![スクリーンショット 2024-01-07 16.11.31.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBdzlWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--46af40070fa6f7e70deba3055323b993c6af2f8f/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2016.11.31.png)
- Install the GRUB boot loader to your primary drive? は、「Yes」を選択

![スクリーンショット 2024-01-07 16.14.03.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeEJWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--99ee356c3816b93677a5fd00e95f6a0f9151f411/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2016.14.03.png)
- Device for boot loader installation は、「/dev/vda」を選択

![スクリーンショット 2024-01-07 16.16.17.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeEZWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--ad33818d3b71221229c0f75ca42a0a5624ee677c/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2016.16.17.png)
- インストールを終えると Please choose <Continue> to reboot. と表示されるので <Continue>を選択


4. Debian を起動する

![スクリーンショット 2024-01-08 19.03.48.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeEpWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--3a21739380e02d928feec049687f337f0e2ace5b/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-08%2019.03.48.png)
- さくらの VPS のサーバー一覧からサーバーを選択して、「起動する」をクリック

![スクリーンショット 2024-01-08 19.07.14.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeE5WQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--15e0dff9b4d15f33e1037d02c43abde703cbcf14/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-08%2019.07.14.png)
- 「実行」をクリック

![スクリーンショット 2024-01-07 16.45.06.png](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeFJWQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--54687ccd784d28ea3e714dcf798fe36a2f3a946c/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202024-01-07%2016.45.06.png)
- 起動した画面に設定したユーザー名を入力することで Debian にログインし、使用することができる
</details>

---

## 💡分かったこと・気付き
- まとめ方について、自身の未熟さ

---

## 🌞次の目標
- プラクティス「**UNIX・Linux について知る**」に着手、そして内容を確認

---

## ❤️‍🔥感じたこと
Linux のインストール手順をなんとかまとめることができましたが、スクリーンショットに収めていない箇所が幾つかあったり、読み手に分かりやすくもっとシュッと作れたのではないか？と反省しています。

明日は気持ちを切り替えて、新しいプラクティスに取り組みます💪🏻

---

## ⏰学習時間
- Today: 3 hours 46 min
- Total: 102 hours 21 min
