---
layout: post
title: "이미 올려버린 커밋 작성자 바꾸기, safari에서 `overflow:hidden`이 적용되지 않는 현상..."
categories: TIL Git CSS
---

# 이미 올려버린 커밋 작성자 바꾸기

## 들어가기

- 집 컴퓨터로도, 회사 컴퓨터로도 열심히 랜딩 페이지 작업을 했다.
- 이제 모든 작업이 끝나고 메인 브랜치에 merge하려고 하는데
- git history에... 내 개인 계정이 올라와 있는 것이다...(헉)
- 그래서 열심히 검색해서 커밋 작성자(author)를 바꾸고 메인 브랜치에 성공적으로 머지했다.

## 방법

- 먼저 원하는 commit보다 한 단계 이전의 commit을 찾는다.
- 해당 commit의 해쉬번호를 복사한다. (Github에서 찾아서 복사했다.)
- git rebase -i를 사용!

```
$git rebase -i @#$@#$@#$@#$@#$@#$@#해쉬넘버@#$@#$@#$@#$
```

- VIM 편집창이 나오면 원하는 commit의 해쉬 번호 앞쪽에 `pick`이라고 적혀 있는 부분을 `e`로 바꾼 후
- 저장, 닫는다 `esc -> :wq`
- 작성자를 변경한다. `git commit --amend --author"유저아이디 <이메일>"`

```
$git commit --amend --author"b41-41 <b41-41@41.kr>"
```

- 다시 VIM 편집창이 나오는데 변경 내용이 맞으면 저장, 닫는다 `esc -> :wq`
- rebase를 종료!

```
$git rebase --continue
```

- push (기존 커밋을 바꾸기 때문에 force 옵션을 줬다.)

```
$git push blabla -f 
```


## Reference

- [otrodevym, commit 한 author 변경(작성자 변경) 방법, 2021.05.22](https://otrodevym.tistory.com/m/entry/git-commit-%ED%95%9C-author-%EB%B3%80%EA%B2%BD%EC%9E%91%EC%84%B1%EC%9E%90-%EB%B3%80%EA%B2%BD-%EB%B0%A9%EB%B2%95)


# safari에서 `overflow:hidden`이 적용되지 않는 현상...

## 들어가기

- 랜딩 페이지를 열심히 만들었다.
- 크롬에서 잘 작동되는 것을 확인 후, safari로 열어보는데
- 부모 태그 안에 있는 녀석이 자식 태그가 밖으로 튀어나오는 현상이 있었다.
- `overflow:hidden`이 적용되어 있는데 왜...?

## 문제는...

- [webkit의 버그라는 블로그 글](https://www.sungikchoi.com/blog/safari-overflow-border-radius/)을 보았다.
- 부모 태그에 border-radius가 적용되었을 때 발생하는 것 같다.
- 해결 방법은 relative가 적용되어 있는 부모 태그에 `z-index: 0`을 주어서 간단하게 해결이 되었다....


## Reference

- [Sungik Choi, 사파리 overflow:hidden + border-radius 관련 이슈 해결법, 2020.12.18](https://www.sungikchoi.com/blog/safari-overflow-border-radius/)