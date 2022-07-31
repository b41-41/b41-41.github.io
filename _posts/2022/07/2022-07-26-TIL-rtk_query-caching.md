---
layout: post
title: "[RTK Query] Mutation과 캐싱(Caching)"
categories: TIL RTK_Query
---

## Mutations

- 서버에서 데이터 업데이트, 추가를 요청하고 변경사항을 캐시에 적용할 때 사용한다.
- 캐시된 데이터를 무효화하고 강제로 다시 가져올 수도 있다.(리패칭)

- createApi의 `endpoints`에 아래와 같이 추가해서 세팅.


```
 updatePost: build.mutation<responseType, requestType>({
      query: (body) => ({
        url: `post/add`,
        method: 'POST',
        body,
      }),
```
- 요청한 데이터의 반환 값을 캐싱하려면 `createApi`에 태그 타입을 정의

```
  tagTypes: ['Posts'],
```

- 그리고 Mutation 안에 `invalidatesTags` 추가

```
 updatePost: build.mutation<responseType, requestType>({
      query: (body) => ({
        url: `post/add`,
        method: 'POST',
        body,
      }),
       invalidatesTags: () => [{ type: 'Posts'}],
```

- `invalidatesTags`안의 콜백 함수를 통해 특정 값만 캐싱하는 것도 가능

## Reference

- [Redux Toolkit, Using RTK Query - Mutations, 2022.06.24](https://redux-toolkit.js.org/rtk-query/usage/mutations)