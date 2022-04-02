---
layout: post
title: "React 재조정(Reconciliation)과 key, DIFF 알고리즘"
categories: TIL React JavaScript DOM algorithm
---

# 들어가기

- 기본에 충실하자!
- 이전에 작성한 코드를 다시 리팩터링 하는 중 이런 코드를 보았다.

```
array.map( x => {
    return ( x.length < 5 && <div id={x.id}>{x.content}</div> )
})
```

- 위 코드에서 x의 length는 4보다 많았고 당연히 5번째 array의 의 리턴 값은 `undefined`가 되었을 것인데 당시에 별 생각 없이 코드를 사용했던 것 같다.
- 문제는 리엑트에서 key 에러가 난다는 것이다.
- `undefined`된 배열의 값들에 key가 삽입되지 않고 동일한 값이 계속 리턴되고 있었기 때문에 발생하는 오류였다.
- React가 변경된 값에 대해서 어떻게 작동하는 지 살펴보자.

# DIFF 알고리즘 (비교 알고리즘)

- '변경 내용 추적'기능처럼 렌더링 화면에서 변경 부분을 확인해서 그 부분만 변경하는 알고리즘
- React에서 핵심 알고리즘이라고 할 수 있다.

# React 재조정(Reconciliation)

1. 서로 다른 타입의 두 엘리먼트는 서로 다른 트리를 만들어낸다.
2. 개발자가 key prop을 통해, 여러 렌더링 사이에서 어떤 자식 엘리먼트가 변경되지 않아야 할 지 표시해 줄 수 있다.

- [공식 홈페이지 문서](https://ko.reactjs.org/docs/reconciliation.html)에 나와있는 재조정에 대한 내용이다.
- Dffing Algorithm을 통해서 `O(n)` 복잡도의 알고리즘 구현했다고 밝히고 있다.

- React에서 새롭게 렌더링이 일어나는 경우는 다음과 같다.

## 엘리먼트의 타입이 다른 경우

- 루트 엘리먼트가 달라지면 그 트리를 완전히 버리고 새롭게 구축
- 따라서 그 자식 엘리먼트도 전부 다시 구축하게 됨.

```
    <a> <Menu /> </a>
    //에서 아래로 바꾸면 전부 다시 렌더링
    <div> <Menu /> </div>
```

- 즉 Menu 컴포넌트는 사라지고 다시 마운트 될 것임.
- 트리를 버릴 때 DOM 노드도 같이 파괴가 되는데 그 때 `componentWillUnmount()`가 실행됨.
- 새로운 DOM 노드들이 DOM에 삽입될 때 `UNSAFE_componentWillMount()`가 실행되고 이어서 `componentDidMount()`가 실행.

## DOM 엘리먼트 타입이 같은 경우

- 같은 타입의 React Dom 엘리먼트를 비교할 때 동일한 내역은 유지하고 변경된 속성만 갱신

```
<div className="before" title="stuff" />
//하단 엘리먼트의 className만 수정
<div className="after" title="stuff" />
```

## DOM 노드의 자식을 효율적으로 처리하자

- 아래 코드와 같이 자식이 변경되는 경우 React는 전부 다시 렌더링하여 안 좋은 성능을 보인다.

```
<ul>
  <li>Duke</li>
  <li>Villanova</li>
</ul>

//위 코드에서 아래와 같이 자식이 변경되면, 전부 다 다시 렌더링

<ul>
  <li>Connecticut</li>
  <li>Duke</li>
  <li>Villanova</li>
</ul>
```

## 효율적으로 처리하는 방법 'Keys'

- React에서 key는 자식들이 동일한 지 확인하는 이름같은 역할을 함.

```
<ul>
  <li key="2015">Duke</li>
  <li key="2016">Villanova</li>
</ul>

// 아래 코드로 바뀌어도 '2015'라는 이름이 지정되어 있기 때문에 다시 변경하지 않음.

<ul>
  <li key="2014">Connecticut</li>
  <li key="2015">Duke</li>
  <li key="2016">Villanova</li>
</ul>
```

- 이번에는 `key`를 사용해서 이름을 지정했기 때문에 위치가 변경되었어도 변경 작업을 하지 않았음.
- 따라서 더 빠르고 효율적으로 React가 렌더링 함.
- 위에서 정리한 대로 `key`는 `이름`이기 때문에 다음과 같은 규칙을 지켜야 함.
  1. 반드시 변하지 않을 것.
  2. 예상이 가능해야 함 (누군지 예상 가능한 이름)
  3. 유일해야함 (똑같은 이름이 여러개 있으면 안됨)
  4. 랜덤 함수같은 것(Math.random())을 사용하면 key를 쓰는 의미가 없음.
- 많이 하는 실수가 `map` 메서드를 돌리면서 `index`를 `key`값으로 넣어버리는 경우.
- `key`는 변하지 않는 이름이어야 하는데 `index`는 단지 array의 순서를 말하는 유동적인 값이기 때문에 절대 `index`를 `key`로 넣으면 안 됨.

# Reference

- https://ko.reactjs.org/docs/reconciliation.html
- https://meetup.toast.com/posts/134
