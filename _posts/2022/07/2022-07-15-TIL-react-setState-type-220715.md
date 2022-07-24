---
layout: post
title: "[TypeScript] React SetState Prop으로 넘길 때 Type 정의하기"
categories: TIL React TypeScript
---

## 들어가기

- 처음으로 React에서 TypeScript를 사용할 때 많이 당황했었다.
- 그 이유는 부모 컴포넌트에서 자식 컴포넌트로 prop을 넘겨주는 일 때문이었다.
- JavaScript에서는 함수, 변수 상관없이 그냥 넘겨주면 됐었다.
- 하지만 TypeScript는 모든 타입을 다 넘겨 주어야 했다.
- 그 중에서 가장 난감했던 것이 `useState` 훅을 사용했을 때 `setState`를 넘기는 일이었다.
- `setState`를 prop으로 넘기는 방법을 알지 못해서 아래와 같이 함수를 만들어서 자식 컴포넌트로 넘겼다.
    ```
    const changeState = (changeValue: string): void => {
        setStateValue(changeValue);
    }
    ```
- 위와 같은 함수를 부모 컴포넌트에 만들고 자식 컴포넌트로 해당 함수를 넘기는 방법이다.
- 하지만.. 간단하게 setState를 넘기고 타입을 정의할 수 있다.

## setState의 타입 정의

- useState 훅을 아래와 같이 사용했다고 한다면
```
const [stateValue, setStateValue] = useState<string>();
```

- 자식 컴포넌트로 넘길 때는 아래와 같이 타입을 정해주면 된다.

```
setStateValue: React.Dispatch<React.SetStateAction<string>>;
```

- 전체적으로 다시 보면

```
//부모 컴포넌트
import React, {useState} from 'react';
import ChildrenComponent from './.';

const parentComponent = () => {

    const [stateValue, setStateValue] = useState<string>();

    return (
        <ChildrenComponent setStateValue={setStateValue} />
    )

}
```

```
//자식 컴포넌트
import React, {useState} from 'react';

interface Props {
    setStateValue: React.Dispatch<React.SetStateAction<string>>;
}

const ChildrenComponent = (props: Props) => {
    
    const chagneState = (e) => {
        setStateValue(e.target.value);
    }

    return (
        <div>
            <button onClick={changeState}>click</button>
        </div>
    )
}

```

## Reference

- [Sweet But Psycho, setState로 prop을 넘길 때, 2021.12.23](https://jemerald.tistory.com/127)