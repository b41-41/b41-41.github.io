---
layout: post
title: "Compound Component Design Pattern 외 기타 용어"
categories: TIL CS React DesignPattern PostCSS JavaScript
---

## Compound Component Design Pattern

- 복합 컴포넌트의 디자인 패턴
- Prop의 드릴을 피하고 상태 공유를 암시적으로 표시
- 복합 컴포넌트 : 상위 구성 요소와 하위 구성 요소가 통신할 수 있는 컴포넌트
- React에서 children을 사용하면 컴포넌트를 `<> 사이 </>` 열고 닫을 때 사이에 있는 내용이 해당 컴포넌트에 삽입된 부분에 들어가도록 구현할 수 있는데, 이것을 이야기 함.
- Reference : [https://betterprogramming.pub/compound-component-design-pattern-in-react-34b50e32dea0](https://betterprogramming.pub/compound-component-design-pattern-in-react-34b50e32dea0)

## CLI

- Command Line Interface
- 터미널처럼 커맨드를 입력해서 컴퓨터와 소통하는 방식
- 항상 같이 나오는 녀석으로는 `GUI(Grapic User Inteface)`가 있음(윈도우, 맥 같은거)

## PostCSS

- 이건 스타일 전처리기가 아님
- JavaScript 도구
- Style Lint, TailwindCSS 등에서 사용하는데
- 사용자 정의 플러그인도 만들 수 있는 장점이 있음.
- Reference : [https://www.julian.io/articles/postcss.html](https://www.julian.io/articles/postcss.html)

## HTML에서 Canvas API

- admin, dashboard에서 그래프를 그린 곳에서 처음 봄
- 주로 그래픽, 애니메이션, 실시간 비디오 등의 처리를 위해 사용된다고 함.
- 사용하기 위해서 추가적 학습이 필요
- [mdn web docs의 캔버스 듀토리얼 (링크)](https://developer.mozilla.org/ko/docs/Web/API/Canvas_API/Tutorial)

## 보일러 플레이트

- 빠르게 개발을 시작할 수 있도록 미리 세팅해 놓은 것.
- 사전으로는 변경 없이 계속하여 재사용할 수 있는 저작품을 말한다고 한다. [(출처 : 텀즈)](http://www.terms.co.kr/boilerplate.htm)
- antd admin으로 검색했더니 바로 프로젝트가 나왔는데 이것도 보일러 플레이트라 할 수 있을 것 같음. [(링크)](https://github.com/zuiidea/antd-admin)

## ~ (틸트) from JavaScript

- 자바스크립트에 이런게 있다고 들어서 깜짝 놀람.
- 반대로 바꿔주는 역할을 하는 것 같은데 내용 공부는 추후 `you don't know javascript` 책을 읽으면서 공부할 것.
