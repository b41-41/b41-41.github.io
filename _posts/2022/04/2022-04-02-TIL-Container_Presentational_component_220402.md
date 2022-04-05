---
layout: post
title: "Container & Presentational Component Pattern"
categories: TIL DesignPattern
---

## Container & Presentational Component Pattern

### 의미

- 데이터 처리와 출력을 분리하는 패턴

### Container Component

- Container Component에서는 로직 처리만 담당

### Presentaional Component

- Presentational Component에서는 보여지는 부분만 담당
  - markup과 styling
  - view에 필요한 state는 가지고 있을 수 있음.

### 장단점

- 기능과 디자인 부분을 분리하였기 때문에 유지보수 시 구분하기 쉽다
- 재사용성을 높일 수 있다
- 일부 컴포넌트에서는 분리하는 것이 더 작업을 복잡하게 할 수 있다

## Reference

- [https://velog.io/@holim0/React-Design-Pattern](https://velog.io/@holim0/React-Design-Pattern)
