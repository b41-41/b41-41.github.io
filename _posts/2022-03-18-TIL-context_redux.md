---
layout: post
title: "Redux와 React Context API의 차이"
categories: TIL ContextAPI Redux
---

# 들어가기

- 어떤 회사는 Redux를 사용하고 어떤 회사는 Context API를 사용하는 것을 보면서 두 개는 무슨 차이인지 궁금해졌다.
- 전역 상태를 관리하기 위해서 Redux를 처음으로 배웠었는데, React Context API도 ~~전역 상태를 관리해준다고 한다.~~
- 두 개는 같은 것이 아닌 것 같은데... 무슨 차이일까?

# Redux와 Context API의 차이

- Context API는 React에서 Prop을 전달해 줄 때 자식 컴포넌트에 깊게 들어가는 경우 prop을 전달하지 않아도 모든 레벨에서 상태 값에 접근할 수 있는 방법을 제공한다.
- 즉, Context API는 Props 전달을 간단하게 표현하기 위한 도구이다. (`drio-drilling`을 피하기 위함)
- Context API를 사용하면서 상태를 관리할 때는 `useState`와 `useReducer`라는 Hook을 사용한다.
- `useReducer`를 사용하면 Redux처럼 상태 관리가 가능하다.
- 하지만 Context API나 `useReducer`가 React 안에 종속되어 있기 때문에 React 밖에서 사용하지 못한다는 단점이 있다.
- Redux는 반대로 React에 속해 있지 않기 때문에 React의 밖에서도 사용이 가능하다.
- 또한 상태를 업데이트할 때 이전 상태 값을 받고 업데이트하기 때문에 관리도구로 상태 추적이 가능하다. (미들웨어 사용을 통한 Redux Devtools 이용)
- 그리고 Redux는 여러 미들웨어를 사용해서 비동기 데이터 처리나 다른 기능들을 추가할 수 있다.

# 상태 관리의 조건

- 초기 값을 저장
- 현재 값을 읽음
- 값 업데이트가 가능

- Context API는 `useState`와 `useReducer`를 같이 사용했을 때 상태 관리라고 할 수 있다.
- 위 조건에 따라 Redux, Mobx, Zustand 등은 상태 관리라고 할 수 있음.

# Reference

- https://ko.reactjs.org/docs/context.html
- https://ko.redux.js.org/introduction/getting-started
- https://olaf-go.medium.com/context-api-vs-redux-e8a53df99b8
