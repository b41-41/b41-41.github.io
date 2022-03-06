---
layout: post
title: "Pseudo Element, Iass, Pass, Sass"
categories: TIL HTML CSS 용어
---

# Pseudo Class (가짜 클래스, 의사 클래스, 가상 클래스, 추상 클래스)

- `:` pseudo class
  - hover, checked 등이 해당.
  - 외부 인자와 관련된 경우에도 스타일 적용할 수 있음. (마우스 위치, 콘텐츠 상태 등)
  - https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-classes

# Pseudo Element (가짜 요소, 의사 요소, 가상 요소, 추상 요소)

- `::` pseudo element
  - after, before 등이 해당.
  - 선택한 요소의 일부분에만 스타일을 입힐 수 있음.
  - https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-elements

# Iass, Pass, Sass

## Iass(Infrastructure as a Service)

- 서버, 네트워크 등의 인프라를 빌려주는 서비스
- OS, 미들웨어를 사용자가 직접 설치
- ex) AWS ES2, S3

## Pass(Platform as a Service)

- 앱 설계, 개발, 테스트, 배포, 호스팅 포함 모든 자원을 빌려주는 서비스
- 개발, 운영 환경을 포함한 플렛폼 제공
- 사용자는 어플리케이션, 서비스 개발에 집중할 수 있음.
- ex) MS Azure

## Saas(Software as a Service)

- 클라우드를 통해 소프트웨어를 제공
- 설치, 전환과정 없이 클라우드에 있는 앱, 서비스를 인터넷을 통해 제공받음.
- Google Docs

## 궁금한 점 - 'Amazon Lightsail'이나 'Oracle Cloud'는 Iass일까? Pass일까?

- 서버 뿐만 아니라 OS의 자동 설치, 호스팅, 모든 자원을 빌려주며 개발 및 운영 환경을 위한 소프트웨어까지 제공해 주고 있으므로
- Iass, Pass, Saas를 포괄하고 있는 클라우드 컴퓨팅 플랫폼(Cloud computing platform)이라고 할 수 있다.

# Reference

- https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-classes
- https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-elements
- https://jsj0903.tistory.com/5
- https://iq-faq.com/en/Q%26A/page=e5ec03f0c175fbe8950bb23b1cd1e067
