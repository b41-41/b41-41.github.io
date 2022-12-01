---
layout: post
title: "Conventional Commit, Variable Name Case (변수명 케이스), Array.isArray()"
categories: TIL JavaScript Git
---

## 들어가기

- 예전에 커밋 컨벤션에 대해서 정리한 적이 있었다.
- 사실 그때 `chore`에 대해서 시스템적인 작업을 할 때 쓴다고 생각을 했다.
- 하지만 `chore`의 뜻은 `잡일`이므로 파일을 삭제하거나, 그 외의 기타 작업할 때 사용한다.
- 느낌으로 알 때와 달랐던 커밋 컨벤션, 사이트에서 다시 봤다. (Conventional Commit)

## Conventional Commit

- [https://www.conventionalcommits.org/](https://www.conventionalcommits.org/)
- 커밋 메시지의 규칙을 간단하게 제공
- 자주 쓰는 부분 정리
    - `feat:` : 기능 개발 (ex: `feat: add a membership registration function`)
    - `chore:` : 잡일 (삭제, 환경변수 변경, 지원 버전 변경 등등...) (ex: `chore: delete unused components`)
    - `docs:` : 본문 없는 커밋 메시지
    - `fix:` : 수정 (ex: `fix: fix bug`)
    - `ci:` : CI/CD (ex: `ci: github action deployment settings`)
    - `style:` : 스타일링, 마크업 (ex: `style: apply moving animation style`)
    - `refector:` : 리팩토링 (코드 정돈) (ex: `refector: code refactoring`))
    - `test`: 테스트 코드 (ex: `Add jest rate utility test code`)
    
## Variable Name Case
- 예전에도 정리한 적이 있지만, 다시 한 번 정리
    - 기본 이름 : my name is b41
    - Camel case : `myNameIsB41`
    - Parscal case : `MyNameIsB41`
    - Snake case : `my_name_is_b41`
    - Title case : `My Name Is B41`
    - Upper case : `MY NAME IS B41`

## Array.isArray()

- isArray의 파라미터로 오는 값이 array가 맞는지 판별
- boolean으로 return

```JavaScript
const arr = [];
const notArr = 'array';

Array.isArray(arr);
//return true

Array.isArray(notArr);
//return false
```


## Reference
- [jawira, https://github.com/jawira/case-converter, 2022.6](https://github.com/jawira/case-converter)
- [Conventional Commits, 2022.4](https://www.conventionalcommits.org/en/v1.0.0/)
- [mdn web docs, Array.isArray() , 2022.11.7](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)
