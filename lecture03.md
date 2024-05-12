# 第三回課題提出
* * * * 
### 1.アプリケーション起動
![AP起動](image/lec03image/01.png)
![AP入力](image/lec03image/04.png)
![AP入力](image/lec03image/05.png)
### 2.APサーバー名前とバージョン
* AP. puma ver. 5.6.5
* `kill`で停止
![AP停止](image/lec03image/02.png)
* `rails s` で再起動

* * * 
### 3.DBサーバー
* DB mysql ver. 8.0.35
* `sudo service mysqld stop` でDBサーバー停止
![DB停止](image/lec03image/03.png)
* 
* `sudo service mysqld start` の後に `rails s` でAPサーバー起動

* * * 
### 4.railsの構成管理ツール
* Bundler

* * * *

今回の課題から学んだ事
* 実行中のアプリケーションは、「Ctrl+C」で止めることができる
* APサーバー　Ruby 等のプログラムで作られたアプリケーションを実行
する為に必要なサーバー
* APサーバー　プログラムが置いてあるコンピュータ
* DBサーバー　データベースが置いてあるコンピュータ
* DBサーバー APとDB間のやり取りをしている
* DB　データを整理して検索しやすくした情報の集まりの事または データを入れておく箱
* Bundler　gemのバージョンやgemの依存関係を管理してくれるgemです。bundlerを使うことで、複数人での開発やgemのバージョンが上がってもエラーを起こさずに開発できる
* Bundler  パッケージ管理ツール
* gem      Rubyのパッケージもしくはライブラリ
* ライブラリ　便利なプログラムの部品をいっぱい集めて、ひとまとめにしたファイル
* puma    組み込みサーバー
* ruby  プログラミング言語
* Ruby on Rails  フレームワーク 型枠
* RDBMS　MySQL
* sql    DB に対してデータの操作を行う為の「言語」
### 感想
* ここまでかなり時間がかかってしまいました、少しずつできるようにはなっていると実感しているがまだまだ勉強不足は否めない
もっと復習,コミュニーツール等を利用していろいろなことを深掘りしていこうと思う