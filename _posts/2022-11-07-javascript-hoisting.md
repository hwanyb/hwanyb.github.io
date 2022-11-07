---
title: "[JS] 호이스팅 (Hoisting)"
excerpt: "자바스크립트 호이스팅 (Hoisting)이란???"

categories:
  - Javascript
tags:
  - [Javascript, Hoisting]

permalink: /Javascript/javascript-hoisting/

toc: true
toc_sticky: true
 
date: 2022-11-07
last_modified_at: 2022-11-07
---
자바스크립트 호이스팅 개념에 대한 포스팅입니다.

***

## ✅ Hoisting 이 무엇인가요?
호이스팅이란 **끌어올린다**라는 의미로, **변수 및 함수 선언문이 스코프 내의 최상단으로 끌어올려지는 현상**을 말합니다.

여기서 주의할 점믄 **선언문** 이라는 것이며 **대입문**은 끌어올려지지 않습니다.

`var`로 선언한 변수의 경우 호이스팅 시 `undefined` 로 변수를 초기화합니다. 반면 `let` 과 `const` 로 선언한 변수의 경우 호이스팅 시 변수를 초기화하지 않습니다.

***

```javascript
console.log(a);
var a = 2;
```
컴파일러는 `var a = 2;` 를 2개의 구문으로 봅니다.
- `var a`
- `a = 2`
`var a` 는 변수 선언문으로 컴파일을 할 때 처리하고, `a = 2` 는 실행할 때 까지 내버려 둡니다. 따라서 변수 `a` 는 호이스팅 되고 콘솔에는 `undefined` 라는 결과가 출력됩니다.
> `var`는 선언, 초기화가 동시에 이루어지기 때문에 undefined를 출력하지만 `let`, `const`는 선언단계만 호이스팅 되기 때문에 `Reference Error`를 출력합니다.

***

```javascript
func();
function func () {
    console.log('함수 선언문 호이스팅');
}
```

함수 선언문의 경우에도 호이스팅되어 `함수 선언문 호이스팅` 이라는 결과가 출력됩니다.

여기서 주의할 점은 함수 선언문은 호이스팅되지 않습니다.

```javascript
func();
var func = function () {
    console.log('함수 선언문 호이스팅');
}
```

함수표현식  func은 var로 선언되이 호이스팅되ㅣ었지만, 실제 func에 할당될 함수로직은 호출된 이후에 선헌되므로, 함수표현식 func는 함수로 인식되지 않고 변수로 인식됩니다. 따라서 콘솔에는 `Uncaught TypeError: func is not a function`이라는 에러가 출력됩니다.