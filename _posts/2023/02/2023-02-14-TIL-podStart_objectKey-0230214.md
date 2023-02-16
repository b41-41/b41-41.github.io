---
layout: post
title: "String.prototype.padStart(), object key에 변수 넣기"
categories: TIL JavaScript
---

## String.prototype.padStart()

    - 문자열 시작을 다른 문자열로 채워서 정해진 길이를 만족하는 새로운 문자열 반환
    - `String.podStart(문자길이(number), 채울 문자(string)`
    - 예)

        ```
            const three = '3';
            const hour = three.padStart(2, '0');

            console.log(hour);
            //결과 : 03
            
        ```

    - padEnd()를 사용하면 오른쪽(끝부분)부터 문자가 채워진다.

## object key에 변수 넣는 방법

    - 변수를 []로 감싼다.
    - (es6부터 지원)
    - 예)

        ```
            const getKey = '1';
            const obj = {[getKey]: 1};
            console.log(obj);
            //결과 : {'1': 1}
        ```


## Reference
- [mdn web docs, String.prototype.padStart(), https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/padStart, 2022.12.29 (Accessed 2023.02.14)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/padStart)
