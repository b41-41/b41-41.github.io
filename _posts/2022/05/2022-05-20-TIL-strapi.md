---
layout: post
title: "Strapi 설치 및 Heroku 배포"
categories: TIL Library JavaScript
---

## 들어가기

- 지난 주에 CTO님께서 Strapi라는 걸로 백엔드 개발 없이 API를 사용할 수 있다고 말씀하셨다.
- 다른 부분에 대해서 열심히 진행하다가 API를 슬슬 가져다가 붙여야 하는데 난감했다.
- 일단 백엔드 구현되기 전까지 프론트만으로도 개발을 진행해야 되서 Strapi를 사용하기로 했다.

## 설치에서 실행까지

- strapi 공식 블로그에서 설명한 방법으로 진행했기 때문에 오른쪽 링크를 참조해서 보면 따라하기 좋을 것이다. -> [[링크]](https://strapi.io/blog/deploying-a-strapi-api-on-heroku)
- 아니다 공식문서를 따라하는 게 더 좋을 것 같다. -> [[링크]](https://docs.strapi.io/developer-docs/latest/setup-deployment-guides/deployment/hosting-guides/heroku.html)

- 설치

  ```bash
  $npx create-strapi-app my-project --quickstart
  ```

- 설치가 끝나면 `http://localhost:1337/admin` 페이지에서 API를 세팅할 수 있다.
  (기본으로 User는 잡혀 있다.)

- Setting - Roles - Public에 들어가서 필요한 API에 체크해주면 API 사용 방법이 같이 뜬다.
  (이 부분 블로그를 검색하는데 UI가 현재버전과 조금 달라서 조금 헤맸다.)

## Heroku 배포

- Heroku CLI을 설치하면 조금 더 가이드에 맞게 쉽게 따라할 수 있다.

- 맥에서 설치는 아래와 같다. (brew가 깔려 있어야 한다.)

  ```
  brew tap heroku/brew && brew install heroku
  ```

- 로그인

  ```
  heroku login
  ```

- 프로젝트 폴더에서 `.gitignore` 파일에 아래와 같이 추가

  ```
  package-lock.json
  ```

- Git 준비하기

  ```
  cd my-project
  git init
  git add .
  git commit -m "Initial Commit"
  ```

- Heroku Project 만들기

  ```
  heroku create
  ```

- Heroku Postgres addon 설치

  ```
  heroku addons:create heroku-postgresql:hobby-dev
  ```

- Retrieve database credentials

  ```
  heroku config
  ```

- Set Database variables automatically

  ```
  npm install pg-connection-string --save
  ```

- `./config/env/production/database.js` 파일 만들기

  내용은 아래처럼

  ```JavaScript
  const parse = require('pg-connection-string').parse;
  const config = parse(process.env.DATABASE_URL);

  module.exports = ({ env }) => ({
  connection: {
      client: 'postgres',
      connection: {
      host: config.host,
      port: config.port,
      database: config.database,
      user: config.user,
      password: config.password,
      ssl: {
          rejectUnauthorized: false
      },
      },
      debug: false,
  },
  });

  ```

- env 설정

  ```
  heroku config:set NODE_ENV=production
  ```

- Strapi server config for production 만들기
  `./config/env/production/server.js`파일 만들기
  아래와 같이 따라 쓰면 됨

  ```JavaScript
  module.exports = ({ env }) => ({
  proxy: true,
  url: env('MY_HEROKU_URL'),
  app: {
    keys: env.array('APP_KEYS')
  },
  })
  ```

- 콘솔 창에 아래와 같이 따라 쓰기

```
heroku config:set MY_HEROKU_URL=$(heroku info -s | grep web_url | cut -d= -f2)
heroku config:set APP_KEYS=$(cat .env | grep APP_KEYS | cut -d= -f2-)
heroku config:set API_TOKEN_SALT=$(cat .env | grep API_TOKEN_SALT | cut -d= -f2)
heroku config:set ADMIN_JWT_SECRET=$(cat .env | grep ADMIN_JWT_SECRET | cut -d= -f2)
heroku config:set JWT_SECRET=$(cat .env | grep -w JWT_SECRET | cut -d= -f2)
```

- 맥 리눅스의 경우는 아래도 따라 쓰기

```
heroku config:set APP_KEYS=$(openssl rand -base64 32)
heroku config:set API_TOKEN_SALT=$(openssl rand -base64 32)
heroku config:set ADMIN_JWT_SECRET=$(openssl rand -base64 32)
heroku config:set JWT_SECRET=$(openssl rand -base64 32)
```

- `pg`노드 모듈 설치

```
npm install pg --save
```

- 지금까지 상황 Git 커밋

```
git add .
git commit -m "Update database config"
```

- yarn.lock 파일 업데이트

```
yarn install
```

- yarn.lock 파일 git commit

```
git add yarn.lock
git commit -m "Updated Yarn lockfile"
```

- 배포

```
git push heroku HEAD:main
```

- 배포 페이지 열고 싶으면

```
heroku open
```

## 마치며

- 참고로 배포 이후에는 로그인해서 직접 데이터 추가하는 것이 불가능하다.
- 기본 데이터 설계한 거는 로컬에서 끝내놓은 다음에 배포하면 될 것.

## Reference

- [https://strapi.io/blog/deploying-a-strapi-api-on-heroku](https://strapi.io/blog/deploying-a-strapi-api-on-heroku)
- [https://docs.strapi.io/developer-docs/latest/setup-deployment-guides/deployment/hosting-guides/heroku.html](https://docs.strapi.io/developer-docs/latest/setup-deployment-guides/deployment/hosting-guides/heroku.html)
