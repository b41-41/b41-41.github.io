---
layout: post
title: "CORS, 브라우저 렌더링, REST란?"
categories: TIL Git Web Css CS
---

#CORS (Cross Origin Resource Sharing)
A 사이트에서 B사이트의 API로 정보를 요청할 때 리소스에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 것을 Cross Origin Resource Sharing, CORS라고 함.
- 프론트엔드 : 접근 방법, 도메인, 포트가 담겨 있는 Origin이라는 Header를 추가해서 요청을 보냄
- 백엔드 : 답장에 Access-Control-Allow-Origin 정보를 실어서 보냄. (저 안에는 프론트에서 요청하는 도메인이 포함되어 있어야 함.)

#REST
- Representational State Transfer
- 리소스(자원)를 이름으로 구분하여 자원의 정보를 주고 받는 모든 것을 의미함.
- HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)를 명시하고, HTTP Method(POST, GET, PUT, DELETE, (PATCH))를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것.
- GET: READ / POST: CREATE / PUT: UPDATE (정보 전체) / PATCH: UPDATE(정보 일부) / DELETE: DELETE
- 즉 HTTP Method를 통해 리소스를 처리하도록 설계된 구조를 말함.

- 각 요청이 어떤 동작이나 정보를 위한 것인지 요청 모습 자체로 추론 가능
- URI : 주소 뒤에 있는 ?id=1 ← 이런 정보
- CRUD : Create, Read, Update, Delete + HEAD: header 정보 조회
- 이것은 형식일 뿐임.

#브라우저 렌더링 과정
URL 입력 → 브라우저가 서버에게 요청/응답 → 로딩 → HTML태그를 DOM요소로 변환 → CSS를 CSSOM요소로 변환 → RenderTree 생성 → 각 요소의 크기 계산 → 브라우저에 출력(painting)
<img width="683" alt="렌더링 과정" src="https://user-images.githubusercontent.com/90027202/155440646-0f8b7068-1b21-47ad-860b-ec952f8778b1.png"