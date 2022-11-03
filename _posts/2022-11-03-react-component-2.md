---
title: "React 컴포넌트(2) - 함수형 컴포넌트"
excerpt: "리액트 컴포넌트에 대한 기초를 다시 다지기 위한 포스팅!"

categories:
  - React
tags:
  - [React, Component, FunctionComponent, useState, useEffect]

permalink: /React/react-component-2/

toc: true
toc_sticky: true
 
date: 2022-11-03
last_modified_at: 2022-11-03
---
안녕하세요! 리액트 클래스형 컴포넌트 포스팅에 이어 함수형 컴포넌트 포스팅을 작성해 보려 합니다!

이 포스팅에서는 리액트의 함수형컴포넌트 `props`, `state`, `hooks` 등에 대해 알아보겠습니다~~

***

## ✅ **함수형 컴포넌트에서의 `props`사용법**

부모 컴포넌트인 `App.js`에서 `FuncComp`라는 컴포넌트에 `props`로 `initNum`을 전달해 보겠습니다.

```javascript
function App() {
        return (
            <div className="container">
                <h1>Hello World!</h1>
                <FuncComp initNum={2} />
            </div>
        );
    }

function FuncComp(props) {
    return (
      <div className="container">
        <h2>Function Component</h2>
        <p>Number: {props.initNum}</p>
      </div>  
    );
}
```

함수형 컴포넌트에서는 부모컴포넌트에서 전달한 `props`를 사용하기 위해서는 함수의 인자로 받아와야 합니다.

## ✅ **함수형 컴포넌트에서의 `state`사용법(useState)**

함수형 컴포넌트에서 state를 사용하려면 `useState`라는 `hook`을 사용해야 합니다.

`useState`는 배열을 반환합니다. 이 배열의 첫번째요소는 `현재 상태값`을 나타내는 변수이고, 두번째 요소는 `해당 상태값을 변경하는 함수입`니다.

`initNum`을 `props`로 전달받아 그 값을 `useState`의 인자로 전달하여 `number`의 초기값으로 설정합니다.

```javascript
import React, { useState } from 'react';

function App() {
        return (
            <div className="container">
                <h1>Hello World!</h1>
                <FuncComp initNum={2} />
            </div>
        );
    }

function FuncComp(props) {
  const [number, setNumber] = useState(props.initNum);
    return (
      <div className="container">
        <h2>Function Component</h2>
        <p>Number: {number}</p>
      </div>  
    );
}
```

## ✅ **함수형 컴포넌트에서의 `state` 변경법 (useState)**
위 코드에서 선언한 상태값 `number`의 값을 변경하기 위해서는 `useState`를 사용하여 선언한 배열의 두번째 값인 `setNumber` 함수를 호출해야합니다.

```javascript
import React, { useState } from 'react';

function App() {
        return (
            <div className="container">
                <h1>Hello World!</h1>
                <FuncComp initNum={2} />
            </div>
        );
    }

function FuncComp(props) {
  const [number, setNumber] = useState(props.initNum);
    return (
      <div className="container">
        <h2>Function Component</h2>
        <p>Number: {number}</p>
        <input type="button" value="random" onClick={() => setNumber(Math.random())} />
      </div>  
    );
}
```
`setNumber()`의 인자에 변경하고자 하는 값을 넣으면 됩니다.


## ✅ **함수형 컴포넌트에서의 라이프사이클 구현 (useEffect)**
hook의 등장 전 함수형 컴포넌트에서 라이프 사이클을 구현하는 것은 불가능했습니다.

하지만 `useEffect` 라는 hook을 사용하여 함수형 컴포넌트에서도 라이프 사이클을 구현할 수 있습니다.


`useEffect`가 컴포넌트의 라이프 사이클의 어느 위치에 호출되는 지 보기 위해 아래와 같은 코드를 작성하겠습니다.

```javascript
import React, { useState, useEffect } from 'react';

function App() {
        return (
            <div className="container">
                <h1>Hello World!</h1>
                <FuncComp initNum={2} />
            </div>
        );
    }

function FuncComp(props) {
  const [number, setNumber] = useState(props.initNum);

  useEffect(() => {
    console.log("useEffect");
  });
    console.log("render");

    return (
      <div className="container">
        <h2>Function Component</h2>
        <p>Number: {number}</p>
        <input type="button" value="random" onClick={() => setNumber(Math.random())} />
      </div>  
    );
}
```

위 코드를 실행시키면 콘솔창에

![image](https://user-images.githubusercontent.com/80311884/225677773-907b7723-5b97-4854-bce6-a6073283c21a.png)

이러한 결과가 뜨게 됩니다.

컴포넌트가 생성된 직후 호출되는 `componentDidMount` 메소드와 같다고 볼 수 있습니다.

랜덤 버튼을 클릭하면 콘솔창에

![image](https://user-images.githubusercontent.com/80311884/225678824-f6c76dcd-7c39-411f-8eff-1034094e18f7.png)

이러한 결과가 뜨게 됩니다.

컴포넌트가 업데이트된 직후에 호출되는 `componentDidUpdate`메소드와도 같다고 볼 수 있습니다.

정리해 보면 `useEffect`는 컴포넌트가 렌더링 된 후, 또는 컴포넌트가 업데이트 된 후에 일어날 `side effect`를 구현하기 위해 사용한다고 볼 수 있습니다.

`useEffect`를 `componentDidMount`와 `componentDidUpdate`, `componentWillUnmount`가 합쳐진 것으로 생각해도 좋습니다.

`componentWillUnmount` 와 같은 메소드가 `useEffect`에서는 어떻게 구현될 수 있을까요???
(밑으로...........)

## ✅ **useEffect - clean-up**
`useEffect` 의 return 함수는 클래스형 컴포넌트의 생명주기 메소드 `componentWillUnmount` 이고, 그 return 함수는 이펙트를 클린업하기 위해 사용한다.

`useEffect` 클린업 함수는 `useEffect`의 첫번째 인자 함수 내에 `return` 함수를 작성하여 사용할 수 있습니다.


```javascript
import React, { useState, useEffect } from 'react';

function App() {
        return (
            <div className="container">
                <h1>Hello World!</h1>
                <FuncComp initNum={2} />
            </div>
        );
    }

function FuncComp(props) {
  const [number, setNumber] = useState(props.initNum);

  useEffect(() => {
    console.log("useEffect");
    return () => {
      // effect 이후에 어떻게 clean-up 할지..
      console.log("useEffect clean-up");
    }
  });
    console.log("render");

    return (
      <div className="container">
        <h2>Function Component</h2>
        <p>Number: {number}</p>
        <input type="button" value="random" onClick={() => setNumber(Math.random())} />
      </div>  
    );
}
```
`useEffect` 의 `return` 함수의 동작 순서는 다음과 같습니다.
1. props 나 state 가 업데이트
2. 컴포넌트 리렌더링
3. 이전 이펙트 클린업
4. 새로운 이펙트 실행

컴포넌트를 리렌더링 하기 전에 클린업이 되는 게 아니라, 리렌더링이 된 후에 클린업이 되고
그 다음 새로운 이펙트가 실행이 되는 것입니다.

### ✔ 왜 clean-up 함수를 사용할까요? 언제 사용해야 할까요?
`clean-up`함수는 컴포넌트가 렌더링된 후 `useEffect`내의 로직이 실행되기 전에 실행되는 함수입니다.

컴포넌트가 언마운트 되거나 업데이트 되기 직전에 어떤 작업을 수행하고 싶다면, clean-up 함수를 반환해주어야 합니다.

위에서 말한 것처럼 새로운 이펙트 실행을 하기 전에 이전 이펙트를 클린업을 해주는데 이 단계에서 클린업을 하게 되면, 선언될 당시의 과거의 변수 값을 참조하고 있던 이펙트가 클린업(정리)되고, 새로운 변수 값을 다시 참조하게 되는 것입니다.
>즉, `clean-up` 함수는 보다 효율적으로 `useEffect`가 작동할 수 있도록 제어하여 메모리 관리를 하기 위한 것입니다.

## ✅ **useEffect - skipping effect**
모든 렌더링 이후에 effect를 정리(clean-up)하거나 적용하는 것이 때때로 성능 저하를 발생시키는 경우도 있습니다.

클래스형 컴포넌트는 이러한 문제를 `componentDidUpdate에서` `prevProps`나 `prevState`와의 비교를 통해 이러한 문제를 해결할 수 있었습니다.
```javascript
componentDidUpdate(prevProps, prevState) {
  if (prevState.count !== this.state.count) {
    document.title = `You clicked ${this.state.count} times`;
  }
}
```
`useEffect`에서도 특정 값들이 리렌더링 시 변경되지 않는다면 React로 하여금 effect를 건너뛰도록 할 수 있습니다.

`useEffect`의 선택적 인수인 두 번째 인수로 배열을 넘기면 됩니다.


```javascript
import React, { useState, useEffect } from 'react';

function App() {
        return (
            <div className="container">
                <h1>Hello World!</h1>
                <FuncComp initNum={2} />
            </div>
        );
    }

function FuncComp(props) {
  const [number, setNumber] = useState(props.initNum);
 const [date, setDate] = useState(Date.now());

  useEffect(() => {
    console.log("useEffect");
    return () => {
      // effect 이후에 어떻게 clean-up 할지..
      console.log("useEffect clean-up");
    }
  }, [date]);

    console.log("render");

    return (
      <div className="container">
        <h2>Function Component</h2>
        <p>Number: {number}</p>
        <p>Date: {date}</p>
        <input type="button" value="random" onClick={() => setNumber(Math.random())} />
        <input type="button" value="date" onClick={() => setDate(Date.now())} />
      </div>  
    );
}
```
위 코드는 

![image](https://user-images.githubusercontent.com/80311884/225695505-795db4d8-3289-4b52-833b-0e4b6976f4e3.png)

`state`인 `number`, `date`를 렌더링하고 버튼 클릭시 값이 변경됩니다.

date 버튼 클릭시 콘솔창에는 아래와 같은 결과가 출력됩니다.

![image](https://user-images.githubusercontent.com/80311884/225696255-0e3b5378-a842-4e3b-9b1b-9107a1712a25.png)

random버튼 클릭시에는 아래와 같은 결과가 출력됩니다.

![image](https://user-images.githubusercontent.com/80311884/225696426-7a7e56bc-ca44-458b-82d9-623ad98cadf3.png)

이와 같이 useEffect의 두번째 인자에 `date`를 전달할 시, date값이 변경되어야만 `useEffect`, `clean-up`함수가 실행되는 것을 확인할 수 있습니다.


> useEffect의 두번째 인자를 빈 배열로 전달할 시 useEffect가 컴포넌트가 최초렌더링 될 때에만 실행됩니다.

***

휴,, 길고도 험한 포스팅이었습니다.

이번 포스팅에서는 리액트의 함수형 컴포넌트에서 props 사용법, useState, useEffect 사용법 등을 알아보았습니다.

저는 리액트를 처음 배울 때에 함수형 컴포넌트로 배우고 프로젝트나 예제를 만들 때에도 함수형으로밖에 만들어보지 않아서 클래스형 컴포넌트에 대해 잘 알지 못했습니다..

이번 기회를 통해 클래스형 컴포넌트, 라이프 사이클에 대해 정리할 수 있는 계기가 되었습니다.

또 클린업 함수에 대해 정확하게 알고 넘어갈 수 있는 계기가 되어서 앞으로 useEffect 사용할 때 유용할 것 같아요! 😃

그럼 이만.. 총총총

![총총총](https://user-images.githubusercontent.com/80311884/225698792-786e35d0-eb5c-448c-b9d1-1b7a371c0770.gif)