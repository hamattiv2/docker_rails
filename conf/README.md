# rails 環境の構築

## rails アプリケーションの作成

```
docker-compose run web rails new . --force --database=mysql
```

## 作成した rails アプリケーション含めビルド

```
docker-compose build
```

## DB 情報の書き換え

```
# config/database.ymlの該当箇所を以下のようにする

default: &default
  adapter: mysql2
  encoding: utf8mb4
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password: password
  host: db
```

```rails用のDB作成しコンテナ起動
docker-compose run web bundle exec rake db:create
docker-compose up -d
```
