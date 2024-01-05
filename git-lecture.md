# 第三回課題提出
* * * * 
### 1.アプリケーション起動
![1](raisetech003/img/01.png)
* * *
### 2.APサーバー名前とバージョン
* AP. puma ver. 5.6.5
* `kill`で停止
![2](raisetech003/img/02.png)
* `rails s` で再起動

* * * 
### 3.DBサーバー
* DB mysql ver. 8.0.35
* `sudo service mysqld stop` でDBサーバー停止
* ![3](raisetech003/img/03.png)
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