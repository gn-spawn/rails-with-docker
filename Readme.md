# railsをDockerでぶっ立てる

## 準備
dockerデーモンを立てておく

## docker-compose runでrailsアプリケーションを立ち上げる

`docker-compose run web rails new . --api --force --database=postgresql`
--apiオプション付けたほうが速いよ

## ビルドする
`docker-compose build`

## データベースに接続(の設定)
config/database.ymlを以下に編集

```
development: &default
  adapter: postgresql
  encoding: unicode
  database: myapp_development
  pool: 5
  username: postgres
  password:
  host: db

test:
  <<: *default
  database: myapp_test
```

## データベースを作る
`docker-compose run web rake db:create`

## 起動
`docker-compose up`
                  


