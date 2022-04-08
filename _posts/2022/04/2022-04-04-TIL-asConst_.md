---
layout: post
title: "타입 단언 as(복습), as const, 상수와 리터럴"
categories: TIL TypeScript
---

## 타입 단언 as

- 컴파일러가 추론하는 것이 아닌 내가 타입을 단언하도록 사용
- 지난 번 정리처럼 `<Element>event.target` 형식으로도 사용할 수 있고
- `as`를 사용해서 `event.target as Element`로 사용할 수도 있음.

## 상수(Constant)와 리터럴(Literal)

### 상수(Constant)

- 변하지 않는 변수
- `const`가 그 예

### 리터럴(Literal)

- 데이터 자체를 이야기 함
- 변수에 넣는 변하지 않는 데이터를 이야기 함.
- TypeScript에서는 `String`, `number`, `boolean`이 이에 해당

## as const - 리터럴 타입의 추론 범위를 줄이자

```TypeScript
const greeting1 = 'Hello, World!'; // "Hello, World!"로 추론
let greeting2 = 'Hello, World!';   // string으로 추론
// 출처 : https://velog.io/@logqwerty/Enum-vs-as-const
```

- TypeScript에서는 타입을 지정하지 않아도 JavaScript처럼 타입을 추론한다.
- 위 코드를 보면 `const`를 썼을 때는 `'Hello, World!'`로 타입을 추론했지만
- 아래 코드는 `string`으로 추론했다.
- 그 이유는 let을 썼기 때문에 greeting2의 값은 언제든지 다른 `string`으로 바뀔 수 있기 때문이다
- 이 때 추론 범위를 넓은 범위의 `string`가 아닌 좁은 범위의 `'Hello, World!'`로 추론하도록 `as const`를 사용할 수 있다.

```TypeScript
let greeting2 = 'Hello, world!' as const;
// 출처 : https://velog.io/@logqwerty/Enum-vs-as-const
```

- 위처럼 작성해 줌으로서 let을 사용했지만 type은 `'Hello, World!'`로 좁혀졌다.
- 하지만 이 경우는 그냥 `const greeting1 = 'Hello, World!'; 으로 사용하면 편하다.
- 그럼 `as const`는 필요 없는 것일까?
- Object와 Array의 경우를 생각해 보면 `const`를 사용해도 내부를 변경할 수 있기 때문에 타입이 좁혀지지 않을 것이라고 추측할 수 있다.

```TypeScript
const members = {
    first: '철수', //string
    second: '영희',  //string
}
```

- 이 경우에 `as const`를 사용하면 타입이 `'철수'`와 `'영희'`로 고정된다.

```TypeScript
const members = {
    first: '철수',
    second: '영희',
} as const;
```

## 기타

- https://velog.io/@logqwerty/Enum-vs-as-const
- 위 포스트를 읽으면서 enum과 const enum에 대해서도 다시 한 번 정리해 보면 좋을 것 같다고 생각한다.

## Reference

- [https://velog.io/@dltjdwls100/TIL-Typescript-is%EC%99%80-as-%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90](https://velog.io/@dltjdwls100/TIL-Typescript-is%EC%99%80-as-%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)
- [https://velog.io/@logqwerty/Enum-vs-as-const](https://velog.io/@logqwerty/Enum-vs-as-const)
- [https://velog.io/@youn0097/TypeScript-4-%EB%A6%AC%ED%84%B0%EB%9F%B4-%ED%83%80%EC%9E%85](https://velog.io/@youn0097/TypeScript-4-%EB%A6%AC%ED%84%B0%EB%9F%B4-%ED%83%80%EC%9E%85)
