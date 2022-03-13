---
layout: post
title: "Zustand - 상태관리 라이브러리"
categories: TIL Zustand
---

# Zusatand란?

![Zustand 홈페이지](/assets/img/post/20220313/zustand.gif)

- redux같은 상태 관리 라이브러리 (홈페이지 캐릭터가 너무 귀여움.)
- store를 쉽게 만들고 한 줄 코드로 불러올 수 있는 정도로 매우 간단

# 사용법

1.  `npm i zustand`

    로 설치

2.  `import create from 'zustand'`

    로 create 불러오기

3.  ```
    const useStore = create(set => ({
        count: 1,
        inc: () => set(state => ({count: state.count + 1}))
    }))

    function Couter() {
        const count = useStore(state => state.count)
        return <h1>{count}</h1>
    }

    function Controls() {
        const inc = useStore(state => state.inc)
        return <button onClick={inc}>+</button>
    }
    ```

- 이렇게 `store`를 하나 만든 다음에 그 안에 실행될 것들을 지정해 주고
- 값을 가져올 때는 `useStore`에서 바로 가져다가 쓰면 됨.

# 장점

- Redux에서 리듀서 만들고, 액션, 디스패치 이런 과정보다 훨씬 심플하고 직관적

# Reference

- https://zustand-demo.pmnd.rs
