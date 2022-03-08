---
layout: post
title: "클로저(Closure)"
categories: TIL JavaScript
tag: Closure
---

# 들어가기

- 이전에 원티드 프리온보딩 코스에서 수업을 들으면서 간단하게 [블로그에 정리](https://b41.kr/2022/02/22/원티드-위코드-fe-프리온보딩-일곱-번째-수업-4-closure/)했지만 너무 얕게 공부했다는 생각이 들어서 다시 정리.

# Scope

- 변수가 유효한 범위를 말함.
- Global Scope (전역), Local Scope (지역)가 있음.

# Lexical scoping

- 어휘적 범위 지정
- Lexical : 변수가 어디에서 사용이 가능한 지 알기 위해서 변수가 소스코드 내 어디에서 선언되었는지 고려하는 것.
- 중첩된 함수는 외부 범위에서 선언한 변수에도 접근할 수 있음.

```
function init() {
    var name = "b41";
    function displayName() {
        alert (name);
    }
    displayName();
}
init();
```

- `var name`은 `init()` 함수의 지역 변수.
- `name`은 `init()` 밖에서는 사용할 수 없지만 중첩된 함수 `displayName()`에서는 사용할 수 있음.

# 클로저(Closure)

```
function makeFunc() {
      var name = "b41";
      function displayName() {
        alert(name);
      }
      return displayName;
    }

    var myFunc = makeFunc();
    //myFunc변수에 displayName을 리턴함
    //유효범위의 어휘적 환경을 유지
    myFunc();
    //리턴된 displayName 함수를 실행(name 변수에 접근)
```

- 이전 예제와 다르게 `displayName()` 함수를 실행하지 않고 리턴만 함.
- 하지만 `myFunc`을 실행했을 때 `displayName()` 함수가 실행됨.
- 보통 다른 언어에서는 return되었으니까 name에는 접근할 수 없다고 생각함.
- 하지만 JavaScript에서는 리턴하는 함수가 클로저(closure)를 형성
- 즉, 클로저는 `함수`와 함수가 선언된 `Lexical 환경`의 조합

- 재미있는 클로저 예제 1

```
    function makeAdder(x) {
      var y = 1;
      return function(z) {
        y = 100;
        return x + y + z;
      };
    }

    var add5 = makeAdder(5);
    var add10 = makeAdder(10);
    //클로저에 x와 y의 환경이 저장됨

    console.log(add5(2));  // 107 (x:5 + y:100 + z:2)
    console.log(add10(2)); // 112 (x:10 + y:100 + z:2)
    //함수 실행 시 클로저에 저장된 x, y값에 접근하여 값을 계산
```

- x, y, z의 합을 리턴하는 함수 `makeAdder(x)`
- `add5`, `add10`는 모두 클로저임.
- 여기에서 x, y값이 이미 정해짐
- 그리고 `add5(z) 실행할 때 클로저에 + z값이 추가되서 계산된 값이 리턴됨.

- 재미있는 클로저 예제 2

```
var A = function() {
    var a = 1;

    var B = function() {
        return ++a;
    };

    **return B;**
};

var outer = A();
console.log(outer());  // 2
console.log(outer());  // 3
```

- `outer()`는 클로저
- `outer()`를 한 번 실행하니 `a = 1`값에서 다시 `1`이 추가되었으므로 `2`가 리턴됨
- 한 번 더 실행하면 클로저가 a값을 기억하고 있다가 `3`을 리턴함

# Reference

https://developer.mozilla.org/ko/docs/Web/JavaScript/Closures
