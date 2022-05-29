---
layout: post
title: "Github Actions - 자동 배포~!"
categories: TIL CI/CD
---

## 들어가기

- 회사에서 일을 하다보니까 Github Actions을 사용해서 자동 배포를 해주도록 세팅되어 있었다.
- 지금까지 자동 배포는 'netlify', 'heroku' 등의 서비스를 사용했는데 'Github Action'은 조금 다르다.
- 배포 뿐만 아니라 여러가지 workflow를 자동화 시켜주는 도구이기 때문이다.

## Github Actions은?

- workflow를 자동화할 수 있는 도구
- 가격 : Public Repository -> 무료(제한 있음), Private Repository -> 유료(시간당, 용량당)
- '테스트 코드 실행', '배포(CD)', '자동화하고 싶은 스크립트 실행' 등에서 사용할 수 있다.

## 자동배포!

- 백엔드는 Jenkins 등을 사용해서 배포를 하는 것 같은데 프론트엔드는 배포한 파일이 실행되면서 변경되고 하는 것은 없기 때문에, 빌드한 파일이 서버에 올라가서 배포가 된다. (그래서 프론트엔드 프로젝트 배포를 정적 사이트 배포라고 하는 것 같다.)
- 회사에서는 AWS를 사용해서 배포를 하고 있었고, 그 자동화에 Github Actions을 사용하고 있었다.

## 방법

- 프로젝트 루트에 `.github/workflows/deploy.yml`이라는 파일을 만들어서 자동 배포할 [스크립트 파일](https://github.com/week-with-me/next-js-deployment-practice/blob/main/.github/workflows/deploy.yml)을 만든다.
- aws 핵심 정보는 secrets를 사용해서 숨겨둔다.
  - `.env`파일처럼 배포할 때 프로젝트의 설정 부분에서 secrets메뉴에서 환경변수를 설정할 수 있다.
  - 배포를 위한 aws id, key, region은 secrets에 담아둔다.
- 설정한 브랜치에 merge될 때마다 자동으로 스크립트가 실행되며 배포된다.

## Reference

- [https://weekwith.tistory.com/entry/Nextjs-AWS-S3%EB%A5%BC-%ED%86%B5%ED%95%9C-%EC%A0%95%EC%A0%81-%EC%9B%B9-%EC%82%AC%EC%9D%B4%ED%8A%B8-%EB%B0%B0%ED%8F%AC-%EB%B0%8F-GitHub-Actions%E1%84%85%E1%85%B3%E1%86%AF-%E1%84%90%E1%85%A9%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB-CICD](https://weekwith.tistory.com/entry/Nextjs-AWS-S3%EB%A5%BC-%ED%86%B5%ED%95%9C-%EC%A0%95%EC%A0%81-%EC%9B%B9-%EC%82%AC%EC%9D%B4%ED%8A%B8-%EB%B0%B0%ED%8F%AC-%EB%B0%8F-GitHub-Actions%E1%84%85%E1%85%B3%E1%86%AF-%E1%84%90%E1%85%A9%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB-CICD)
