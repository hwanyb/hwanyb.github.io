---
title: "[JS] Closure"
excerpt: "자바스크립트에서의 클로저란?"

categories:
  - Javascript
tags:
  - [Javascript, Closure]

permalink: /Javascript/javascript-closure/

toc: true
toc_sticky: true
 
date: 2022-11-07
last_modified_at: 2022-11-07
---
자바스크립트에서의 동기, 비동기 처리에 대한 개념에 대한 포스팅입니다.

***

## ✅ Closure 란 무엇인가요?
함수와 함수가 선언된 어휘적 환경(Lexical Environment)의 조합입니다.
또한 함수가 속한 Lexical Scope를 기억하여 함수가 Lexical Scope 밖에서 실행될 때도
그 스코프에 접근할 수 있게 하는 기능을 말합니다.
```javascript
function outer() {
  var a = 2;
  function inner() {
    console.log(a);
  }
  return inner;
}
var func = outer();
func(); // 2
```
내부함수인 `inner()`는 해당 스코프의 변수인 `a` 를 참조하고 있습니다.
스코프 외부에서 `inner()`가 실행되어도 해당 스코프를 기억하기 때문에 2를 출력하게 됩니다.즉 여기서 클로저는 `inner()`입니다.