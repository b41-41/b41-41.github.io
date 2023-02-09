---
layout: post
title: "콘솔창 예쁘게 꾸미기"
categories: TIL JavaScript
---

# 들어가기

- 프론트엔드를 공부하면서 인터렉티브한 UI에 관심이 많았고, 여러 사람들의 포트폴리오에서 이런 것들을 보며 즐거움을 느꼈다.
- 가끔은 어떻게 만들었는지 궁금할 때도 있다.
- 그럴 때 하는 것이 `opt + shift + i`!
- 그런데 가끔은 정말 특이한 콘솔을 볼 때가 있다.
  ![티스토리 콘솔창](../../assets/img/post/20220316/story.png)
  ![티스토리 콘솔창](../../assets/img/post/20220316/port.png)
- 위 처럼 이쁜 콘솔 로그를 사용해 들어오는 개발자에게 인사를 남길 수 있다.
- 어떻게 하는 지 궁금해서 방법을 찾아 보았다.

# 콘솔에 CSS 적용하기

- `console.log()`를 사용해서 CSS를 출력한다.

- `console.log()`의 첫 번째 매개 변수에 `%c`를 쓰면 두 번째 매개 변수에 스타일을 지정할 수 있다.

- 아래 처럼 사용하면 된다.
- `console.log('%c 반갑습니다!', `color:white; font-size: 20px; background-color: #C08571`)`

- 그럼 이렇게 출력된다.

![예시](../../assets/img/post/20220316/example.png)

# Reference

- https://jungdev.tistory.com/3
