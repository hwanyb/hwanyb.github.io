---
title: "React 컴포넌트(1) - 클래스형 컴포넌트"
excerpt: "리액트 컴포넌트에 대한 기초를 다시 다지기 위한 포스팅!"

categories:
  - React
tags:
  - [React, Component, ClassComponent, LifeCycle]

permalink: /React/react-component-1/

toc: true
toc_sticky: true
 
date: 2022-10-31
last_modified_at: 2022-11-03
---
리액트 컴포넌트에 대한 기초를 다시 다지기 위한 포스팅!

생활코딩의 **React class vs function style coding** 강의를 참고하여 작성하였습니다.

강의 링크 : [React class vs function style coding](https://inf.run/NgAx)

***

React 컴포넌트는 **클래스형 컴포넌트**, **함수형 컴포넌트** 이 2가지 방식으로 만들 수 있습니다.

과거에는 클래스형 컴포넌트를 많이 사용했습니다.

과거 함수형 컴포넌트는 컴포넌트 내부에 `state`를 만들어 사용하는 것이 불가능했고, 컴포넌트의 생성, 변경, 소멸 이벤트인 `life cycle API`를 사용하는 것이 불가능했습니다.

하지만 2019년 v16.8 부터 함수형 컴포넌트에 `hook`이 지원되기 시작하면서 내부적으로 `state`를 만들어 다룰 수 있고, `life cycle`에 따라 해야할 작업들을 정의할 수 있게 되었습니다.

현재는 공식문서에서도 함수형 컴포넌트와 hook을 함께 사용할 것을 권장하고 있습니다.

그래도 클래스방식과 컴포넌트방식의 차이점을 알아야 하고 필요에 따라 두가지 방식을 이용할 수 있어야 합니다.

클래스형 컴포넌트와 함수형 컴포넌트의 차이와 `state`, `life cycle`에 대해 정리해 보는 시간을 갖겠습니다!


## ✅ **클래스형 컴포넌트에서의 `props`사용법**

부모 컴포넌트인 `App.js`에서 `ClassComp`라는 컴포넌트에 `props`로 `initNum`을 전달해 보겠습니다.

1. **`render()`메소드에서 `props` 사용하기**
    ```javascript
    function App() {
        return (
            <div>
                <h1>Hello World!</h1>
                <ClassComp initNum={2}></ClassComp>
            </div>
        )
    }

    class ClassComp extends React.Component{
        render() {
            return (
                <div>
                    <h2>Class Component</h2>
                    <p>Number : {this.props.initNum}</p>
                </div>
            )
        }
    }
    ```
    `render()` 메소드 내에서 `this.props`를 통해 전달된 props를 사용할 수 있습니다. 

    위 컴포넌트는 `render()`메소드에서 `this.props`를 기본적으로 제공하는 `React.Component` 클래스를 상속받았습니다.

    따라서 `constructor()` 메소드에서 `props`를 호출하지 않아도 `render()`메소드에서 `this.props`를  바로 사용할 수 있습니다.

2. **`constructor()`메소드에서 `props` 사용하기**
    ```javascript
    function App() {
        return (
            <div>
                <h1>Hello World!</h1>
                <ClassComp initNum={2}></ClassComp>
            </div>
        )
    }

    class ClassComp extends React.Component{
        constructor(props) {
            super(props);
        }
        render() {
            return (
                <div>
                    <h2>Class Component</h2>
                    <p>Number : {this.props.initNum}</p>
                </div>
            )
        }
    }
    ``` 
    `constructor()` 메소드는 클래스형 컴포넌트가 만들어질 때 호출되는 생성자 메소드입니다. `super()`는 부모클래스의 생성자 메소드를 호출하는 것으로, 부모 클래스의 생성자 메소드를 호출하지 않으면 `this.props`를 사용할 수 없습니다. (위 코드에서 ClassComp의 부모 컴포넌트는 React.Coponent 입니다.)

3. **클래스필드(Class Field)에서 `props` 사용하기**
    ```javascript
    function App() {
        return (
            <div>
                <h1>Hello World!</h1>
                <ClassComp initNum={2}></ClassComp>
            </div>
        )
    }

    class ClassComp extends React.Component{
        number = this.props.initNum;
        render() {
            return (
                <div>
                    <h2>Class Component</h2>
                    <p>Number : {this.number}</p>
                </div>
            )
        }
    }
    ```
    **클래스필드**(Class Field)란 클래스의 인스턴수 변수를 선언하는 방법 중 하나입니다.
    
    클래스 필드를 사용하면 클래스 생성자(`constructor`)에서 필드를 정의할 필요 없이 클래스 내부에서 바로 변수를 선언하고 사용할 수 있습니다.

    클래스 필드는 클래스 외부에서 선언된 변수와는 달리, 클래스 내부에서만 사용할 수 있는 변수입니다. 따라서 클래스 필드를 참조하려면 `this` 키워드를 사용해야 합니다.

    ES2015(ES6)에서는 클래스 필드를 지원하지 않았지만, 최신 버전의 자바스크립트(ES2019, ES2020)에서는 클래스 필드를 지원합니다.


## ✅ **클래스형 컴포넌트에서의 `state`사용법**

1. `constructor()` 메서드 내에서 `props` 값을 `state`로 할당하기
    ```javascript
    function App() {
            return (
                <div>
                    <h1>Hello World!</h1>
                    <ClassComp initNum={2}></ClassComp>
                </div>
            )
        }

        class ClassComp extends React.Component{
            constructor(props) {
                super(props);
                this.state = { number: this.props.initNum }
            }
            render() {
                return (
                    <div>
                        <h2>Class Component</h2>
                        <p>Number : {this.state.number}</p>
                    </div>
                )
            }
        }
    ```

2. `getDerivedStateFromProps()` 정적 메서드를 사용하여 `props` 값을 `state`로 업데이트하기

    ```javascript
    function App() {
            return (
                <div>
                    <h1>Hello World!</h1>
                    <ClassComp initNum={2}></ClassComp>
                </div>
            )
        }

        class ClassComp extends React.Component{
            static getDerivedStateFromProps(props, state) {
                if (props.initNum !== state.initNum) {
      return { number: props.initNum };
    }
    return null;
            }
            render() {
                return (
                    <div>
                        <h2>Class Component</h2>
                        <p>Number : {this.state.number}</p>
                    </div>
                )
            }
        }
    ```

3. **클래스필드(Class Field)에서 `props` 값을 `state`에 할당하기**
```javascript
function App() {
        return (
            <div>
                <h1>Hello World!</h1>
                <ClassComp initNum={2}></ClassComp>
            </div>
        )
    }

    class ClassComp extends React.Component{
        state = {
            number: this.props.initNum
        };
        render() {
            return (
                <div>
                    <h2>Class Component</h2>
                    <p>Number : {this.state.number}</p>
                </div>
            )
        }
    }
```
위와 같이 App컴포넌트에서 전달한 `initNum`을 `state`객체를 사용하여 저장할 수 있습니다.

## ✅ **클래스형 컴포넌트에서 state값 변경하는 법**

```javascript
function App() {
        return (
            <div className="container">
                <h1>Hello World!</h1>
                <ClassComp initNum={2}></ClassComp>
            </div>
        )
    }

    class ClassComp extends React.Component{
        state = {
            number: this.props.initNum
        };
        render() {
            return (
                <div className="container">
                    <h2>Class Component</h2>
                    <p>Number : {this.state.number}</p>
                    <input
                      type="button"
                      value="random"
                      onClick={() => this.setState({ number: Math.random() }).bind(this)}
                    />
                </div>
            )
        }
    }
```

![image](https://user-images.githubusercontent.com/80311884/225573897-8ad6cee9-74fb-416b-9488-e4b0c9c2f86d.png)

현재 위와 같은 화면이 렌더링됩니다.

컴포넌트들의 최상위 `element`에 `container`라는 `className`을 부여하고 스타일을 적용하였습니다.

랜덤 버튼을 추가하고, 클릭시 `number`가 무작위수로 변경되는 이벤트를 추가하였습니다.

`state`로 저장한 `number` 를 변경하기 위해서는 `this.setState()`를 호출해야 합니다. `this.setState()`함수는 객체나 함수의 인자를 받을 수 있습니다.

또한, `setState` 함수에서는 `this`를 사용하여 컴포넌트의 인스턴스를 가리키는 방법도 있습니다. 이 때, `this` 바인딩을 해주기 위해 `bind`함수를 사용할 수 있습니다.


## ✅ **클래스형 컴포넌트에서의 라이프사이클**
제가 참고한 인프런 강의는 2020년 2월에 게시되어서 현재 버전에서 권장하는 라이프사이클 메소드 사용법과 조금 상이합니다.

이 부분은 리액트 공식문서 내용을 참고하여 작성하겠습니다.

라이프사이클 메소드는 컴포넌트가 브라우저상에 나타나고, 업데이트되고, 사라지게 될 때 호출되는 메소드들입니다.

라이프사이클 메소드는 클래스형 컴포넌트에서만 사용할 수 있습니다.

![image](https://user-images.githubusercontent.com/80311884/225583970-a8889cd8-0098-437f-b7e8-69674d48b8ac.png)
> 이미지 출처 : [리액트 공식문서](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

### ✔ **마운트 (Mount)**
리액트에서 마운트란 DOM객체가 생성되고 브라우저에 나타나는 것을 의미합니다.

컴포넌트가 마운트될 때 호출돠는 메소드는 다음과 같습니다.
- **constructor**

    **생성자 메소드**로 컴포넌트가 만들어지면 **가장 먼저 실행되는 메소드**입니다.
- getDerivedStateFromProps

    `props`로 받아온 것을 `state`로 저장하고자 할 때 사용할 수 있는 메소드입니다.

    다른 생명주기 메서드와는 달리 앞에 `static` 을 필요로 하고, 이 안에서는 `this` 를 조회 할 수 없습니다. 여기서 특정 객체를 반환하게 되면 해당 객체 안에 있는 내용들이 컴포넌트의 `state` 로 설정이 됩니다. 반면 `null` 을 반환하게 되면 아무 일도 발생하지 않습니다.

    참고로 이 메서드는 컴포넌트가 처음 렌더링 되기 전에도 호출 되고, 그 이후 리렌더링 되기 전에도 매번 실행됩니다.
- **render**

    컴포넌트를 렌더링하는 메서드입니다.
- **componentDidMount**

    컴포넌트의 첫번째 렌더링이 마치고 나면 호출되는 메서드입니다.


### ✔ **업데이트 (Update)**
컴포넌트가 업데이트 되는 시점에 호출되는 메소드는 다음과 같습니다.

- getDerivedStateFromProps

    마운트되는 시점에도 발생하는 메소드로 컴포넌트의 `props`나 state가 변경되었을 때도 이 메소드가 호출됩니다.
- shouldComponentUpdate

    컴포넌트가 리렌더링할지 말지 결정하는 메소드입니다.
    
    주로 성능 최적화를 위해 사용되며 `props` 또는 `state`가 새로운 값으로 갱신되어서 렌더링되기 직전에 호출됩니다.
- **render**
- getSnapshotBeforeUpdate

    가장 마지막으로 렌더링된 결과가 DOM 등에 반영되기 전에 호출됩니다. 이 메서드를 사용하면 컴포넌트가 DOM으로부터 스크롤 위치 등과 같은 정보를 이후 변경되기 전에 얻을 수 있습니다. 이 생명주기 메서드가 반환하는 값은 `componentDidUpdate()`에 인자로 전달됩니다.
- **componentDidUpdate**

    갱신이 일어난 직후에 호출됩니다. 이 메서드는 최초 렌더링에서는 호출되지 않습니다.

### ✔ **언마운트 (Unmount)**
리액트에서 언마운트는 컴포넌트가 화면에서 사라지는 것을 의미합니다. 

언마운트 시점에 호출되는 메소드는 `componentWillUnmount`가 있습니다.
- **componentWillUnmount**

    컴포넌트가 화면에서 사라지기 직전에 호출되는 메소드입니다.

    여기서는 주로 DOM에 직접 등록했었던 이벤트를 제거하고, 만약에 setTimeout 을 걸은것이 있다면 clearTimeout 을 통하여 제거를 합니다. 추가적으로, 외부 라이브러리를 사용한게 있고 해당 라이브러리에 dispose 기능이 있다면 여기서 호출해주시면 됩니다.

***

이번 포스팅은 클래스형 컴포넌트에서의 `props` 사용법, `state` 사용법, `state` 변경법, `life cycle` 메소드에 대해 작성했습니다.

다음 포스팅에서는 함수형 컴포넌트에서의 `props` 사용법, `state` 사용법, `state` 변경법, `life cycle` 구현 에 대해 알아보겠습니다.

그럼 이만..총총총

![i15928796274](https://user-images.githubusercontent.com/80311884/225607989-d6bbdd7c-c505-458b-8b34-79e533b87e6e.gif)