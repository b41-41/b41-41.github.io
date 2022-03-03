---
layout: post
title: "instanceof, DOM"
categories: TIL HTML JavaScript TypeScript
---

## 들어가기

```
<M.MUITableRow
      hover={hover}
      {...(stickyTop !== undefined && {
        sx: { position: 'sticky', zIndex: 1, top: stickyTop, ...sx },
      })}
      onClick={event => {
        isHeader ? onClickHandler?.() : onClickHandler?.(order.orderId);
        modalHandler?.(order.id);
        if (event.target instanceof HTMLElement) {
          console.log(event.target.nodeName);
        }
        // console.log((event.target as Element).nodeName);
      }}
    >
```

이벤트 클릭 target을 받아와서 클릭하는 element에 따라 다른 handler를 지정하고자 event.target을 사용했는데 여기에 타입이 선언되지 않았다는 에러가 계속 나왔다.

구글 검색한 결과 `instanceof HTMLElement`을 넣으면 타입 에러가 발생하지 않는 다는 것이었는데 <b>왜 그렇게 되는 지</b> 궁금해서 `instanceof`에 대해서 그리고 `DOM`구조에 대해서 찾아봤다.

## 프로토타입(Prototype)

- 프로토타입은 객체 간 상속을 구현하기 위해 사용

## instanceof 연산자

- 개체가 특정 클래스의 인스턴스인지 boolean값으로 반환하는 비교 연산자

```
객체 instanceof 생성자 함수
```

- 우측에 생성자 함수의 prototype에 바인딩된 객체가 좌측 객체의 프로토타입 체인 상에 존재하면 true로 평가됨.

```
if (event.target instanceof HTMLElement) {
          console.log(event.target.nodeName);
        }
```

- 따라서 HTMLElement 노드 안에 event.target이 있었기 때문에 true가 되어서 사용 가능하게 됨.

## 타입 단언 as

- 지금 이것의 타입은 내가 생각하는 그것이다.
- 컴파일러의 추론과 상관없이 내가 타입을 단언하는 경우에 사용.
- 타입 단언은 `<Element>event.target`의 형식으로도 사용할 수 있음.
  - 하지만 이 상황에서는 tsx의 태그 문법과 비슷해서 헛갈릴 수가 있다.

```
console.log((event.target as Element).nodeName);
```

- 사실 타입 문제 해결 방법에서 `as`를 사용한 방법이 가장 처음으로 나와서 사용했는데 알고 보니 내가 타입 단언하는 경우에 사용하는 것이기 때문에 위 코드에서는 조금 위험하다고 생각

## DOM

![node의 종류](/assets/img/post/20220301/node.png)
출처 : https://ko.javascript.info/basic-dom-node-properties

- 위 크림으로 관계를 간단하게 설명할 수 있음.
- 가장 상위에 `EventTarget`이 있음.
- `EventTarget`과 `Node`는 '추상(abstract)' 클래스이기 때문에 객체가 실제로 만들어지지 않음.
  - (그래서 위 코드에서 `as Node`라고 했을 때는 에러가 났었음.)
- `Element`는 DOM요소를 위한 베이스 클래스

  - `QuerySelector`같은 탐색을 도와주는 프로퍼티나 메서드를 기반으로 함.
  - `SVGElement`, `HTMLElement`, `XMLElement`의 클래스 베이스 역할도 함.

- `HTMLElement`는 HTML요소의 베이스 역할을 하는 클래스
- 여기에서 언급한 것 이외에도 많은 클래스들이 있음.

```
alert( document.body instanceof HTMLBodyElement ); // true
alert( document.body instanceof HTMLElement ); // true
alert( document.body instanceof Element ); // true
alert( document.body instanceof Node ); // true
alert( document.body instanceof EventTarget ); // true
```

## Reference

https://radlohead.gitbook.io/typescript-deep-dive/type-system/type-assertion

https://velog.io/@dltjdwls100/TIL-Typescript-is와-as-의-차이점

https://ko.javascript.info/basic-dom-node-properties
