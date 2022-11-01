---
layout: post
title: "Object에 특정 항목 삭제하기 (+destructuring)"
categories: TIL JavsScript
---

# 문제

- key a는 1, key b는 2, key c는 3...
- 이렇게 많은 숫자가 연속적으로 커지는 객체가 있다고 생각해보자
- 여기에서 key a, b 부분을 빼고 나머지 값만 있는 객체를 새로 하나 만들고 싶다
- 그럼 어떻게 하면 좋을까?
- 라는 문제에 답변을 못해서 정리...


## 먼저 mdn에서 살펴보기

- `delete`라는 연산자가 있다고 한다.

```
    const obj = { a: 1, b: 2 };
    
    delete obj.a;

    // obj = { b : 2 };
```

- 이렇게 하면 간단하게 지워지기는 하는데...
- strict mode로 들어가면 syntax error가 발생한다.

## 다른 방법

- 디스트럭처링으로 새로운 object를 변수에 삽입해 주면 된다.

```
    const obj = { a: 1, b: 2, c: 3, d: 4 };
    const {a, b, ...obj2} = obj;
    
    return obj2;
    //return value is {c: 3, d: 4}

```

- 위 예시에서 변수 a의 값을 확인하면 1이 나온다.
- 그리고, 객체에서 a, b를 디스트럭처링해서 값을 넣어 주었기 때문에 스프레드 연산자로 객체를 출력해주면 a, b를 제외한 나머지 값이 obj2에 남게 된다.
- 그래서 a, b를 제외한 나머지 key와 value들을 출력할 수 있다.

# Destructuring (비구조화, 구조 파괴)

- 객체나 배열의 구조를 파괴하여 변수에 할당하는 것을 의미한다.
- 가끔 코딩할 때 Object의 값을 쉽게 불러오기 위해서 `const {value} = key;` 형식으로 사용하는 것이 이에 해당한다.

- 배열의 경우

```
const arr = [1, 2, 3];

const [one, two] = arr;

return one;
// return value is 1
```

- 객체의 경우

```
const obj = {name: 'bin', age: 20};

const {name}

```


## Reference
- [mdn web docs, 구조 분해 할당, 2022.10.14](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
- [mdn web docs, delete 연산자, 2022.8.13](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/delete)
