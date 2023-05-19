---
layout: post
title: "prevent app freezes when use JSON.parse"
categories: TIL JavaScript
---

## use JSON.parse

- Parse json to an object or value.
- but, Sometimes value to pars is not json.
- so, `JSON.parse` code causes error
- Use try catch to `prevent apps from stopping` at that time.

## example

```JavaScript
const parseJSON = (str) => {
    try {
        return JSON.parse(str);
    } catch {
        console.error(str is not JSON);
        return ''; //return empty string;
    }
}
```


## Reference
- [째스터, [JavaScript] JSON.parse 사용 시 Error 방지, https://ramdajs.com/docs/#compose, 2018.11.01](https://jjester.tistory.com/13)
- [mdn web docs, JSON.parse(), https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse, accessed 2023.05.19](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)