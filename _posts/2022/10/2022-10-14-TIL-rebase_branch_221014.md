---
layout: post
title: "git 브랜치 관리할 때 merge와 rebase의 차이"
categories: TIL Git
---

## 들어가기

- 회사 프로젝트 진행 중 일부 프로젝트에서 협업할 때 `merge`를 쓰지 않고 `rebase`를 사용해서 브랜치를 관리하는 것을 봄.
- 기존 프로젝트를 할 때 `merge`만 사용했으므로 `rebase`를 사용하는 이유에 대해서 궁금해짐.

## merge와 rebase의 차이

- merge는 새로운 커밋의 가지가 분기되어서 열심히 쌓이다가 나중에 merge되는 기록을 갖게 된다.

 커밋 1- - 2 - - - 머지 - - - - 
     - 새로운 가지 - 

- rebase는 모든 커밋들을 한 줄로 바꾼다.

 커밋 1 - rebase했던 내용들 - 커밋2


## rebase로 브랜치를 관리했을 때 장점

- 분기처리된 내용이 없기 때문에 모든 커밋 내용이 한 줄로 표시되고
- 커밋 내용이 직관적으로 잘 보인다.

## rebase로 브랜치를 관리했을 때 장점

- rebase하는 경우 합쳐지는 다른 commit들의 hash값이 변경되어 버리기 때문에 버전관리 측면에서 오히려 안 좋을 수도 있다.
- (기존에 작업했던 내용이 그대로 있는게 아니고 rebase를 통해서 새로운 커밋이 되는 것이다.)

## 마무리

- 각자 장단점이 있으므로 프로젝트, 구성원의 의견에 따라서 맞는 git 브랜치 관리 방법을 사용하면 될 것이다.

- 이 기회에 rebase로 브랜치 관리하는 방법도 봤으니, 잊지 않고 있다가 rebase로 브랜치를 관리하는 방법을 도입하자는 분이 계시면 장단점을 이야기하며 같이 깊은 고민을 한 번 더 나눠봐야 겠다.

## Reference

- [anonymDev, Merge와 Rebase의 차이점, 2019.03.02](https://brunch.co.kr/@anonymdevoo/7)