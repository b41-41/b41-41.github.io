---
layout: post
title: "React Event Handler의 이름 짓기, day.js, [TypeScript] prop 타입 정의하기"
categories: TIL React
---

## React에서 Event Handler의 이름 짓기

- 정확한 규칙이 있는 것은 아님
- 하지만 대부분 개발자들이 많이 사용하는 이름은 있음
- [https://blog.sonim1.com/220](https://blog.sonim1.com/220)
- [https://jaketrent.com/post/naming-event-handlers-react](https://jaketrent.com/post/naming-event-handlers-react)
- 위 블로그에서 정리된 내용을 보면 prop에는 `on##`
- 함수의 이름에는 `handle##`로 접두사를 붙여서 사용되는 것 같음
- 또한 `handleClick` 같은 형식으로 만들어버리면 `onClick`과 겹치기 때문에 다른 단어를 사용하는 것이 좋음.
  - (오늘 useState를 쓰면서 이름이 `setTimeout`이 되버렸는데 보자마자 다른 `setTimeout`과 겹친다는 걸 깨닫고 이름을 바꾸었다.)

## day.js

- JavaScript 날짜 라이브러리
- 20kb도 안되는 가벼운 라이브러리 (사이트에서 2kB라고 써 있음)
- 시간을 조금 더 쉽게 계산할 수 있도록 해 줌.
- 불러온 다음 `dayjs(new Date).format()`
- 위 같은 형식으로 dayjs안에 매개변수로 `date` 타입을 넣어주면 잘 작동한다.
- 'date'타입이 아니더라도 `"2022-02-11"` 처럼 `string` 타입을 넣어줘도 돼서 편함
- [공식사이트 링크](https://day.js.org/)

## TypeScript에서 prop의 타입을 정의할 때 (React, Next에서...)

- 부모 컴포넌트에서 자식 컴포넌트로 prop을 넘겨줄 때 TypeScript에서는 타입을 정의해 줘야 한다.
- 타입을 하나하나 지정해줘도 되고, [보통은 Type Aliases와 Inteface를 사용한다.](https://b41-41.github.io/posts/TIL_interface_type/)
- props을 넘기고 여기에 모든 prop의 type을 정해주면 더 짧은 코드로도 사용할 수 있다.

```TypeScript

import {ReactElement} from 'react';

type Props {
    abc : string;
    bbc : 'abc' | 'bbc';
    ccc : number;
    ddd : () => void;
}

const Component = (props: Props): ReactElement => {
    return (<div>{props.bbc}</div>);
}

```

- 위 코드처럼 작성하면 prop을 모두 쓰지 않아도 된다.
- 다만 사용할 때마다 `props.####` 처럼 props를 무조건 붙여야 해서 귀찮을 수도 있다.
- 다른 방법으로는 아래와 같이 쓰는 방법도 있다.

```TypeScript
import {FC} from 'react';

type ComponentProps {
    abc : string;
    bbc : 'abc' | 'bbc';
    ccc : number;
    ddd : () => void;
}

const Component: FC<ComponentProps> = (abc, bbc, ccc, ddd): ReactElement => {
    return (<div>{abc}</div>)
}

```

- react의 FC를 컴포넌트 자체에 타입으로 지정해 줄 떄 제네릭에 타입을 지정해줄 수 있다.
- 이렇게 쓰면 처음에 prop들을 일일히 써 주어야 하지만 나중에 사용할 때는 바로 prop을 쓰기만 하면 되니까 편하다.
- 위 방법과 아래 방법 중에 뭐가 더 좋다고 말하기는 어렵기 때문에 잘 생각해보고 편한 방법을 쓰는 것이 좋을 것임.
- 그런데 내가 위의 방법을 사용하는 이유는 Visual Studio Code의 `react snippet` 익스텐션에서 `tsrafce`라는 명령어를 치면 위의 방식으로 자동 입력되어 있다.
- 그래서 위 방법을 이용.

## Reference

- [https://blog.sonim1.com/220](https://blog.sonim1.com/220)
- [https://jaketrent.com/post/naming-event-handlers-react](https://jaketrent.com/post/naming-event-handlers-react)
- [https://day.js.org/](https://day.js.org/)
