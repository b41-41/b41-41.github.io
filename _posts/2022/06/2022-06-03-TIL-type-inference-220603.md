---
layout: post
title: "[고민] 타입스크립트에서 타입이 정확한 경우 지정하지 않는 것이 맞는가?"
categories: TIL TypeScript
---


## 들어가기

- 타입스크립트로 프로젝트를 진행하는 중 의문이 생겼다.

```
const LOGIN_ID = 'login id';
const array = ['abc', 'bbc', 'ccc'];
```

- 위와 같은 코드의 경우 `LOGIN_ID`는 한 눈에 타입 판단이 가능하고 TypeScript도 자동 타입 추론(Type Inference)으로 `string`이라고 판단할 것이다.
- 과연 이 경우에도 타입을 지정해야 하는가?라는 의문이 들었다.

## 모든 타입을 선언했을 때 장점과 단점
- 간단한 코드라도 타입을 선언했을 때
- 장점
  - 코드를 읽으면서 정확한 타입을 볼 수 있다.
    - 예를 들면
    ```
    let StudentCount = '1';
    ```
    - 위와 같은 코드에서 보통이라면 number타입을 지정해서 사용하겠지만 특정 API가 `string`으로만 값을 받는다고 하여 타입을 `string`으로 지정해주었다.
    - 이 경우 스쳐 지나가다가 잘못보아 `number`로 착각할 수 있다.
    - 타입 추론에 의해서 `number`로 썼을 때 오류는 발생할 수도 있다.
    - 하지만 `let StudentCount: string = '1';` 이라고 쓰는 게 조금 더 명확하다.
  - 우리의 예상보다 더 정확한 타입으로 추론되는 것을 막을 수 있다.
    ```
    const 1: string = 'x'; // 타입은 string
    const 2 = 'y'; // 타입은 'y'
    ```
- 단점
  - 타입이 정확한데 추가적으로 타입을 전부 작성해야 하니 코드가 길어진다.
  ```
  const x: number = 15;
  const x = 15;
  ```
  - 

## 따라서...

- 정말로 변할 일이 없는 정확한 경우에 타입을 선언하지 않고,
- 그렇지 않은 경우에는 기본적으로 모두 타입을 선언하는 것이 좋을 것 같다.

## 하지만 궁금한 점...

- React에서 타입스크립트를 사용할 때 `tsx` 컴포넌트의 타입 선언을 해야 하는 지 의문이다.
```
//Counter.tsx

import {React, ReactElement} from 'react';

const Counter = ():ReactElement => {

return (
    <div>
    Counter
    </div>
)
};

export default Counter;
```
- 위와 같은 파일이 있다고 할 때
- 파일 확장자는 `tsx` 즉, 파일을 열 때부터 이 파일에는 `tsx`가 들어간다는 것을 알고 있고 안에 들어가는 함수는 당연히 `ReactElement`를 리턴한다는 것을 알고 있을 것인데
- 굳이 `():ReactElement`를 선언해 주어야 할까?

- 개인적인 생각으로는 해당 파일 안에 함수가 여러개가 존재한다면 `ReactElement`를 리턴한다고 타입을 지정해 주어야 하고,
- 아니라면 쓰지 않아도 될 것 같다는 생각이다.

```
//Counters.tsx

import {React, ReactElement} from 'react';

export const AddCounterValue = (value: number, plus: nubmer): number => (value + plus);

const Counter = ():ReactElement => {

return (
    <div>
    Counter
    </div>
)
};

export default Counter;

```

- 위처럼 한 파일 안에 두 가지 함수가 있다고 하면 함수의 성격을 구분하기 위해서 리턴 값의 타입을 지정해줘도 될 것 같다는 생각은 있다.
- (하지만 위 처럼 코드를 작성하는 경우는 없을 것 같다.)

## 그 외 복습
- 위의 고민들은 타입이 확실할 때의 타입 선언에 관한 고민이고, 확실하지 않은 경우는 무조건 선언해야 한다.
- [이전 글(TypeScript Narrowing, TIL, 220226)](https://b41-41.github.io/posts/TIL_repeat_26/)
  


## Reference

- [오웬의 개발 이야기, [이펙티브 타입스크립트] 3장 타입 추론, 2022.03.07, https://devowen.com/440#%EC%--%--%EC%-D%B-%ED%--%-C%-----%--%EC%B-%--%EB%A-%A-%--%EA%B-%--%EB%-A%A-%ED%--%-C%--%ED%--%--%EC%-E%--%EC%-D%--%--%EC%--%AC%EC%-A%A-%ED%--%B-%--%EC%-E%A-%ED%--%A-%ED%--%-C%--%EC%BD%--%EB%--%-C%--%EB%B-%A-%EC%A-%--%ED%--%--%EA%B-%B-](https://devowen.com/440#%EC%--%--%EC%-D%B-%ED%--%-C%-----%--%EC%B-%--%EB%A-%A-%--%EA%B-%--%EB%-A%A-%ED%--%-C%--%ED%--%--%EC%-E%--%EC%-D%--%--%EC%--%AC%EC%-A%A-%ED%--%B-%--%EC%-E%A-%ED%--%A-%ED%--%-C%--%EC%BD%--%EB%--%-C%--%EB%B-%A-%EC%A-%--%ED%--%--%EA%B-%B-)