---
title: "Codepen에서 React 템플릿 사용하기"
excerpt: "온라인 IDE 서비스인 Codepen에서 React 템플릿을 만들고 사용하는 법!"

categories:
  - React
tags:
  - [React, Codepen, IDE]

permalink: /React/react-codepen/

toc: true
toc_sticky: true
 
date: 2022-10-25
last_modified_at: 2022-10-25
---
리액트 프로젝트를 사용하기 위해서는 로컬환경에 node.js를 설치해야하고 프로젝트 폴더를 만들어 npx create-react-app 으로 프로젝트를 만들어 시작을 합니다.

하지만 간단한 예제 연습이나 테스트를 할 때에도 로컬에 프로젝트를 만들어 사용하기에는 비효율적입니다.

온라인 IDE 인 codepen 을 이용하여 간단하게 개발을 할 수 있습니다.

codepen에서 리액트를 프로젝트 템플릿을 만들어 간편하게 사용하는 법에 대해 포스팅해 보겠습니다! 😁
***
## ✅ 1. 코드펜 가입 / 로그인 후 Pen 생성
![image](https://user-images.githubusercontent.com/80311884/225558078-63a275e9-688b-44e1-b042-9ff40d1b0c76.png)

사이드바의 create의 Pen을 클릭하여 새 Pen을 생성합니다.

![image](https://user-images.githubusercontent.com/80311884/225558752-7c669fe4-bc4a-4013-b9ec-c263c575c8c1.png)

Pen이 생성되었으면 우측 상단의 Setting버튼을 클릭합니다.

## ✅ 2. JS Preprocessor 설정
좌측 사이드바에 JS 탭으로 이동합니다.

![image](https://user-images.githubusercontent.com/80311884/225559038-4ab3414f-a05a-44f5-8099-247c323e0a9c.png)

`Javascript Preprocessor`를 Babel로 설정합니다.

## ✅ 3. Add External Scripts/Pens 설정
`Javascript Preprocessor` 하단의 `Add External Scripts/Pens` 검색창에 `react`를 검색하여 `react`와 `react-dom`을 추가합니다.

![image](https://user-images.githubusercontent.com/80311884/225560414-508a05be-1566-4696-94ec-2d1a4df8df95.png)

그럼 두개의 CDN이 추가됩니다!

![image](https://user-images.githubusercontent.com/80311884/225560908-64a5d04d-aac3-4b57-a7c4-868874eab73c.png)

하단의 Save & Close 버튼을 클릭해 설정을 저장합니다.

## ✅ 4. HTML
html 에 `<div id="root"></div>` 를 작성합니다.
![image](https://user-images.githubusercontent.com/80311884/225561597-2516299c-08ba-4d8f-b651-817d92976b34.png)

## ✅ 5. JS
JS에 아래와 같이 작성합니다.
```javascript
const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(
  <div>Hello World!</div>
);
```
![image](https://user-images.githubusercontent.com/80311884/225563398-53c3f1d1-6bae-4e50-85d0-3c76c7e2e913.png)

위와 같이 하단에 라이브 뷰가 나타나게 됩니다.

## ✅ 6. 리액트 템플릿 만들기
해당 Pen을 템플릿으로 저장합니다.
![image](https://user-images.githubusercontent.com/80311884/225564188-1f64232d-57ff-4542-85e2-1403d2fbacd5.png)
우측 상단의 Save 버튼의 화살표를 클릭하면 옵션창이 드롭다운됩니다.

Template 토글을 On하여 Pen을 템플릿으로 저장할 수 있습니다.

Settings의 Template 탭에서도 저장할 수 있으며 Template URL을 복사할 수 있습니다.

## ✅ 7. 리액트 템플릿 사용하기
![image](https://user-images.githubusercontent.com/80311884/225565248-905de813-48fe-40ea-8610-4cbce2ad335c.png)

코드펜 홈화면 우측 사이드바에 Pen > FromTemplate 을 클릭하면 템플릿이 저장되어있습니다.

![image](https://user-images.githubusercontent.com/80311884/225565824-5d13180d-4f34-4418-93f3-cc36ecfff288.png)

템플릿을 오픈할 때 마다 리액트 프로젝트로 새로운 Pen이 생겨 간편하게 코딩할 수 있습니다!
***
코드펜에서 리액트 템플릿을 만들고 사용하는 법에 대해 알아봤습니다!

그럼 이만..총총총