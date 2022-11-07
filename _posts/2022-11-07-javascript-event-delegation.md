---
title: "[JS] 이벤트 위임"
excerpt: "자바스크립트 이벤트 위임"

categories:
  - Javascript
tags:
  - [Javascript, Event-Delegation]

permalink: /Javascript/javascript-event-delegation/

toc: true
toc_sticky: true
 
date: 2022-11-07
last_modified_at: 2022-11-07
---
자바스크립트에 이벤트 위임에 대한 개념에 대한 포스팅입니다.

***

## ✅ Event Delegation 이란 무엇인가요?
`Event Delegation`: `이벤트위임`은 **[이벤트 버블링](#✔-이벤트-버블링-event-bubbling)을 이용해 상위요소에서 하위 요소의 이벤트를 제어하는 방식**입니다.

## ✅ Event Delegation 은 어떻게 구현하나요?
하위 요소에 이벤트 리스너(혹은 이벤트 핸들러)를 생성하는 대신, **상위 요소에만 이벤트 리스너를 생성하고 해당 이벤트 리스너에서 어떤 요소에서 이벤트가 발생했는지 조건문을 설정**하는 방식으로 이벤트 위임을 구현할 수 있습니다.

```html
<!-- html -->
<div id="div-content">
  <span id="span-content">
    <button id="btn">버튼</button>
  </span>
</div>
```

```javascript
// js

// id 속성 조건문

// 상위 요소인 id가 "div-content"인 div 노드 접근
const divNode = document.getElementById("div-content");

// div 노드에만 이벤트 리스너를 설정
divNode.addEventListener("click", function (e) {
    const id = e.target.id;

    // 이벤트 객체의 target.id로 조건문을 설정
    if (id === "div-content") {
        // div click event
        ...
    } else if (id === "span-content") {
        // span click event
        ...
    } else if (id === "btn") {
        // button click event
        ...
    }
});
```
```javascript
// js

// tagName 속성 조건문

// 상위 요소인 id가 "div-content"인 div 노드 접근
const divNode = document.getElementById("div-content");

// div 노드에만 이벤트 리스너를 설정
divNode.addEventListener("click", function (e) {
    const tagName = e.target.tagName;

    // 이벤트 객체의 target.id로 조건문을 설정
    if (tagName === "DIV") {
    // div click event
    ...
    } else if (tagName === "SPAN") {
    // span click event
    ...
    } else if (tagName === "BUTTON") {
    // button click event
    ...
    }
});
```

위와 같이 `id` 속성이나 `tagName` 속성으로 조건문을 설정하여 이벤트 위임을 구현할 수 있습니다. 

## ✅ 이벤트 위임의 장점과 단점이 무엇인가요?
### ✔ 장점
: **코드 가독성 ⬆, 메모리 절약**

다수의 이벤트 핸들러를 할당하는 대신 하나의 이벤트 핸들러만 할당하기 때문에, 코드가 단순해 지고 메모리가 절약됩니다.
### ✔ 단점
: 이벤트가 반드시 버블링되어야 합니다. `focus` 이벤트처럼 버블링되지 않는 이벤트나, [`stopPropagation()`](#✔-eventstoppropagation)을 사용한 경우에는 이벤트 위임을 사용할 수 없습니다.

## 📕 용어 설명
### ✔ 이벤트 버블링 (Event Bubbling)
**이벤트 버블링 (Event Bubbling)**은 특정 요소에서 이벤트가 발생했을 때, 해당 이벤트가 더 **상위 요소들로 전달되어가는 특성**을 의미합니다.

![이벤트버블링](https://joshua1988.github.io/images/posts/web/javascript/event/event-bubble.png)

```html
<!-- html -->
<body>
	<div class="one">
		<div class="two">
			<div class="three">
			</div>
		</div>
	</div>
</body>
```
```javascript
// js
const divs = document.querySelectorAll('div');
divs.forEach(function(div) {
	div.addEventListener('click', logEvent);
});

function logEvent(event) {
	console.log(event.currentTarget.className);
}
```
위 코드와 같이 세개의 `div`태그에 모두 클릭이벤트를 등록하고  `three` 클래스를 갖는 `div`태그를 클릭시 `logEvent`함수를 실행시켰을 때, 아래와 같은 결과가 출력됩니다.

three

two

one

이와 같은 하위에서 상위 요소로의 이벤트 전파 방식을 **이벤트 버블링(Event Bubbling)**이라고 합니다.

### ✔ 이벤트 캡쳐 (Event Capture)
**이벤트 캡쳐 (Event Capture)**는 이벤트 버블링과 반대방향으로 진행되는 이벤트 전파방식입니다.

![이벤트캡처](https://joshua1988.github.io/images/posts/web/javascript/event/event-capture.png)

```html
<!-- html -->
<body>
	<div class="one">
		<div class="two">
			<div class="three">
			</div>
		</div>
	</div>
</body>
```
```javascript
// js
const divs = document.querySelectorAll('div');
divs.forEach(function(div) {
	div.addEventListener('click', logEvent, {
        capture: true
    });
});

function logEvent(event) {
	console.log(event.currentTarget.className);
}
```
`addEventListener()` 에서 옵션 객체에 `capture: true`를 설정해주면 됩니다.

그러면 해당 이벤트를 감지하기 위해 이벤트 버블링과 반대 방향으로 탐색합니다.

따라서, 아까와 동일하게 <div class="three"></div> 를 클릭해도 아래와 같은 결과가 나타납니다.

one

two

three

이와 같은 **상위에서 하위 요소로의 이벤트 전파 방식**을 **이벤트 버블링(Event Bubbling)**이라고 합니다.

## ✔ event.stopPropagation()
`event.stopPropagation()` 은 **이벤트가 전파되는 것을 방지**합니다.

- **이벤트 버블링**의 경우에는 클릭한 요소의 이벤트만 발생시키고 상위요소로 이벤트를 전달하는 것을 방해합니다.

- **이벤트 캡쳐**의 경우에는 클릭한 요소의 최상위 요소의 이벤트만 동작시키고 하위요소들로 이벤트를 전달하지 않습니다.

```javascript
function logEvent(event) {
  event.stopPropagation();
}
```
***
## 🔗 참고
- [이벤트 버블링, 이벤트 캡처 그리고 이벤트 위임까지](https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/)