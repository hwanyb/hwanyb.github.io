---
title: "[CSS] 포지션 (Position)"
excerpt: "CSS 포지션이란?"

categories:
  - CSS
tags:
  - [CSS, Position]

permalink: /CSS/css-position/

toc: true
toc_sticky: true
 
date: 2022-11-07
last_modified_at: 2022-11-07
---
CSS 포지션에 대한 포스팅입니다.

***

## ✅ CSS에서 Position이 무엇인가요?
`position` 속성은 **문서 상에 요소를 배치하는 방법을 지정**합니다.

## ✅ `Position`속성에는 어떤 값이 있나요?
### ✔ `static` : 요소를 일반적인 문서 흐름에 따라 배치합니다.
### ✔ `relative` : static + 자신을 기준으로 top, right, bottom, left의 값에 따라 [offset](#-offset-오프셋)을 적용합니다.
### ✔ `absolute` : 요소를 일반적인 문서 흐름에서 제거하고, 가장 가까운 위치 지정 부모 요소에 대해 상대적으로 배치합니다.
### ✔ `fixed` : 요소를 일반적인 문서 흐름에서 제거하고, [viewport](#-viewport-뷰포트)의 초기 [containing-block](#-containing-block-컨테이닝-블록)을 기준삼아 배치합니다 => 바뀌지 않는 위치에 지정
### ✔ `sticky` : `static` + `fixed` 특징을 동시에 가집니다.



## 📕 용어 공부
### ✔ Offset (오프셋)
오프셋(offset)이란 `top`, `left`, `right`, `bottom` 값을 의미하고 기준이 되는곳으로부터 얼마만큼 떨어져있는지를 나타내기 위해 필요한 속성입니다.
### ✔ Viewport (뷰포트)
뷰포트(viewport)는 화면에서 실제 내용이 표시되는 영역으로, 데스크톱은 사용자가 설정한 해상도가 뷰포트 영역이 되고, 스마트 기기는 기본으로 설정되어 있는 값이 뷰포트 영역이 됩니다.
### ✔ Containing-block (컨테이닝 블록)
컨테이닝 블록이란 요소의 위치와 크기를 지정하는 데 사용하는 블록을 의미합니다. 상대적인 값이나, 요소의 위치를 지정하는 기준이 필요할 때 사용한다는 의미힙니다.