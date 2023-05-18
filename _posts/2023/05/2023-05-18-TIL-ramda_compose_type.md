---
layout: post
title: "type of R.compose"
categories: TIL TypeScript Ramda.js
---

## Type of R.compose

    - Type declaration is Union type.
    - The first is the input value (argument).
    - From the second, specify the type in the order of function 1 and function 2 (function 1, 2 is return type)

## example

```TypeScript
R.compose<[{[key: string]: number}], number, number,  >(
	(val) => val + 1,
	R.propOr(0, ['a'])
)({a: 1, b: 2});
```


## Reference
- [ramda Documentation, compose(), https://ramdajs.com/docs/#compose, Accessed 2023.05.18](https://ramdajs.com/docs/#compose)
- [@types/ramda, https://www.npmjs.com/package/@types/ramda](https://www.npmjs.com/package/@types/ramda)