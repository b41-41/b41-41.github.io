---
layout: post
title: "Nullish Coalescing operator (??) & Falsy"
categories: TIL JavaScript
---

## 들어가기

- 물음표 두 개를 사용하는 Nullish coalescing operator(널 병합 연산자)
- Falsy (거짓같은 값)
- 전자는 모르고 있었고 후자는 단어를 모르고 있었다.
- 정리하자

## Nullish coalescing operator (null 병합 연산자)

- `const check = 0 ?? 7`이라면 result는 '0'이다.
- 왼쪽 연산자(operator)가 `null` or `undefined`일 때만 오른쪽 연산자를 반환한다.
- 아니면 왼쪽 연산자를 반환하는 논리 연산자라고 한다.
- 비슷한 문법으로 `논리 연산자 OR(||)`이 있는데 `||`은 `Falsy`값 기준으로 반환하기 때문에 0, [] 같은 경우에도 왼쪽 연산자를 없는 값으로 간주하여 오른쪽 연산자를 반환하게 된다.

```JavaScript
console.log (0 ?? 7);
//expected output : 0

console.log (0 || 7);
//expected output : 7
```

## Falsy

- JavaScript에서 `boolean`으로 체크했을 때 `false`가 나오는 값을 이야기한다.
- `0`, `-0`, `0n`, `""`, `null`, `undefined`, `Nan (en-US)`이 Falsy에 해당한다.
- 반대 되는 단어는 `Truthy`라고 한다. (`boolean`으로 체크할 때 `true`가 나오는 값)


## Reference
- [mdn web docs, Nullish coalescing operator, 2022.11.1](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing)
- [mdn web docs, 거짓같은 값, 2022.11.26](https://developer.mozilla.org/ko/docs/Glossary/Falsy)
