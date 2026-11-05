# 2026/11/05(木)
## 🧑🏻‍💻 本日の取り組み
### 📚 プラクティス『🌐🎩 Sinatra を使ってWebアプリケーションの基本を理解する』 
#### FBC Press: Sinatra
- 7.5 更新処理を作る 〜 7.10 この章の完成コード

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
### 7.5 更新処理を作る
#### 更新処理の全体の流れを確認する
**① 編集フォームから送信**
`POST` + `_method=patch`
タイトルや監督など、5項目の情報が送られる。
　　　↓
**② JSONファイルを読み込む**
`load_movies`で映画の配列を取得する。
　　　↓
**③ 更新する映画を探す**
`find_movie_from`で ID が一致する映画を見つける。
　　　↓
**④ 映画情報を書き換える**
`movie.merge!(movie_params)`で5項目を更新する。
　　　↓
**⑤ JSONファイルに保存**
`save_movies(movies)`で変更を保存する。
　　　↓
**⑥ 詳細画面へ移動**
更新に成功したら、映画詳細画面へリダイレクトする。

#### find_movie_from の追加
第6章では映画を探すために`find_movie`というメソッドを作成した。
```ruby
def find_movie(id)
  load_movies.find { |movie| movie["id"] == id }
end
```
今回も映画を探すが、新しく`find_movie_from`というメソッドを追加する。
```ruby
def find_movie_from(movies, id)
  movies.find { |movie| movie["id"] == id }
end
```
それぞれの違いを比較してみる。
|メソッド   |映画の探し方   |
|---|---|
|find_movie(id)   |メソッドの中で JSONファイルを読み込んで探す   |
|find_movie_from(movies, id)   |引数として受け取った配列から探す   |

今回の更新処理では、次のように JSONファイルを読み込む。
```ruby
movies = load_movies
```
↑この段階で、映画の配列はすでに`movies`に格納されている。
そのため、再度 JSONファイルを読み込む必要はない。
おそらく、**すでに読み込んだ配列を使って映画を探すため**に、`find_movie_from`メソッドを用意するということだと思う🤔（ここはよく分かっていない箇所）

#### movie.merge!(movie_params)で映画情報を書き換える
```ruby
movie_merge!(movie_params)
```
まず、`movie_params`は第5章で作成したメソッド。
これは、フォームから送られてきた5項目をハッシュにまとめる役割がある。
```ruby
{
  "title" => "月面カフェ",
  "director" => "山田アキラ",
  "year" => "2042",
  "genre"  => "SF",
  "description" => "月面の喫茶店を舞台にした新しい物語。"
}
```
一方、`movie`には、JSON から読み込んだ既存の映画情報が入っている。
たとえば、更新前のタイトルが『月面喫茶』だったとする。
|項目   |更新前   |更新後   |
|---|---|---|
|title   |月面喫茶   |月面カフェ   |
|director   |山田アキラ   |山田アキラ   |
|year   |2042   |2042   |
|genre   |SF   |SF   |
|description  |以前の紹介文   |新しい紹介文   |

`merge!`は、指定したハッシュの内容を元のハッシュに反映するメソッド。
今回の場合、`movie_params`の値で、既存の`movie`の該当する項目を書き換える。
そして、`!`が付いているので**破壊的メソッド**だと分かる。
つまり、新しいハッシュを作るだけでなく、配列の中にある映画のハッシュそのものを変更する。

#### save_movies(movies)で保存する
`merge!`で映画情報を書き換えても、それだけでは JSONファイルの内容は変わらない。
最後に次の処理を行う必要がある。
```ruby
save_movies(movies)
```
これも第5章で作成したメソッドで次のような関係になっていた。
- `JSON.generate`：Ruby の配列・ハッシュを JSON形式の文字列に変換する。
- `File.write`：変換した文字列を JSONファイルに書き込む。

今回は次のような関係になる。
- `merge!`でメモリ上のデータを変更し、`save_movies`でファイルに保存する。

#### 更新後に詳細画面へリダイレクトする
最後は、更新した映画の詳細画面へ移動する。
```ruby
redirect "/movies/#{movie["id"]}"
```
更新後も同じ映画の ID を使って詳細画面へ移動する。

ここまでの流れを整理すると、次のようになる。
- `movie.merge!`：映画情報を書き換える。
- `save_movies`：JSONファイルに保存する。
- `redirect`：更新した映画の詳細画面へ移動する。

#### ファイルとディレクトリの位置関係を確認する
`app.rb`
```text
メソッド定義
  ├─  load_movies
  ├─  save_movies
  ├─  find_movie
  ├─  find_movie_from  ← 今回追加
  └─  movie_params

ルート定義
  ├─  GET /
  ├─  GET /movies
  ├─  GET /movies/new
  ├─  GET /movies/:id/edit
  ├─  GET /movies/:id
  ├─  POST /movies
  └─  PATCH /movies/:id  ← 今回追加
```

#### この節で追加した処理を確認する
|処理   |何をするのか   |
|---|---|
|load_movies   |JSONファイルを読み込む   |
|find_movie_from   |URL の ID と一致する映画を探す   |
|halt 404   |映画が存在しない場合に処理を停止する   |
|merge!   |映画情報を更新する   |
|save_movies   |更新した配列を JSONファイルに保存する   |
|redirect   |更新後の詳細画面へ移動する   |

### 7.6 詳細画面から編集へ進む
#### 追加するリンクについて確認する
```erb
<a class-"button-link" href="/movies/<%= h(@movie["id"]) %>/edit">編集する</a>
```
|記述   |役割   |
|---|---|
|\<a\>   |リンクを作る HTML要素   |
|href   |リンク先の URL を指定する属性   |
|/movies/   |映画の URL   |
|@movie["id"]   |詳細画面で表示している映画の ID   |
|/edit   |編集画面を表す URL の末尾   |
|h(...)   |HTML として安全に出力するためのエスケープ   |
|class="button-link"   |CSS でボタン風に装飾するためのクラス   |

たとえば、映画の ID が`abc-123`なら、リンク先は次のようになる。
```text
/movies/abc-123/edit
```
リンクをクリックすると、7.3 で追加した次のルートが呼び出される。
```ruby
get "/movies/:id/edit" do
```
その後、編集対象の映画を取得し、`views/edit.erb`を表示する。
つまり、**詳細画面から編集画面への移動経路を作る**ということ。

#### 編集機能全体のつながり
**映画の詳細画面**
`views/show.erb`
　　　↓
**編集画面**
`GET /movies/:id/edit`
　　　↓
**更新処理**
`PATCH /movies/:id`
　　　↓
**更新後の詳細画面**
更新した情報が表示される。

### 7.7 詳細画面から削除する
#### 削除フォームの仕組みを確認する
```erb
<form action="/movies/<%= h(@movie["id"]) %>" method="post">
  <input type="hidden" name="_method" value="delete">
  <button type="submit" class="danger-button">削除する</button>
</form>
```
|記述   |役割   |
|---|---|
|form   |削除リクエストを送信するフォーム   |
|action   |削除対象の映画の URL   |
|method="post"   |ブラウザから POST で送信する   |
|type="hidden"   |画面に表示しない入力欄   |
|name="_method"   |HTTPメソッドを読み替えるための項目名   |
|value="delete"   |DELETE として扱ってほしいことを指定する   |
|type="submit"   |フォームを送信するボタン   |
|class="danger-button"   |削除ボタン用の CSSクラス   |

#### page-actions とは？
FBC Press： Sinatra では、詳細画面の3つの操作を次のような<div>でまとめている。
```erb
<div class="page-actions">
  ...
</div>
```
`page-actions`は、詳細画面の主な操作をまとめるためのクラス。

### 7.8 削除処理を作る
#### 削除処理の流れを確認する
```
delete "/movies/:id" do
  movies = load_movies
  movie = find_movie_from(movies, params["id"])
  halt 404, "映画が見つかりません" if movie.nil?

  movies.delete(movie)
  save_movies(movies)

  redirect "/movies"
end

```
**① 詳細画面から削除ボタンを押す**
`POST` + `_method=delete`
　　　↓
**② Rack が DELETE として読み替える**
`DELETE /movies/:id`
　　　↓
**③ JSONファイルから映画一覧を読み込む**
`load_movies`
　　　↓
**④ 削除対象の映画を探す**
`find_movie_from`
　　　↓
**⑤ 配列から映画を削除する**
`movies.delete(movie)`
　　　↓
**⑥ JSONファイルに保存する**
`save_movies(movies)`
　　　↓
**⑦ 映画一覧へ移動する**
`redirect "/movies"`

#### load_movies で映画一覧を読み込む
```ruby
movies = load_movies
```
JSONファイルから映画の一覧を読み込み、Ruby の配列として`movies`に格納する。
たとえば、次のような状態。
```text
movies
  ├─  月面喫茶
  ├─  北風のリズム
  └─  週末ロケット
```
この配列から、削除する映画を探し出す。

#### find_movie_from で削除対象を探す
```ruby
movie = find_movie_from(movies, params["id"])
```
- `movies`：映画一覧の配列
- `params["id"]`：URL に含まれる映画の ID
- `movie`：ID が一致した映画のハッシュ

たとえば、ID が`id-001`の映画を削除する場合、対象の「月面喫茶」が`movie`に格納される。

#### halt 404 で存在しない映画を処理する
```ruby
halt 404, "映画が見つかりません" if movie.nil?
```
指定した ID の映画が見つからなかった場合は、`404`を返して処理を停止する。
存在しない映画を削除することはできない。

#### movies.delete(movie) で映画を削除する
```ruby
movies.delete(movie)
```
`delete`は、Ruby の配列から指定した要素を削除するメソッド。
たとえば、次の配列があったとする。
```text
削除前のmovies
  ├─  月面喫茶
  ├─  北風のリズム
  └─  週末ロケット
```
ここで「月面喫茶」を削除すると、
```text
削除後のmovies
  ├─  北風のリズム
  └─  週末ロケット
```
という状態になる。
つまり、`movies.delete(movie)`は、配列から対象の映画を取り除く処理。
**この段階では、まだ JSONファイルから削除されたわけではない。**

#### save_movies(movies) で JSONファイルに保存する
```ruby
save_movies(movies)
```
配列から映画を削除しただけでは、JSONファイルの内容は変わらない。
そこで、変更後の配列を JSONファイルに書き込む。
- `movies.delete(movie)`：メモリ上の配列から削除する。
- `save_movies(movies)`：変更した配列を JSONファイルに保存する。

#### redirect "/movies" で一覧画面へ移動する
```ruby
redirect "/movies"
```
削除された映画はもう存在しないため、削除した映画の詳細画面には戻らない（戻れない）。
そのため、残っている映画を確認できる一覧画面へ移動する。

#### 更新処理と削除処理を比較する
|処理の内容   |PATCH（更新）   |DELETE（削除）   |
|---|---|---|
|映画一覧を読み込む   |load_movies   |load_movies   |
|対象の映画を探す   |find_movie_from   |find_movie_from   |
|見つからない場合   |404   |404   |
|メインの処理   |movie.merge!   |movies.delete   |
|JSONファイルに保存   |save_movies   |save_movies   |
|移動先   |詳細画面   |一覧画面   |

#### 考えてみよう
##### なぜ編集フォームの表示は GET で、更新処理は PATCH なのでしょうか。
- `GET`：編集画面を表示するだけで、映画のデータは変更しないため。
- `PATCH`：フォームから送信された情報を使って、既存の映画データを更新するため。

##### なぜ HTML フォームは PATCH や DELETE を直接送れないのに、Sinatra では patch や delete のルートを書けるのでしょうか。
HTMLフォームが基本的に`GET`と`POST`にしか対応していないため。
そこで、POST と hidden input の`_method`を組み合わせ、Rack の method override によって PATCH や DELETE を扱えるようにしている。
##### 削除後に、削除した映画の詳細画面ではなく一覧画面へ移動するのはなぜでしょうか。
削除した映画は存在しなくなり、詳細画面を表示できないため。
そのため、残っている映画を確認できる一覧画面へ移動する。

---

## ⏭️ 次回
### 📚 プラクティス『🌐🎩 Sinatra を使ってWebアプリケーションの基本を理解する』
#### FBC Press: Sinatra
- 第8章 リダイレクトは二つのリクエストをつなぐ

---

## ✍🏻 感想
第7章では、映画の登録・一覧表示・詳細表示・編集・削除と、一通りの機能を実装しました。
まだ「あれ？このファイルは何と繋がって、何をするんだっけ？」となることもありますが、何度も動かして確認しながら慣れていきたいです！

---

### ⏰ 学習時間
- Today:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 4 hours 56 min
- Total: 1683 hours 51 min
