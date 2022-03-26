---
layout: post
title: "JavaScript에서 소수점을 더했을 때 값이 이상하다? (220318 업데이트)"
categories: TIL JavaScript CS
---

# JavaScript에서 소수점 더하기

- 컴퓨터는 2진법을 사용함.
- `0.1 + 0.3 = 0.30000000004` (?!)
- 컴퓨터의 부동 소수점 계산 문제 발생
- 소수를 2진수로 표현할 때 무한소수가 발생
- 무한수를 유한하게 표현하려다 보니 미세한 값들이 손실, 초과 됨.
- 따라서 계산 오류가 발생
- 원화는 괜찮지만 미국 달러화, 비트코인에서는 소수점 계산 문제가 발생할 수 있음.

# 해결법

1. ~~소수점 숫자의 경우 `*10`을 해서 정수로 바꿔서 계산한 후 다시 실수로 바꾸기

   - ~~`(0.1 * 10 + 0.2 * 10) / 10;`~~

- 2022.03.18 추가!

  - 아니다... \*10을 곱해도 오류가 날 수 있다.

  - 아래 방법을 쓸 것.

1. toFixed() 메서드로 소수점 고정해 주기

   - `(0.1 + 0.2).toFixed(1);`

2. Math객체의 메서드로 소수를 다루기

3. 수학 라이브러리 활용하기

# Reference

- https://www.youtube.com/watch?v=rT8P3s82--4
- https://bigtop.tistory.com/47
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/round
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed
