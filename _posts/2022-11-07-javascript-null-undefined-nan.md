---
title: "[JS] null & undefined & undeclared & NaN"
excerpt: "자바스크립트에서의 null & undefined & undeclared & NaN 이란 무엇인가요?"

categories:
  - Javascript
tags:
  - [Javascript, null, undefined, Nan]

permalink: /Javascript/null-undefined-nan/

toc: true
toc_sticky: true
 
date: 2022-11-07
last_modified_at: 2022-11-07
---
자바스크립트에서의 `null` & `undefined` & `undeclared` & `NaN` 에 대한 포스팅입니다.

***

## ✅ 자바스크립스에서 null이란 무엇인가요?
`null`은 빈 값으로, 변수는 존재하나, null 값으로 변수에 할당된 상태입니다.
```javascript
const test = null;
console.log(test); // null
console.log(typeof test); // object
```
> `null`의 type은 `object`임에 주의하여야 합니다.

## ✅ 자바스크립스에서 undefined란 무엇인가요?
`undefined`는 변수는 존재하나, 어떠한 값으로도 할당되지 않은 상태입니다.

var 선언문의 경우, 호이스팅되었을 때 변수 선언과 초기화가 동시에 일어나기 때문에 변수가 undefined 가 됩니다.
```javascript
var test;
console.log(test); // undefined
console.log(typeof test); // undefined
```

## ✅ 자바스크립스에서 undeclared란 무엇인가요?
`undeclared`는 변수가 선언조차 되지 않은 상태입니다. 참조시 에러가 발생합니다.
```javascript
console.log(test) // Uncaught ReferenceError: test is not defined at <anonymous>:1:13
console.log(typeof test) // undefined
console.log(typeof undeclared) // undefined
```
> `undeclared`의 type은 `undefined`입니다.

## ✅ 자바스크립스에서 NaN이란 무엇인가요?
`NaN`은 **Not-A-Number** (숫자가 아님)의 의미로, 표현 불가능한 수치형 결과입니다.
```javascript
const test = 0 / 0;
console.log(test); // NaN
```

***

## 🔗 참고
- [Javascript undefined/undeclared/null and NaN 🧟](https://dkrnfls.tistory.com/388)
- [Javascript의 undefined는 정확히 무슨 뜻일까? (null vs undefined)](https://siyoon210.tistory.com/148)
- [Nan -mdn](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/NaN#%EC%8B%9C%EB%8F%84%ED%95%B4%EB%B3%B4%EA%B8%B0)