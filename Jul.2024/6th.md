# 2024/07/06(土)
## 🧩 タスクばらし
### プラクティス『Ruby初級』の修了
- [x] 各参考ページを確認
- [x] 書籍『スラスラ読めるRubyふりがなプログラミング』
- [ ] 動画講座
- [ ] 課題取り組み


## 📋 段取り
<details><summary>各参考ページを確認</summary>

- [x] [ホワイの(感動的)Rubyガイド](http://www.aoky.net/articles/why_poignant_guide_to_ruby/chapter-1.html)
- [x] [TryRuby](https://try.ruby-lang.org/)
- [x] [ゼロからわかるRuby超入門の読み方](https://bootcamp.fjord.jp/pages/289)
- [x] [学習を加速させるインデックス読書術](https://qiita.com/dkatsura/items/3364b293ed1451a66a8a)
- [x] [Ruby の公式リファレンスが読めるようになる本](https://zenn.dev/jnchito/books/how-to-read-ruby-reference)
- [x] [オブジェクト指向スクリプト言語 Ruby リファレンスマニュアル](https://docs.ruby-lang.org/ja/latest/doc/index.html)
- [x] [【新人プログラマ応援】公式ドキュメントも読もう - Qiita](https://qiita.com/chooyan_eng/items/cd0d3174b77ff1e02c3f)
</details>

<details><summary>書籍『スラスラ読めるRubyふりがなプログラミング』</summary>

- [x] Chapter 1
- [x] Chapter 2
- [x] Chapter 3
- [x] Chapter 4
</details>

<details><summary>動画講座</summary>

- [ ] [ゼロからわかるRuby超入門動画講座](https://bootcamp.fjord.jp/pages/374)
   - [x] CHAPTER 2
   - [x] CHAPTER 3
   - [x] CHAPTER 4
   - [x] CHAPTER 5
   - [x] CHAPTER 6
   - [x] CHAPTER 7
   - [x] CHAPTER 8
   - [ ] CHAPTER 9
   - [ ] CHAPTER 10
   - [ ] CHAPTER 11
</details>

<details><summary>課題取り組み</summary>

- [ ] ゼロからわかる Ruby 超入門の各章の練習問題
   - [x] CHAPTER 2
   - [x] CHAPTER 3
   - [x] CHAPTER 4
   - [x] CHAPTER 5
   - [x] CHAPTER 6
   - [x] CHAPTER 7
   - [ ] CHAPTER 8
   - [ ] CHAPTER 9
   - [ ] CHAPTER 10
- [ ] [TryRuby](https://try.ruby-lang.org/)
</details>


## ✍🏻 本日の取り組み
### 書籍『[RubyとRailsの学習ガイド2023](https://garnettech373.com/books/rrsg.html)』
- 第1章 ~ 第4章


## 💡 本日の学び・気付き
### 第1章 はじめに
- Ruby や Rails を学ぶ上で、頭の中に Ruby そして Rails 技術全体の地図を描き、イメージすること。
- 全体を把握するために、ひとまずは「そういう技術があるのだな」くらいで捉えれば大丈夫。
- お勧めの勉強方法は、まずは Ruby と Rails をスタート地点に、自分ができる範囲を深掘りして理解を深め、得意なところ、好きなところを見つけていくのが良い。また、**もしも1つの技術の学習が難しくて進めなくなったときには、その周辺や地図の他の場所を調べたりして、そのあとでまた戻って積み重ねて学ぶ**のがお勧め。その方が挫折しづらいし、分からないこともあとで学ぶと、別の所で学んだことが理解を助けることもある。
- たのしさは学びを継続する燃料となる。

##### 環境構築
- すぐに動かしたいとき、環境構築でつまづいたときは、ブラウザ上で Ruby プログラムを実行できる**TryRuby Playground**や**GitHub Codespaces**がお勧め。

##### Ruby を手軽に使いたい（Rails をつかわない）
- **TryRuby Playground** ではブラウザ状で Ruby のプログラムを実行することができる。一部で実行できない制限もあるが環境構築をせずに気軽に Ruby プログラミングができる。

##### Ruby をしっかり使いたい（Rails を使う）
- Rails ではたくさんの Gem を使う。
- インストール時にコンパイルが必要な Native extention と呼ばれる C 言語で書かれた Gem も必要となるため、環境構築がやや難しくなる。
- macOS では rbenv、Command line tools、homebrew を使って Ruby をインストールする方法がお勧め。
- GitHub Codespaces では Rails 用テンプレートが用意されていて、かんたんに環境を作って Rails アプリを開発できる。無料プランでも月 60 時間使うことができる。


### 第2章 Railsアプリ関連技術地図
- 量の多さに圧倒されそうになるが、全てを一度に学ぶ必要はなく、ある範囲から勉強を進めて、少しずつ広げていけば良い。


### 第3章 Ruby, Rails地方
##### Ruby
- Ruby はプログラミング言語。Ruby だけでもプログラムを書くことができる。
- プログラミングを学ぶ人へ Ruby を勧める点は
    - プログラムが短く読みやすいこと。
    - 「おまじない」と呼ばれる説明が困難な事柄が学習の過程であまり出てこないこと、などがある。
- Ruby というプログラミング言語には**「プログラマーが楽しく開発できる言語」を目指して開発されている**という特徴がある。

##### プログラミングを Ruby で始める
- ゼロからわかる Ruby 超入門は、Ruby でよく使われる整数、文字列、配列、ハッシュと言ったオブジェクトを説明している。また、エラーメッセージの読み方とその対処法方、リファレンスマニュアルの調べ方、プログラミングの間違いを見つけて直すデバッグ方法も学べるため、自分で調べながらプログラミングする力を身に付けることができる。

##### Ruby について調べる
- Ruby について調べたいときには**Rubyリファレンスマニュアル**を利用する。たとえば Array クラスのメソッド一覧を調べるには、「組み込みライブラリ Builtin libraries - Array」と辿る。辞書的な使い方のほかに、全体を一読するのもお勧め。まずは Array, Hash, String, Enumerable だけでも読んでおくと Ruby を書く力が上がる。
- るりまの全文検索として**るりまサーチ**が用意されている。たとえば、メソッド名から機能を調べたいようなケースで役立つ。
- 有志により不定期発行されている**Rubyist Magazine**は Rubyist へのインタビュー、コミュニティ活動レポート、Ruby の技術的な話など、Ruby コミュニティの話題を読むことができる。

##### Rails
- Rails は Web アプリ（ブラウザからアクセスするアプリ）を簡単に作るための様々な便利な道具を集め、開発に役立つ規約を定めたフレームワーク。Rails アプリを作るときには Ruby と Rails の両方の知識を使ってアプリを作っていくことになる。

##### Rails を学ぶ前に Web アプリについて学ぶ
- Rails では書いたソースコードファイルをたくさんのフォルダに規約通りに整理して置いて Web アプリ開発を進める。そのルールを覚えることも最初は大変かもしれない。そこで Rails を学ぶ前に、Ruby をつかって1ファイルで簡単に Web アプリを書ける道具 Sinatra を使って Web アプリの概要を学ぶのも良い方法。


### 第4章 フロンドエンド、スマートフォンアプリ地方

##### HTTP, HTTPS
- Web で利用されている通信プロトコル（取り決められているルール）に HTTP がある。Web サーバは HTTP をつかって通信することができるサーバであり、HTTP プロトコルでブラウザやスマートフォンアプリと通信する。
- Rails アプリは Puma などのアプリケーションサーバを利用して起動する。
- アプリケーションサーバは Web サーバーの一種で、Web アプリを起動して HTTP 通信を可能にするための基礎機能を提供する。

##### 暗号技術
- Web では HTTPS 通信などで暗号技術を多く利用している。

##### HTML, CSS
- ブラウザで表示するページを記述するにはHTML（HyperText Markup Language）と CSS（Cascading Style Sheets）と呼ばれる言語を使う。
- ブラウザと Web アプリがやりとりするとき、HTTP を使って HTML や CSS がブラウザへ送信される。

##### JavaScript
- ブラウザ上で動くプログラミング言語として、JavaScript があります。JavaScript や HTML, CSS をつかってブラウザに描画する技術群はフロントエンドやクライアントサイドと呼ばれる。
- それに対して、HTTP 通信でフロントエンドから見て対岸にあたる、Rails などで構成されて技術群をバックエンドやサーバーサイドと呼ぶ。

##### TypeScript
- TypeScript は 	JavaScript へ、トランスパイル（変換）できるプログラミング言語で、ブラウザ上で動作可能なプログラムを書くことができる。JavaScript の機能に加えて静的型付けである特徴を持っている。
- JavaScript が動作する環境で広く使われている言語。

##### React, Vue.js
- React は Web ユーザーインターフェイスを作るための JavaScript ライブラリ。JavaScript や TypeScript を使ってブラウザ上で動作するページを作成する。
- Rails と組み合わせて使うときは主に2つの方法がある。
    1. Rails で HTML を作成した上で React を使う方法。
    2. React で SPA（Single Page Application）と呼ばれるブラウザ上で動作するフロントエンドアプリを作り、バックエンドである Rails アプリと API で接続して JSON をやり取りする方法。
- SPA の場合、バックエンドで動作する API を提供するアプリを同じ言語で書くことができる Next.js で構築することもできる。
- また、別の種類のライブラリとして、Vue.js がある。
- React と Vue.js は同じ場面で使うライブラリ。通常、どちらか一方を選んで使うことになる。

##### Next.js, Nuxt
- Next.js は React を使った Web アプリ作成のためのフレームワーク。フロントエンドアプリ作りの道具を提供してくれる。また、HTML, CSS, JavaScript を生成する手法である CSR（Client Side Rendering：ブラウザ上で生成する）、SSR（Server Side Rendering：バックエンドサーバーで生成する）、SSG（Static Site Generation：静的ファイルとして事前生成）などに対応するのが簡単になる。
- また、バックエンドで動作する API を提供するアプリを作ることもできる。
- 別の種類のフレームワークとして、Vue.js を使った Web アプリ作成のためのフレームワーク Nuxt がある。
- Next.js と Nuxt は同じ場面で使うフレームワーク。通常、どちら一方を選んで使うことになる。

##### WebAssenmbly（Wasm）
- WebAssenmbly（Wasm）はブラウザ上でプログラムを実行できる形式を定めたバイナリ命令フォーマット。ブラウザ上で動作するプログラムのプログラミング言語として JavaScript が使われるが、Wasm を使うことで他のプログラミング言語で書かれたプログラムをブラウザ上で実行することが可能になる。ただし、Wasm から DOM（Document Object Model：HTML を扱うためのインターフェイス）へアクセスするためには JavaScript と比較して様々な制限がある。
- 現在は様々な環境で Wasm バイナリを動作させる仕様 WASI（WebAssembly System Interface）の普及も進みつつあり、ブラウザの他にも、各種 OS でのコンテナ環境、サーバーレス基盤や CDN などの動作するエッジコンピューティングなど、Wasm バイナリ化した Ruby プログラムが動作する環境が増えている。

##### スマートフォンアプリ
- スマートフォンアプリの主な OS として、iOS と Android がある。iOS においてアプリを作るときの言語には Swift を使う。Android においてアプリを作るときの言語には Kotlin を使う。Kotlin は JVM（Java Virtual Machine）上で動作するプログラムを生成する。

##### JSON
- データをやりとりすることを目的としたデータ形式として、JSON（JavaScript Object Notation）がある。たとえば、スマートフォンアプリと Rails アプリでデータをやりとりするときには、JSON がよく利用される。また、ブラウザ上のフロントエンドを SPA（Single Page Application）とするときにも、Rails アプリとのデータのやりとりには HTML の替わりに JSON を使う。
- Ruby では Hash オブジェクトに対して to_jsonメソッドを使ったり、Rails では jbuilder などを使って JSON を作成することができる。

##### OpenAPI, Swagger
- OpenAPI は API 仕様（API スキーマとも呼ばれる）を記述する記法と、それに関連する動作するソフトウェア。
- OpenAPI は API 仕様を定義して見やすいドキュメントを生成したり、相手側の替わりをするテストプログラムであるモックを自動生成したりと、風呂とエンド開発者、スマートフォンアプリ開発者とバックエンド開発者とのやりとりをスムースに楽にするための機能を提供する。
- OpenAPI はかつては Swagger と呼ばれていたが、標準化され OpenAPI となった。

##### GraphQL
- GraphQL は API のためのクエリ言語（DB における SQL に相当）と言える。フロントエンドやスマートフォンアプリで画面を表示するときに必要な情報をバックエンドから集めようとしたとき、従来の REST API では複数のリクエストの発行が必要になったり、余分な情報を取得してしまうため通信コストが掛かることもある。そこで、GraphQL API をバックエンドで提供し、フロントエンドやスマートフォンアプリで必要な情報を指示して過不足なく取得する世界を作るのが GraphQL 。


## 📍 次回
### 書籍『RubyとRailsの学習がガイド2023』
- 第5章 ~


## ❤️‍🔥 感想
### ✅ 復習に入る前に......
ゼロからわかるRuby超入門動画講座の復習に入る前に、書籍『[RubyとRailsの学習ガイド2023](https://garnettech373.com/books/rrsg.html)』を読むことにしました。Ruby や Ruby on Rails を学ぶ上で必要な技術全体のイメージを描きやすくしてくれる内容で、私のような初学者には必読だと感じました。

分かりやすい解説に可愛らしいイラストのおかげで楽しみながらインプットできています。裏表紙には「**ファンクラブ**」と「**会報**」の文字が......ファンクラブの会報にしては内容が濃すぎます☺️✨

![IMG_9002.jpeg](https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBMnljQXc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--e48802e12d28b59f23435423cc2e5dcdb40c7430/IMG_9002.jpeg)


## ⏰ 学習時間
- Today:&nbsp;&nbsp; 4 hours 50 min
- Total: 412 hours 40 min
