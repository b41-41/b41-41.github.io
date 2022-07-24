---
layout: post
title: "[Node.js]Event emitter"
categories: TIL Node.js
---

## Event emitter
- 어떤 동작이 실행되었을 때 이벤트를 인식하고 이벤트를 인식했을 때 다른 행위를 실행시키는 것
- 이벤트 리스너라고 생각하면 쉽다.

### 자세하게 다시 정리

- JavaScript를 브라우저에서 사용할 때 DOM 이벤트를 받는 `이벤트 리스너`의 사용 방법은 다음과 같다.

```
const button = document.querySelector("button");

button.addEventListener("click", (event) => {
    console.log(`clicked`);
})
```

- 그런데 DOM 이벤트가 아니고 다른 행위(트리거)를 기반으로 이벤트를 내보내고 응답하도록 할 때 custom event emitter가 필요하다.

```
let n = 0;
const event = new EventEmitter();

event.subscribe("THUNDER_ON_THE_MOUNTAIN", value => (n = value));

event.emit("THUNDER_ON_THE_MOUNTAIN", 18);

// n: 18

event.emit("THUNDER_ON_THE_MOUNTAIN", 5);

// n: 5
```

- 위 예제에서 `THUNDER_ON_THE_MOUNTAIN`이라는 이름의 이벤트를 구독한다. (subscribe)
- 이벤트가 발생할 때마다 `value => (n=value)` 콜백함수가 실행된다.
- 이벤트를 발생시키기 위해 `emit` 을 사용했다.
- `evetn.emit('THUNDER_ON_THE_MOUNTAIN', 18)`은 `THUNDER_ON_THE_MOUNTAIN`이벤트의 값(value)를 `18`로 설정했기 때문에 변수 `let n`의 값도 `18`로 변경되었다.


- 예시는 다음 글을 참고했습니다. [(https://css-tricks.com/understanding-event-emitters/)](https://css-tricks.com/understanding-event-emitters/)

## Reference

- [Node.js, The Node.js Event emitter : https://nodejs.dev/learn/the-nodejs-event-emitter](https://nodejs.dev/learn/the-nodejs-event-emitter)
- [CSS-TRICKS, Understanding Event Emitters, 2019.03.25](https://css-tricks.com/understanding-event-emitters/)