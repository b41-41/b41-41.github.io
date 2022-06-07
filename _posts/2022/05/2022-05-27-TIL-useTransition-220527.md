---
layout: post
title: "[React 18] useTransition"
categories: TIL React
---

## 컨커런트 UI 패턴

- 화면에 나타나는 변화를 지연시키고 싶은 경우 사용
- 예를 들면 검색 창에서 실시간으로 검색 결과를 표시할 때 검색 결과 로직 처리보다 검색어 입력을 더 우선적으로 보여주게 하는 것.
- 디바운싱 기법을 사용해서 이전에 구현했었음.

## useTransition

```
const [startTransition, isPending] = useTransition({
    timeoutMs: 3000
  });
```

- 위 코드처럼 작성한다면 3초를 기다린다는 이야기 (3000ms)
- `startTransition()`안에 있는 함수는 변화를 기다렸다가 업데이트.
- `startTransition(() => { 내용 })`

- `isPending`은 불리언으로 transition이 완료되었을 때 `true`로 바뀜.

## Reference

- [https://ko.reactjs.org/docs/concurrent-mode-patterns.html](https://ko.reactjs.org/docs/concurrent-mode-patterns.html)
- [https://velog.io/@katanazero86/React-18-%EC%97%90%EC%84%9C-%EB%8B%AC%EB%9D%BC%EC%A7%80%EB%8A%94%EC%A0%90](https://velog.io/@katanazero86/React-18-%EC%97%90%EC%84%9C-%EB%8B%AC%EB%9D%BC%EC%A7%80%EB%8A%94%EC%A0%90)
- [https://medium.com/naver-place-dev/react-18%EC%9D%84-%EC%A4%80%EB%B9%84%ED%95%98%EC%84%B8%EC%9A%94-8603c36ddb25](https://medium.com/naver-place-dev/react-18%EC%9D%84-%EC%A4%80%EB%B9%84%ED%95%98%EC%84%B8%EC%9A%94-8603c36ddb25)
