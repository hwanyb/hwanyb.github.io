---
title: "[JS] 자바스크립트 this"
excerpt: "자바스크립트에서 this란 무엇인지, 어떻게 쓰이는지.."

categories:
  - Javascript
tags:
  - [Javascript, this]

permalink: /Javascript/javascript-this/

toc: true
toc_sticky: true
 
date: 2022-11-07
last_modified_at: 2022-11-07
---
자바스크립트 에서 this란 무엇인지, 어떻게 쓰이는지에 대한 정리 포스팅입니다.

***

## ✅ 자바스크립트에서 this란 무엇인가요?
`this`는 호출 패턴에 따라 다른 객체를 참조합니다. [실행 컨텍스트](#-실행-컨텍스트-ec-execution-context)가 생성될때마다 this의 [바인딩](#-바인딩-binding)이 일어납니다.


즉, 바인딩이 선언이 아닌 호출에 따라 달라집니다.

this 의 바인딩을 우선순위 순으로 나열해 보면 다음과 같습니다.

1. [`new`](#-new) 를 사용했을 때 해당 객체로 바인딩됩니다.
    ```javascript
    var name = 'global';
    function Func() {
        this.name = "Func";
        this.print = function f() {
            console.log(this.name);
        };
    }
    var a = new Func();
    a.print(); // Func
    ```
2. [`call`](#-call), [`apply`](#-apply), [`bind`](#-bind) 와 같은 명시적 바인딩을 사용했을 때, 인자로 전달된 객체에 바인딩됩니다.
    ```javascript
    function func() {
        console.log(this.name);
    }
    var obj = { name: 'obj name' };
    func.call(obj); // obj name
    func.apply(obj); // obj name
    func.bind(obj)(); // obj name
    ```
3. 객체의 메소드로 호출할 경우 해당 객체에 바인딩됩니다.
    ```javascript
    var obj = {
        name: 'obj name',
        print: function p() {
            console.log(this.name);
        }
    };
    obj.print(); // obj name
    ```
4.  그 외의 경우
    - stric mode (엄격모드): `undefined`로 초기화됩니다.
    - 일반 브라우저라면 `window` 객체에 바인딩됩니다.

***

## 📕 용어 설명
### ✔ 바인딩 (Binding)
바인딩이란 프로그램의 어떤 기본 단위가 가질 수 있는 구성요소의 구체적인 값, 성격을 확정하는 것을 의미합니다.
### ✔ 실행 컨텍스트 (EC: Execution Context)
실행 컨텍스트란 `scope`, `hoisting`, `this`, `function`, `closure` 등의 동작원리를 담고 있는 자바스크립트의 핵심 원리입니다.
### ✔ new
new 는 자바스크립트의 고유의 예약어이며, 고유의 연산자 (operator)입니다.
### ✔ call
`call`을 사용하면 함수를 실행하고, 함수의 첫번째 인자로 전달하는 값에 `this`를 바인딩합니다.
### ✔ apply
`call`과 마찬가지로 `apply`를 사용하묜 함수를 실행하고 함수의 첫번째 인자로 전달하는 값에 `this`를 바인딩합니다.<br />
`call`과의 차이점은 인자를 배열의 형태로 전달한 다는 점입니다. 이 때 인자로 배열 자체가 전달되는 것이 아니라, 배열의 요소들이 값으로 전달됩니다.
### ✔ bind
`bind`는 함수의 첫번째 인자에 `this`를 바인딩한다는 점은 `call`, `apply`와 같지만, 함수를 실행하지 않으며 새로운 함수를 반환합니다. 즉 반환된 새로운 함수를 실행해야 원본 함수가 실행됩니다.