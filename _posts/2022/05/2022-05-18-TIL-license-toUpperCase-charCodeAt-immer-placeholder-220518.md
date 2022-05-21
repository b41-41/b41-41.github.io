---
layout: post
title: "라이센스 선택하기, 아스키 코드로 영문자 쓰기, 옵셔널 체이닝이 뭐였지?, immer, a11y lint, Faker"
categories: TIL Library JavaScript TypeScript License
---

## Github 라이센스 선택하기

### 들어가기

회사에서 프로젝트를 진행하면서 라이브러리를 많이 사용하게 되었다. 별 생각 없이 라이브러리르 사용했었는데 회사에서는 그러면 안 됐다. 라이센스라는게 있기 때문이다. 전에는 자세히 알지 못하고 막 썼는데, 이제 라이센스에 대해서 신경 써야 겠다.

### 이런 라이센스들이 있다.

- BSD : 소스코드 공개 X, 라이센스, 저작권 명시
- GPL : GPL 코드를 사용한 경우 내 프로그램도 GPL이 됨. 프로그램 유료로 사용 가능하지만 소스코드는 무료로 모두 공개해야 함.
- MIT👍 : 라이선스 저작권 명시 필요. 상업적 이용 가능. 제약 조건이 느슨.
  - (따라서 회사에서 프로젝트를 진행할 때 전부 MIT 라이센스의 라이브러리만 사용했다.)

## 아스키 코드로 영문자 쓰기

### 아스키 코드?

- 정보 교환용 부호 체계
- 0과 1을 사용하는 컴퓨터에서는 결국 문자도 숫자로 기억하는 것.
- 문자의 인코딩 방식 중 하나가 아스키 코드
- 여러 프로그래밍 언어에서 사용할 수 있음
- 아스키 코드에서 65~90는 A~Z, 97~122는 a~z는 기본 상식이라고 함.

### [JS] String.prototype.charCodeAt()

- 이 메서드는 string을 아스키 코드로 바꿔 줌.

## [JS] String.prototype.toUpperCase()

- 이 메서드는 string 소문자를 대문자로 바꿔 줌.

## [TS] 옵셔널 체이닝

- 예전에 프로젝트 할 때 엄청 이야기했으면서 뭔지 또 까먹고 있었음.
- 객체 불러올 때 depth를 `.`으로 쓸 수 있는데
- 혹시 그 객체가 아직 덜 불러와져서 Type이 undefined나 null이 나는 경우가 있음.
- 그 때 undefined나 null타입을 추가하는 대신에 그 객체의 value 값을 불러오는 부분에 `?`을 추가하면 됨
- 비동기 코드 작성할 때 상당히 편했었음.

```TypeScript
const abc = { aaa : {bbc : 'ccc'}}

console.log(abc.aaa?.bbc)
```

## 여러가지 유용한 라이브러리

- a11y lint - 장애인 스크린 리더기가 잘 작동할 수 있도록 코드가 작성되어 있는지 확인하는 린터
- immer - 불변성 지키면서 reducer 코드 작성할 때 편한 라이브러리 (추후에 다시 정리)
- Faker - 더미데이터 랜덤으로 만들어주는 라이브러리

## Reference

- [https://flyingsquirrel.medium.com/github-license%EC%9D%98-%EC%A2%85%EB%A5%98%EC%99%80-%EB%82%98%EC%97%90%EA%B2%8C-%EB%A7%9E%EB%8A%94-%EB%9D%BC%EC%9D%B4%EC%84%A0%EC%8A%A4-%EC%84%A0%ED%83%9D%ED%95%98%EA%B8%B0-ae29925e8ff4](https://flyingsquirrel.medium.com/github-license%EC%9D%98-%EC%A2%85%EB%A5%98%EC%99%80-%EB%82%98%EC%97%90%EA%B2%8C-%EB%A7%9E%EB%8A%94-%EB%9D%BC%EC%9D%B4%EC%84%A0%EC%8A%A4-%EC%84%A0%ED%83%9D%ED%95%98%EA%B8%B0-ae29925e8ff4)
- [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt)
- [https://shaeod.tistory.com/228](https://shaeod.tistory.com/228)
- [https://jaeheon.kr/155](https://jaeheon.kr/155)
- [https://inf.run/VyTM](https://inf.run/VyTM)
