---
title: "[JS] 동기 & 비동기"
excerpt: "자바스크립트에서의 동기, 비동기 처리"

categories:
  - Javascript
tags:
  - [Javascript, Asynchronous]

permalink: /Javascript/javascript-async/

toc: true
toc_sticky: true
 
date: 2022-11-07
last_modified_at: 2022-11-07
---
자바스크립트에서의 동기, 비동기 처리에 대한 개념에 대한 포스팅입니다.

***

![이미지](https://i.imgur.com/hh3Mawr.png)

더 쉬운 이해를 위해 동기 / 비동기 처리의 차이에 대한 이미지를 첨부합니다!

## ✅ 동기(Synchronous)란 무엇인가요?
동기는 요청을 보낸 후 결과물을 받아야지만 다음 동작이 이루어지는 방식을 의미합니다.

모든 일은 순차적으로 진행되면 어떤 작업이 수행중이라면 다음 작업은 대기하게 됩니다.
```javascript
function func1() {
    console.log('첫번째 함수!');
    func2();
}

function func2(){
    console.log('두번째 함수!');
    func3();
}

function func3() {
    console.log('세번째 함수');
}

func1();
```
출력값은 아래와 같습니다.
첫번째 함수!
두번째 함수!
세번째 함수!

## ✅ 비동기(Asynchronous)란 무엇인가요?
데이터를 서버로 부터 받아오는 앱을 만든다고 가정합니다. 서버로부터 데이터를 받아와서 해당 데이터를 뿌려주어야 하므로 맨 처음에 서버로부터 데이터를 받아오는 코드가 실행되어야 할 것입니다.

이것을 동기적으로 처리하게 된다면 데이터를 받아오기 까지 기다린 후 앱이 실행될 것이고, 데이터의 양이 많을 수록 앱의 실행속도는 기하급수적으로 느려지게 됩니다.

이러한 문제점을 보완하기 위해 비동기적으로 처리를 해야 합니다.

```javascript
function func1(){
    console.log('첫번째 함수!');
    func2();
}

function func2(){
    setTimeout(function(){
        console.log('두번째 함수!');
    }, 0);
    func3();
}

function func3(){
    console.log('세번째 함수!');
}
func1();
```
출력값은 아래와 같습니다.
첫번째 함수!
세번째 함수!
두번째 함수!

## ✅ 자바스크립트에서 어떠한 경우에 비동기처리가 필요한가요>?
- AJAX web api 요청
- 파일 읽기
- 암호화 / 복호화
- 작업 예약

## ✅ 자바스크립트에서 비동기적으로 코딩하는 방법이 무엇인가요?
자바스크립트에서 비동기처리를 위해 [`callback 함수`](#callback-함수), `Promise`, `async` / `await` 를 사용할 수 있습니다.
콜백함수 사용에는 콜백지옥이라는 단점이 존재해, ES6에 도입된 `Promise`나 ES8에 도입된  `async` / `await를` 사용하여 비동기처리를 합니다.

### ✔ Promise
`Promise`란 어떠한 값을 미래에 반환하는 자바스크립트 오브젝트입니다.
비동기 작업이 성공 또는 실패로 끝났을 때, 그 다음 수행 내용을 처리할 수 있게 하는 도구입니다.

#### Promise의 상태
- **pending (대기)**<br/>
: 넘겨받은 콜백 함수에서 아직 `resolve()` 혹은 `reject()`가 실행되기 전 상태
- **fulfilled (성공)**<br/>
: 넘겨받은 콜백함수에서 `resolve()`가 실행된 상태
- **rejected (실패)**<br/>
: 넘겨받은 콜백함수에서 `reject()`가 실행된 상태

#### Promise 예제
```javascript
const promise = new Promise((resolve, reject) => {
    setTimeout(()=>{
        resolve('Good');
    }, 3000);
});

promise.then(
    (result) => console.log('Success!', result)
).catch(
    (error) => console.log('Error!', error)
)
```
- 위처럼 `Promise`는 생성 시 콜백함수 하나를 전달합니다. 해당 콜백함수는 `resolve`, `reject` 라는 두 인자를 가지는데, 이때 `resolve`, `reject` 도 함수입니다.
- Promise에 넘긴 콜백함수 내용이 메인 로직입니다.
    - 해당 로직의 결과는 `resolve()`가 실행되느냐, `reject()`가 실행되느냐에 따라서 달라집니다.
    - resolve 시 `then()`의 콜백함수 실행
    - reject 시 `catch()`의 콜백함수 실행

### ✔ async / await
javascript 비동기 처리 패턴 중 가장 최근에 나온 ES8 문법으로, 기존의 비동기 처리 방식인 콜백 함수와 `Promise` 의 단점을 보완하고 개발자가 읽기 좋은 코드를 작성할 수 있게 도와줍니다.
#### async / await 기본 문법
```javascript
async function 함수명() {
  await 비동기_처리_메서드_명();
}
```
- `async` 는 `function` 앞에 위치합니다.
- `function` 앞에 `async`를 붙이면 해당 함수는 항상 `Promise`를 반환합니다.
- `await`는 `Promise`가 처리될 때 까지 대기합니다.
#### async / await 예제
```javascript
const promise = new Promise((resolve, reject) => {
    setTimeout(()=>{
        resolve('Good');
        reject('Bad');
    }, 3000);
});

promise.then(
    (result) => console.log('Success!', result)
).catch(
    (error) => console.log('Error!', error)
)


async function f() {
    let result = await new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve('Good');
        }, 3000);
    });
    console.log(result);
}
f(); // 3초 뒤 콜솔에 Good 이 출력됩니다.
```
***
## 📕 용어 공부
### ✔ callback 함수
함수가 끝나고 난 뒤에 실행되는 함수입니다. 자바스크립트에서 함수는 객체입니다. 따라서 함수는 함수를 인자로 받고 다른 함수를 통해 반환될 수 있습니다. 인자로 대입되는 함수를 콜백함수라고 부릅니다.
### ✔ 콜백지옥 (callback hell)
콜백 지옥은 JavaScript를 이용한 비동기 프로그래밍시 발생하는 문제로서, 함수의 매개 변수로 넘겨지는 콜백 함수가 반복되어 코드의 들여쓰기 수준이 감당하기 힘들 정도로 깊어지는 현상을 말합니다.
```javascript
step1(function (value1) {
    step2(function (value2) {
        step3(function (value3) {
            step4(function (value4) {
                step5(function (value5) {
                    step6(function (value6) {
                        // Do something with value6
                    });
                });
            });
        });
    });
});
```
이와 같은 코드는 가독성이 떨어지고, 코드를 수정하기 어려워 집니다.