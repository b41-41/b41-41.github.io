---
layout: post
title: 타입 표명, prettier 설정 있는 곳만 적용하기
categories: TIL TypeScript Prettier
---

## 들어가기

- 타입스크립트에서 `as`를 사용하는 경우가 가끔 있었는데 어떻게 부르는 지는 몰랐다. 간단 정리…
- 가끔 prettier 설정이 안 되어 있는 프로젝트에서 나의 vscode prettier 익스텐션 때문에 PR올릴 때 코드 스타일이 달라지는 경우가 있었다.. 이것도 정리..


## 타입 표명

- `as`는 `assertion`이라고 읽음.
- `assertion` 주장이라는 의미
- 책에서는 타입 표명이라고 번역됨


## Prettier 설정 파일 있는 프로젝트만 적용하기

- prettier 설정 페이지에 들어가서 Require Config 설정 켜기


## Reference

- [Typescript Deep Dive (번역 프로젝트), 타입 표명(Type Assertion), 2022.12.7 열람](https://radlohead.gitbook.io/typescript-deep-dive/type-system/type-assertion)
- [TE$$ERACT, Prettier 설정 파일이 있을 때에만 적용하기, 2022.6.19](https://tesseractjh.tistory.com/220)