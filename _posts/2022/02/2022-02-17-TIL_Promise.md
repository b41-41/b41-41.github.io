---
layout: post
title: "Next, Atomic 디자인 패턴, 라이브러리 사용"
categories: TIL JavaScript DesignPatten Library
---

# NEXT

- pages에는 component를 import만 (컴포넌트들이 한 눈에 들어올 수 있도록)
- components에 페이지의 모든 컴포넌트를 정리.
- API 호출할 때 SSR, CSR 어디에서 할 지 고민해보고 구현하면 좋음.
- `useSWR` 이미 가져온 것은 캐시에서 응답하고 아니면 새로 가져오는 것인데
    - 이 훅은 전부 Client Side Rednering이기 때문에 SSR으로 구현해야 하는 부분은 안 쓰는 것이 좋음.
- getServerSideProps를 썼을 때 페이지 로딩이 많이 느려짐.
- 그래서 대부분 getStaticProps와 CSR을 조합해서 쓰는 방식을 많이 씀.
- 데이터 호출 메서드는 3개를 사용
    - getStaticProps : api를 호출하고 데이터를 응답 받아서 HTML을 완성하는 정적 생성
    - getStaticPath : 빌드 시점에서 api호출하고 데이터를 응답받아 정적으로 생성
    - getServerSideProps : 페이지 접근 요청이 있을 때마다 서버에서 호출

# Atomic 디자인 패턴

- 디자이너가 폴더 구조에 따라서 Figma에 디자인을 제시할 때 좋다.

# 라이브러리

- 애니메이션에서 고려해야할 부분이 많은데 라이브러리를 사용하면 더 빨리 개발할 수 있다.
- 주니어 때는 라이브러리를 잘 활용하는 것도 실력이다.