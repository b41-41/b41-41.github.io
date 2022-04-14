---
layout: post
title: "파일명 컨벤션 Git 대소문자 오류 처리"
categories: TIL Convention
---

## 케이스

- 스네이크 케이스 : main_menu
- 케밥 케이스 : main-menu
- 카멜 케이스: mainMenu

## 카멜 케이스에서 대소문자를 잘못 써서 Git에 올린 후 수정할 때

- git은 파일의 대소문자를 무시하여 대소문자 변경을 인식하지 못함
- 따라서 파일명이 컴포넌트인데 `mainMenu`에서 `MainMenu`로 변경해서 push를 해도 변경 사항이 없다고 나옴.

## 해결 방법

`git mv mainMenu.js MainMenu.js`
로 해결

## 그래서

- 대부분 카멜 케이스를 사용하지만 이런 문제 때문에 '케밥 케이스'나 '스네이크 케이스'를 쓰는 경우도 있다는 것을 알고 있으면 될 것 같음.

## Reference

[https://jeonghwan-kim.github.io/dev/2020/05/18/filename.html](https://jeonghwan-kim.github.io/dev/2020/05/18/filename.html)
