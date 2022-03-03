---
layout: post
title: "Debounce, MUI 사용법"
categories: TIL JavaScript React TypeScript Merterial-UI 
---

# Debounce
- 연속으로 발생하는 이벤트를 제어하기 위해서 사용함.
- 이번 프로젝트에서 onChange로 검색 창을 구현하는데 실시간으로 변하는 값의 최적화 때문에 사용.
- useDebounce라는 커스텀 훅을 만들어서 값이 입력된 후 일정 시간이 지났을 때 처리하는 방식으로 만들 수 있음.

```
typeScript
import { useEffect, useState } from 'react'

export function useDebounce<T>(value: T, delay?: number): T {
  const [debouncedValue, setDebouncedValue] = useState<T>(value)

  useEffect(() => {
    const timer = setTimeout(() => setDebouncedValue(value), delay || 500)

    return () => {
      clearTimeout(timer)
    }
  }, [value, delay])

  return debouncedValue
}
```

# MUI 사용법
- mui를 import해서 사용
- styled component 처럼 커스텀해서 사용할 수 있음
- 커스텀할 때 모양은 styled 컴포넌트랑 조금 다른 데 아래와 같음

```
import { styled } from '@mui/material/styles';
import { InputBase } from '@mui/material';

export const SearchBar = styled(InputBase)`
  width: 100%;
  color: #252525;
`;
```