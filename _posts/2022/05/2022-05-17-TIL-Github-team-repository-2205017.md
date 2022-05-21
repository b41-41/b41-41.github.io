---
layout: post
title: "Github 개인 저장소를 팀 저장소로 옮기기, Docker로 github repository 관리"
categories: TIL Github Docker
---

## Github 개인 저장소를 팀 저장소로 옮기기

### 들어가기

처음 프로젝트를 시작할 때 샘플이라고 생각해서 개인 레파지토리에 올려놓고 작업을 했는데 정식 프로젝트가 되면서 조직(팀) 저장소로 옮기게 되었다. 그런데 해본 적이 없어서 인터넷에서 찾아보며 팀 저장소로 이동 시켰다.

### 옮기는 방법

1. 개인 레파지토리 페이지로 들어간다.
2. Settings 메뉴로 이동한다.
3. 쭉 아래로 내리면 Danger Zone을 볼 수 있다. 거기에서 Transfer ownership의 Transfer를 누른다.
4. 옮길 계정 아이디나 조직 이름을 입력한다.
5. 아래에 레파지토리 이름을 다시 재입력하고 trasfer this repository 버튼을 클릭한다.
6. 끝!

### 마무리

생각보다 간단했다.
그 이후는 조직에 있는 레파지토리에서 권한을 받은 후에 다시 본인 레파지토리로 fork해서 작업하면 된다.

## Docker에서 Github repository를 관리하기?!

### 들어가기

CTO님께서 도커를 통해서도 각각의 Repository를 의존성 없이 관리할 수 있다는 것을 알려주시고, 직접 보여주셨다.
뭔가 각 프로젝트가 컨테이너마다 나뉘어서 독립적으로 돌아가는 부분이 굉장히 멋있어 보였다.
(사실 도커로 관리하는 진짜 목적은 node.js 버전의 호환성이라던지 Github 계정이 여러 개인 경우 각 프로젝트마다 다른 계정을 설정해 준다던지 하는 부분에서 독립 컨테이너 안에서 실행되기 때문에 한 컴퓨터에서 여러 환경을 관리할 수 있따는 장점이 더 크다.)

그래서 설치!

## 설치 및 실행

1. 먼저 Docker 계정 만들기

   - 요기 [도커허브](https://hub.docker.com/login)에서 계정을 만들 수 있다.
   - [https://hub.docker.com/login](https://hub.docker.com/login)

2. 설치하기

   - 맥과 윈도우, 리눅스 환경 전부 설치 프로그램이 다르다.
   - 나의 경우는 [맥용 Docker Desktop 다운로드](https://docs.docker.com/desktop/mac/install/)
   - 윈도우는 [여기에서 (클릭)](https://docs.docker.com/desktop/windows/install/)
   - 리눅스는 [여기에서 (클릭)](https://docs.docker.com/desktop/linux/install/)

3. 로그인하고 Dev Environments에 들어와서 Create New Environment 클릭

   - [!](../../../assets/img/post/20220517/1.png)

4. Enter the Git Repository에 git Clone용 주소 붙여넣고 컨테이너 생성

   - [!](../../../assets/img/post/20220517/2.png)

5. 생성된 컨테이너에서 OPEN IN VSCODE를 누르면 vscode에서 컨테이너의 프로젝트를 확인할 수 있음.
   - [!](../../../assets/img/post/20220517/3.png)

## 마무리

- 나는 결국 Github 계정 세팅을 못 했는데...
- 나중에 해결한 후에 다시 내용 추가합시다.

## Reference

- [https://velog.io/@hidaehyunlee/Github-%EA%B0%9C%EC%9D%B8-%EC%A0%80%EC%9E%A5%EC%86%8C%EB%A5%BC-%ED%8C%80-%EC%A0%80%EC%9E%A5%EC%86%8C%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%98%EA%B8%B0](https://velog.io/@hidaehyunlee/Github-%EA%B0%9C%EC%9D%B8-%EC%A0%80%EC%9E%A5%EC%86%8C%EB%A5%BC-%ED%8C%80-%EC%A0%80%EC%9E%A5%EC%86%8C%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%98%EA%B8%B0)
- CTO님의 말씀...
- [https://docs.docker.com/desktop/dev-environments/](https://docs.docker.com/desktop/dev-environments/)
