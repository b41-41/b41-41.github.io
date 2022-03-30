---
layout: post
title: "Jest 스냅샷(Snapshot) 테스트"
categories: TIL TEST UI
---

# 들어가기

약 한 달 전에 Unit Test를 위해 Jest를 사용하면서 여러 가지 테스트 자동화에 대해서 알게 되었다. [(해당 포스팅으로 이동)](https://b41-41.github.io/posts/TIL_bubbling/)

최근에는 Cypress를 사용해서 사용자 관점에서의 UI, 기능 테스트를 진행하는 방법을 배웠는데, [(해당 포스팅으로 이동)](https://b41-41.github.io/posts/TIL-e2e_test-220329/)

그 외에도 Jest를 이용한 UI테스트가 있다고 해서 알아보았다.

# Jest Snapshot Testing

- 미리 찍어놓은 스냅샷과 UI 컴포넌트를 렌더링하고 찍은 스냅샷을 비교하여 일치하는 지 확인하는 UI 자동 테스트 방법.

## 장점

- 자동 테스트이기 때문에 달라지는 부분이 있으면 바로 확인할 수 있다.

## 단점

- UI 변경이 자주 있는 컴포넌트일 경우 오히려 매번 수정하는 비용이 더 발생할 수 있다.
- 혹은 UI 변경이 전혀 없는 컴포넌트인데 테스트 코드를 작성함으로써 더 비용이 발생할 수 있다.

## 기타

- 직접 사용해 보지는 않아서 다음 프로젝트 때 적절한 상황이 발생한다면 사용해 볼 예정이다.

# Reference

- [https://mulder21c.github.io/jest/docs/en/next/snapshot-testing](https://mulder21c.github.io/jest/docs/en/next/snapshot-testing)
- [https://www.daleseo.com/jest-snapshot/](https://www.daleseo.com/jest-snapshot/)
