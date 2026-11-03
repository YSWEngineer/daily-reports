# 2026/11/03(火)
## 🧑🏻‍💻 本日の取り組み
### 📚 プラクティス『🌐🎩 Sinatra を使ってWebアプリケーションの基本を理解する』 
#### FBC Press: Sinatra
- 7.3 編集画面を表示する 〜 7.4 編集フォームを作る

---

## 🧩 タスクばらし
<details><summary> 🧩 タスクばらし ※ 随時、追加・変更あり</summary>

- [ ] STEP1：参考教材を読んで、Sinatra と Webアプリの基本を理解する。
- [ ] STEP2：開発環境を準備し、GitHub のリポジトリを作成する。
- [ ] STEP3：リクエスト・レスポンス、ルーティング、ERB を理解する。
- [ ] STEP4：フォームと HTTPメソッドの関係を理解する。
- [ ] STEP5：JSONファイルへのデータの保存・読み込みを理解する。
- [ ] STEP6：メモアプリの一覧・詳細・追加・編集・削除を実装する。
- [ ] STEP7：REST・PRGパターンを意識し、Networkタブで動作を確認する。
- [ ] STEP8：XSS対策、RuboCop、ERB Lint を確認する。
- [ ] STEP9：README を作成し、動作確認を行う。
- [ ] STEP10：スクリーンショットを用意して提出・レビュー・修正する。
  - [ ] 完成したアプリのスクリーンショット
  - [ ] XSS対策のスクリーンショット
  - [ ] RuboCop のスクリーンショット
  - [ ] ERB Lint のスクリーンショット
- [ ] STEP11：余裕があれば CSS と 404ページにも対応する。
</details>

---

## 💡 本日の学び・気付き
### 7.3 編集画面を表示する
```ruby
get "/movies/:id/edit" do
  @movie = find_movie(params["id"])
  halt 404, "映画が見つかりません" if @movie.nil? 

  erb :edit
end
```
今回追加する URL は、次のとおり。
```text
/movies/:id/edit
```
たとえば、映画の ID が`abc-123`なら、実際の URL は次のようになる。
```text
/movies/:id/edit
```
この URL は、特定の映画の編集画面を表す。
これまで学習した URL と比較してみる。
|URL   |役割   |
|---|---|
|/movies   |映画一覧を表示する   |
|/movies/:id   |特定の映画の詳細を表示する   |
|/movies/:id/edit   |特定の映画の編集画面を表示する   |

同じ映画でも、URL によって表示する画面や役割が異なる。
これは前回のプラクティスの課題で学んだ内容。

#### なぜ GET を使うのか？
今回のルートは次のようになる。
```ruby
get "/movies/:id/edit" do
```
ここで`GET`を使う理由は、**編集画面を表示するだけで、まだ映画のデータを変更しないから。**

#### HTTPメソッドの役割を整理する
|HTTPメソッド   |今回の用途   |
|---|---|
|GET   |編集フォームを表示する   |
|PATCH   |編集フォームから送られた情報で映画を更新する   |

とりあえず、今は「編集するための画面を取得するから`GET`」という理解でいいと思う。

#### find_movie で映画を探す
```ruby
@movie = find_movie(params["id"]
```
この処理を分解すると、次のようになる。
- `params["id"]`：URL に含まれている映画の ID を取得する。
- `find_movie`：その ID に一致する映画を探す。
- `@movie`：見つけた映画の情報を格納する。

たとえば、タイトルが「月面喫茶」の映画を編集する場合、その映画の情報が`@movie`に格納される。

#### 映画が見つからなかった場合
これは、第6章でも登場した処理と同様。
```ruby
halt 404, "映画が見つかりません" if @movie.nil?
```
指定した ID の映画が存在しなければ、編集画面を表示せずに`404`を返す。

### 7.4 編集フォームを作る
#### 編集フォームとは？
編集フォームは、すでに登録されているデータを変更するための入力画面のこと。
新規フォームと似ているが一緒にしないこと。
- **新規登録フォーム**：新の映画の情報を入力する。
- **編集フォーム**：保存済みの映画情報を最初から表示する。

#### value属性とは？
テキストの入力欄には、`value`という属性がある。
これは入力欄に最初から表示しておく値を指定するもの。
今回なら、保存済みのタイトルや監督名などを表示するために使う。
おそらく、イメージは以下のような感じ。
```text
input
  └─ value
        └─ 保存済みの映画情報
```
一方、紹介文には`textarea`を使う。
`textarea`は、複数行の文章を入力するための要素。

#### なぜ5項目すべてをフォームに用意するのか？
映画図鑑では、次の5項目を送信できるようにする。
|項目   |HTML要素   |
|---|---|
|タイトル   |input   |
|監督   |input   |
|公開年   |input   |
|ジャンル   |select   |
|紹介文   |textarea   |

たとえば、タイトルだけ変更した場合でも、監督・公開年・ジャンル・紹介文の現在の値を一緒に送る。
その理由は、フォームから届いた値を使って映画の情報を更新するため。

#### 指定されたコードを入力する
`views/edit.erb`ファイルを作成し、指定されたコードを入力する。
Sinatra が起動している状態で、映画の編集 URL にアクセスすると映画編集が表示される。

<a href="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjg1MzUzLCJwdXIiOiJibG9iX2lkIn19--99d9cdfbaea36a68a485a26fa28a28bebd0db89f/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-11-03%2020.04.21.png" target="_blank" rel="noopener noreferrer"><img src="https://bootcamp.fjord.jp/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsiZGF0YSI6Mjg1MzUzLCJwdXIiOiJibG9iX2lkIn19--99d9cdfbaea36a68a485a26fa28a28bebd0db89f/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-11-03%2020.04.21.png" width="1036" height="591" alt="スクリーンショット 2026-11-03 20.04.21.png"></a>

#### input と textarea の初期値の指定方法の違い
##### input の場合
`input`は、`value`属性に初期値を指定する。
```html
<input type="text" name="title" value="月面喫茶">
```
この場合、入力欄には最初から「月面喫茶」と表示される。

##### textarea の場合
一方、`textarea`は**開始タグと終了タグの間に初期値を記述する。**
```html
<textarea name="description">月面にある小さな喫茶店を舞台にした物語。</textarea> 
```

##### 違いを整理すると
|HTML要素   |初期値を指定する場所   |
|---|---|
|input   |value属性   |
|textarea   |開始タグと終了タグの間   |

- `input`は、1行の入力欄を作る要素で、値を`value`属性で指定する。
- `textarea`は、複数行の文章を入力する要素。そのため、HTML では要素の中に初期表示する文章を記述する仕組みになっている。

覚え方：「**input は value、textarea はタグの中**」

---

## ⏭️ 次回
### 📚 プラクティス『🌐🎩 Sinatra を使ってWebアプリケーションの基本を理解する』
#### FBC Press: Sinatra
- 7.5 更新処理を作る

---

## ✍🏻 感想
今回は編集フォームを作成しました。
既存の映画情報をフォームに表示する仕組み、`input`と`textarea`で初期値を指定する方法など、新しく理解することがいくつかありました。

特に、`input`は`value`属性、`textarea`は開始タグと終了タグの間に値を記述するという違いに戸惑いましたが、実際のコードと照らし合わせることで整理できました。
あとは何度もコードに触れて挙動を確かめながら、少しずつ慣れていくことですね🏋🏻

あっ、あと [Q&A](https://bootcamp.fjord.jp/questions/2162) に質問を投稿しました。
ゆるーく募集しています😊👋🏻

---

### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2 hours 28 min
- Total: 1678 hours 55 min
