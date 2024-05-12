# 第５回課題


## 課題提出
* ec2上にサンプルアプリケーションのデプロイ　組み込みサーバー
* Web サーバー(Nginx)
* AP サーバー(Unicorn)
* ELB(ALB) 
*  S3 

* * *

## 環境構築
* raisetech-live8-sample-appのREADME

  - `ruby 3.1.2`
  - `Bundler 2.3.14`
  - `Rails 7.0.4`
  - `Node v17.9.1`
  - `yarn 1.22.19`

* * *

### ec2の環境構築

- パッケージの更新
```
sudo yum update -y
```

- gitインストール
```
sudo yum install git
```

- サンプルアプリケーションのクローンを作成
```
git clone https://github.com/yuta-ushijima/raisetech-live8-sample-app.git
```

- railsに必要なパッケージのインストール
```
sudo yum  -y install git make gcc-c++ patch libyaml-devel libffi-devel libicu-devel zlib-devel readline-devel libxml2-devel libxslt-devel ImageMagick ImageMagick-devel openssl-devel libcurl libcurl-devel curl
```

- RVM(rubyのバージョン管理)インストール

```
curl -L get.rvm.io | bash -s stable
gpg2 --keyserver hkp://keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
curl -sSL https://rvm.io/mpapis.asc | gpg2 --import -
curl -sSL https://rvm.io/pkuczynski.asc | gpg2 --import -
\curl -sSL https://get.rvm.io | bash -s stable

```

- Ruby

```
rvm install "ruby-3.1.2"
source /home/ec2-user/.rvm/scripts/rvm
rvm use --default 3.1.2
rvm rubygems latest
source ~/.bash_profile
```
- rubyバージョン確認

```
ruby -v
```
nvm(node.jsのバージョン管理)

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```
- nvmの設定、インストール、確認

```
. ~/.nvm/nvm.sh
nvm install 17.9.1
nvm -v
```

- npmを使用yarnインストール、確認

```
npm install -g yarn@1.22.19
yarn -v
```

-　Bundlerのインストール,確認

```
gem install bundler -v 2.3.14
bundler -v
```

- MariaDB用パッケージを削除

```
sudo yum remove -y mariadb-*
```

-  MySQLのリポジトリをyumに追加

```
sudo yum localinstall -y https://dev.mysql.com/get/mysql80-community-release-el7-11.noarch.rpm
```

- MySQLに必要なパッケージを取得

```
sudo yum install --enablerepo=mysql80-community mysql-community-server
```
```
sudo yum install --enablerepo=mysql80-community mysql-community-devel

```

- MySQL関連のパッケージを出力

```
yum list installed | grep mysql
```
- mysqldを起動,mysqldの状態を確認
```
sudo systemctl start mysqld
```
```
systemctl status mysqld.service
```
- mysqldの停止
```
sudo service mysqld stop
```
- railsのインストール
```
gem install rails -v 7.0.4
bundle install
rails -v
```
- database.ymlの作成
```
cp config/database.yml.sample config/database.yml
```

- database.ymlの編集
```
default: &default
  adapter: mysql2
  encoding: utf8mb4
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: RDSのユーザー名
  password: RDSのパスワード
  host: RDSのエンドポイント
```
- setup
```
bin/setup
```
```
bin/dev
```
- EC2のセキュリティーグループに3000番ポートを追加
![dep](image/lec05image/deploy1.png)

* * *

## Unicorn

* unucorn起動コマンド

```
bundle exec unicorn -c config/unicorn.rb -D -E development

```
* 起動の確認

```
ps -ef | grep unicorn | grep -v grep

```

* 停止コマンド

```
sudo kill -QUIT `cat /home/ec2-user/raisetech-live8-sample-app/tmp/pids/unicorn.pid`

```

* unicorn.rbの編集
 
![unicorn.rb](image/lec05image/unicorn.rb.png)


## nginxのインストール、動作確認

* nginxのインストール

```
sudo amazon-linux-extras install nginx1
```
* nginxの起動
```
sudo systemctl start nginx
```
* nginxのステータス確認
```
sudo systemctl status nginx
```
* nginxの停止
```
sudo nginx -s stop
```

* nginx動作確認

![nginx](image/lec05image/nginx.png)


* nginx.configの編集


![nginx.config](image/lec05image/nginx.config.png)

* * *
    
## unicornとNginxの連携　デプロイ

`rails assets:precompile`

![deploy](image/lec05image/deploy.png)
画像の表示と保存を確認





## ELB（ALB）の追加
![alb](image/lec05image/ALBsyousai.png)
* * *

![alb](image/lec05image/ALBta-get.png)
* * *

![alb](image/lec05image/ALB.png)
* * *

![alb](image/lec05image/ALBdepu.png)

* development.rbにconfig.hosts << "ALBのDNS名"追加
* nginx.conf内のservernameにも追加


## S3
* /config/storage.ymlの編集

```zsh
amazon:
 service: S3
 access_key_id: アクセスキー
 secret_access_key: シークレットキー
 region: ap-northeast-1
 bucket: バケット名
 ```
* development.rbを修正
config.active_storage.serviceをamazonに変更

![s3](image/lec05image/s3fullakuse.png)
* * *
![s3](image/lec05image/s3depu.png)
* * *
![s3](image/lec05image/s3gazoou.png)
* * *


## 構成図
![AWS](image/lec05image/AWS.drawio.png)


