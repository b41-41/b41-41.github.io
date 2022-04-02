---
layout: post
title: "TypeScript에서 인터페이스(Interface)와 타입 앨리어스(Type Aliases)의 차이"
categories: TIL TypeScript
---

# 시작하기

- TypeScript를 사용하기 시작하면서 객체의 타입 선언을 위해 Interface와 Type을 사용하고 있다.
- 그런데 막상 두 개는 무슨 차이가 있는 지 잘 모르면서 사용하고 있는 것 같았다.
- 무슨 차이가 있을까? [공식문서](https://www.typescriptlang.org/docs/handbook/advanced-types.html#interfaces-vs-type-aliases)에서 살펴 보았다.

# 첫 번째

- 확장 방식이 다르다.
- 인터페이스는 `extends 블라블라` 형태로 확장하는 반면
- 타입 앨리어스는 `&`를 사용해서 확장한다

```
//인터페이스의 경우
interface Animal {
  name: string
}

interface Bear extends Animal {
  honey: boolean
}

//타입 앨리어스의 경우
type Animal = {
  name: string
}

type Bear = Animal & {
  honey: Boolean
}
```

# 두 번째

- '새 속성을 추가하기 위해 다시 선언할 수 있는가?'에 대한 차이
- 인터페이스는 여러 번 선언해서 새 필드를 추가할 수 있지만 타입 앨리어스는 불가능

```
//인터페이스의 경우
interface Window {
  title: string
}

interface Window { //괜찮음!
  ts: string
}

//타입 앨리어스의 경우
type Window = {
  title: string
}

type Window = { //ERROR!!!
  ts: import("typescript")
}
```

# 세 번째

- 공식문서에서는 튜플, 유니언 타입을 사용하는 경우 '타입 앨리어스' 를 사용하는 것이 좋다고 밝히고 있다.

## 튜플이란?

- 자바스크립트에서는 없는 타입으로 '길이와 타입이 고정된 배열을 의미'
- 아이디, 비밀번호 같은 데이터를 배열로 만들 때 정해진 형태로만 삽입할 수 있도록 사용할 수 있음.

```
let user1: [number, string, string];
user1 = [1, 'test@b41.kr', '123456789'];
```

# Reference

- https://www.typescriptlang.org/docs/handbook/advanced-types.html#interfaces-vs-type-aliases
