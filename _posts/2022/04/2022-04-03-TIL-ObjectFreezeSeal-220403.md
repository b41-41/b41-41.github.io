---
layout: post
title: "Object freeze(), seal()"
categories: TIL JavaScript Object
---

## Object.seal()

- 객체를 밀봉
- 새로운 속성을 추가할 수 없게 됨
- `Object.seal(object1)`의 형식으로 사용
- 하지만 속성의 값은 변경 가능

```JavaScript
const object1 = {
    value1: 32,
    value2: 24,
}

Object.seal(object1);
object1.value1 = 22;
console.log(object1.value1);
// expected output : 22
```

## Object.freeze()

- 객체를 동결
- 더 이상 속성을 변경할 수도 추가할 수도 없게 됨
- `Object.freeze(object1)` 형식으로 사용

## Reference

- [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/seal](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/seal)
- [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze)
