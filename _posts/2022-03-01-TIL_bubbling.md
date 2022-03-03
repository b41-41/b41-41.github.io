---
layout: post
title: "Bubbling 방지하기와 주의점, Jest Unit Test"
categories: TIL JavaScript TDD Jest
---

# Bubbling 방지하기와 주의점

- onClick 등의 이벤트에선 `event.preventDefault()`를 사용
- 하지만 지난 번에 정리한 것처럼 부모 엘리먼트에서 자식 엘리먼트로 상속되는 이벤트의 경우 `event.stopPropagation()`를 사용 (a태그 등)
- 하지만 `event.stopPropagation()`의 경우 위쪽으로 일어나는 버블링만 막아주고, 다른 핸들러들이 동작하는 것은 막지 못함.
- 버블링 중지와 동시에 다른 핸들러 동작까지 막으려면 `event.stopImmediatePropagation()`를 사용.
- `event.stopPropagation()`을 사용해서 생길 수 있는 문제점
  - 중첩 메뉴를 만들었을 때 상위 메뉴 클릭 이벤트 핸들러가 동작하지 않도록 `stopPropagation`을 사용함.
  - 그런데 나중에 페이지 행동을 분석하기 위해 window 전역에 클릭 이벤트를 감지하도록 함.
  - 하지만 `stopPropagation` 때문에 버블링을 막아놓은 영역은 분석이 작동하지 않게 됨
  - 이런 영역을 `Dead Zone`이라고 함.

참고 : https://ko.javascript.info/bubbling-and-capturing

# Jest Unit Test

## 사용하기

### 설치

```
npm install --save-dev jest
```

### 계산을 위한 sum.js라는 파일 생성

```JavaScrip처
function sum(a, b) {
    return a + b
}
module.exports = sum;
```

### 테스트 파일 작성

```JavaScript
//sum.test.js
const sum = require('./sum');
test('1 + 2는 3과 같다', () => {
    expect(sum(1, 2)).toBe(3);
})
```

- `package.json`에 추가

```JavaScript
{
    "scripts": {
        "test": "jest"
    }
}
```

- `npm test`을 실행해서 통과하면 PASS라고 나옴

출처 : https://jestjs.io
