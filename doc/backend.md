# koa.js and prisma and mysql

## 手順

### koa.js側

```bash
npm init -y
touch server.js
npm i koa koa-router koa-body
npm i -D nodemon
```

### mysql環境
- dockerで立てるため、以下の操作を行う。

```bash
mkdir docker
mkdir db
touch docker-compose.yml db/my.cnf
```

### prisma側

```bash
npm i @prisma/client
npm i -D prisma
npx prisma init
```

- prismaフォルダができる。
- その下に`shcema.prisma`ができるので、テーブル構造を書く。
- 以下、サンプル。
  - `.env`にdatabaseのurlを書く。

```prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "mysql"
  url      = env("DATABASE_URL")
}

model テーブル名 {
  id    Int     @id @default(autoincrement())
  title String
  done  Boolean @default(false)
}
```

- 初期データのため、seed.jsをprisma配下に書く。

- 記述後、`npx prisma migrate dev --name init`でマイグレーション。
  - テーブル作成が行われている。

- 次に`npx prisma db seed`でseedで定義した初期データをデータベースに流し込む。