# 2026/11/04(水)
## 🧑🏻‍💻 本日の取り組み
### 📚 プラクティス『🌐🎩 Sinatra を使ってWebアプリケーションの基本を理解する』 
#### FBC Press: Sinatra
- 7.5 更新処理を作る 〜 

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
