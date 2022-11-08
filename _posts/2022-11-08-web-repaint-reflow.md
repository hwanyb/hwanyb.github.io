---
title: "[Web] Reflow & Repaint"
excerpt: "Reflow & Repaint 무엇인지.."

categories:
  - Web
tags:
  - [Web, Reflow, Repaint]

permalink: /Web/web-repaint-reflow/

toc: true
toc_sticky: true
 
date: 2022-11-08
last_modified_at: 2022-11-08
---
Reflow와 Repaint에 대한 개념을 정리한 포스팅입니다.

***

`Repaint`와 `Reflow`의 개념을 알기 위해서는 [브라우저의 동작원리](https://hwanyb.github.io/Web/web-browser-works)에 대한 이해가 필요합니다.

브라우저의 구성 요소중 하나인 `렌더링엔진`은 요청한 콘텐츠를 표시합니다. 예를들어 HTML을 요청하면 `HTML`과 `CSS`를 파싱하여 화면에 표시합니다.

파이어폭스는 게코(Gecko)엔진을 사용하고, 크롬, 사파리는 웹킷(Webkit) 엔진을 사용합니다.

## ✅ 렌더링엔진 동작과정
![image](https://user-images.githubusercontent.com/80311884/225900049-f49a046a-d776-4804-af37-852dd4bb0031.png)

1. HTML 마크업을 처리하고 `DOM 트리를 빌드`합니다. (**"무엇을"** 그릴지 결정)
2. CSS 마크업을 처리하고 `CSSOM 트리를 빌드`합니다. (**"어떻게"** 그릴지 결정)
3. DOM 및 CSSOM을 결합하여 `렌더 트리`를 빌드합니다. (**"화면에 그려질 것만"** 결정)

렌더링엔진은 위와 같은 과정으로 동작합니다.

![이미지](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F9960C33359A5059D09)

> 웹킷 동작 과정

![이미지](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F9988D33359A5059D1B)

> 게코 동작 과정

위 두 그림에서 보는 것과 같이 웹킷과 게코가 용어를 약간 다르게 사용하고 있지만, 동작과정은 기본적으로 동일합니다.

웹킷은 시각적으로 처리되는 렌더트리를 `렌더트리(render tree)`라는 명칭으로 부르고, 게코는 `프레임트리(frame tree)`라고 부릅니다.
웹킷은 렌더

그리고 웹킷은 요소를 배치하는 것을 `레이아웃(layout)`이라고 부르고, 게코는 이것을 `리플로우(Reflow)`라고 부릅니다.

이제 `리플로우(Reflow)`에 대해 알아보도록 하겠습니다.

## ✅ Reflow 란 무엇인가요?
렌더링 엔진에서 요소를 배치하는 과정을 의미합니다. `렌더 트리 구축`단계에서 DOM트리와 CSSOM 트리를 합쳐 렌더 트리를 만들고 여기에서 reflow를 통해 각각의 요소들의 레이아웃을 위치시킵니다.

여기서 렌더 트리는 DOM요소 기반으로 만들어 지지만, 완전히 대응되지는 않습니다. DOM트리가 문서의 구조를 나타낸다면 렌더 트리는 문서의 시각적 구조를 나타냅니다. 예를들어 스타일에 `display: none` 속성이 있다면 DOM에서는 존재하지만 시각적으로는 없기에 트리에는 할당되지 않습니다.


### ✔ reflow가 발생하는 경우
- DOM 노드의 추가, 제거
- DOM 노드의 위치변경
- DOM 노드의 크기변경 (`margin`, `padding`, `border`, `width`, `height` 등)
- CSS3 애니메이션과 트랜지션
- 폰트 변경, 텍스트 내용 변경
- 이미지 크기 변경
- `offset`, `srollTop`, `scrollLeft와` 같은 계산된 스타일 정보 요청
- 페이지 초기 렌더링
- 윈도우 리사이징

## ✅ Repaint 란 무엇인가요?
**렌더 트리가 탐색되고 paint 메서드가 호출되어 UI기반의 구성요소를 사용해서 그리는 과정입니다.**

repaint가 이루어지기 위해서는 reflow 작업으로 만들어진 렌더트리가 있어야 합니다.

화면의 구조가 변경될 때는 reflow와 repaint가 모두 발생합니다.

repaint가 발생할 때에 항상 reflow가 발생하는 것은 아닙니다. repaint만 발생하는 경우는 레이아웃에 영향을 주지 않는 엘리먼트 개별이 변경되었을 때 입니다.
예를들어 `color`, `background-color`, `visibility` 같은 속성이 있습니다.


## 🔗 참고
- [브라우저는 어떻게 동작하는가?-naver D2](https://d2.naver.com/helloworld/59361)