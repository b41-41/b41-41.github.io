---
layout: post
title: "Thymeleaf, [Ant Design] 카드와 버튼 컴포넌트"
categories: TIL AntDesign Thymeleaf
---

## Thymeleaf

- Java Spring의 View Template Engine
- html태그를 기반으로 View를 담당.

## Ant Design의 Card, Button 컴포넌트

- Ant Design의 [공식 사이트](https://ant.design)는 설명이 아주 잘 나와 있다.

### Card 컴포넌트

- `bodyStyle` prop을 사용하면 카드를 커스터마이징할 수 있다.
- `hoverable` prop을 사용하면 hover 상태일 때 그림자 등의 상태가 변한다.

### Button 컴포넌트

- `type`이라는 prop을 사용해서 모양을 정함 모양은 'primary, default, dashed'가 있음.
- `ghost`를 사용하면 배경이 transparent(투명)으로 바뀜
- `danger`prop을 사용하면 버튼들이 빨간색으로 변함
- Ant Design의 기본 테마 색이 파란색으로 되어 있는데, 기본 primary색을 다른 색으로 바뀌면 버튼들 색도 다 변함
- 따라서 색상 관련 부분은 style로 커스터마이징 하는 것보다 기본 세팅에서 수정해주는 것이 좋음.

## Reference

- [https://ant.design/components/card/#API](https://ant.design/components/card/#API)
- [https://ant.design/components/button/#API](https://ant.design/components/button/#API)
- [https://www.thymeleaf.org/](https://www.thymeleaf.org/)
