---
title: "[JS] 자바스크립트 런타임"
excerpt: "자바스크립트 런타임 개념 정리"

categories:
  - Javascript
tags:
  - [Javascript, Runtime, Javascript-Runtime]

permalink: /Javascript/runtime/

toc: true
toc_sticky: true
 
date: 2022-11-07
last_modified_at: 2022-11-07
---
자바스크립트 런타임에 대한 개념 정리 포스팅입니다.

***

**런타임 (Runtime)** 이란 프로그래밍 언어가 구동되는 환경을 말합니다.

## ✅ 자바스크립트의 런타임에 대해 설명해 주세요.
![크롬의 자바스크립트 런타임](https://beomy.github.io/assets/img/posts/javascript/javascript_runtime.png)

위 그림은 크롬의 자바스크립트 런타임을 표현한 그림입니다.

자바스크립트의 런타임은 `자바스크립트 엔진`, `Web API`, `콜백큐`, `이벤트 루프`, `렌더큐` 로 구성됩니다.

### ✔ `자바스크립트 엔진`
크롬은 V8을 사용하고 있고, V8은 구글에서 개발한 오픈소스 자바스크립트 엔진입니다.

V8은 싱글스레드를 제공합니다.

싱글스레드는 하나의 `콜스택`과 하나의 `힙`을 제공합니다. 하나의 콜스택을 가진다는 의미는 한 번에 한 가지 일밖에 못한다는 의미입니다.

- `콜스택` (Call Stack)
    - 실행된 코드의 환경을 저장하는 자료구조
    - 함수호출시 함수가 저장
    - 후입선출: LIFO (Last In Firt Out)
- `힙` (Heap)
    - 할당된 메모리들이 저장되는 역역

### ✔ `Web API`
`Web API`는 자바스크립트 엔진에서 정의되지 않았던 `setTimeout` 이나 `AJAX`, `DOM` 이벤트 등의 메소드를 지원합니다.

콜스택에서 실행된 비동기함수는 Web API를 호출하고, Web API는 콜백함수를 콜백큐에 넣습니다.

### ✔ `이벤트 루프 (Event Roop)`
이벤트 루프는 콜스택과 콜백큐를 관찰하는 역할을 합니다.

**콜스택이 비어있으면, 콜백큐의 첫번째 콜백을 스택**에 쌓습니다.

### ✔ `콜백큐 (Callback Queue)`
콜백큐는 Web API 결과값을 쌓아두는 큐입니다. 콜스택과 다르게 가장 먼저 들어온 함수를 가장 먼저 처리합니다. 선입선출: FIFO (First In Firt Out)

> 자바스크립트 런타임 동작 예제

![이벤트루프](https://beomy.github.io/assets/img/posts/javascript/javascript_runtime_settimeout.gif)

***

## 🔗 참고
- [자바스크립트 런타임](https://beomy.github.io/tech/javascript/javascript-runtime/)
- [개발자 90%가 모르는 자바스크립트 동작원리 (Stack, Queue, event loop)](https://www.youtube.com/watch?v=v67LloZ1ieI&t=250s)