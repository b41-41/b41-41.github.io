---
layout: post
title: "Git Flow 모델"
categories: TIL Git GitFlow 
---

# Git
- git tag 0.1
    - 0.1 버전이라고 태그를 달아 놓는 방법
- checkout할 때 b옵션
    - 브랜치 생성과 동시에 체크아웃
- git branch release/0.2 
    - /0.2는 0.2버전을 준비하겠다고 달아 놓음.
- git merge --no-ff release/0.2
    - 커밋 메세지 남김
- 

# Git Flow Model
- 기능 단위로 브랜치를 만들어서 협업 시 프로젝트 관리를 용이하게 함.
- branch 관리
    - master : 출시하는 제품의 브랜치
    - develop : 개발용 브랜치
    - feature branches : 기능 개발용 브랜치들
    - release branhes : 릴리즈를 위한 브랜치
    - hotfixes : 긴급한 수정을 위한 브랜치