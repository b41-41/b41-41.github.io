---
layout: post
title: "호출 스택과 이벤트 루프"
categories: TIL JavaScript
---

# 호출 스택 (Call Stack)

- 함수가 호출되었을 때 호출 스택에 쌓이게 됨.
- 들어오는 순서대로 쌓이고 실행되는 순서는 반대로
- 호출 스택에는 `Anonymous`라는 가상의 전역 컨텍스트가 있음.
- 이 컨텍스트는 무언가가 호출되면 생기고 모든 함수가 실행되면 사라짐.
- 호출 스택의 이런 자료 구조 방식이 `LIFO`라고 함

## LIFO (last in, first out)

- 말 그대로 후입선출
- 나중에 들어온 데이터가 가장 먼저 나가는 자료 구조
- 그래서 `Stack`(쌓다)이라고 함.

# 실행 컨텍스트와 이벤트 루프(Event Loop)

![EventLoop](/assets/img/post/20220310/eventLoop.png)
턴

- +) 테스크 큐에 `setTimeout`과 `Promise then`이 있으면 `then`이 더 빨리 실행 됨.
