---
title: "[Web] CSR (Client Side Rendering) & SSR (Server Side Rendering)"
excerpt: "CSR과 SSR이 무엇인지.."

categories:
  - Web
tags:
  - [Web, CSR, SSR, Clien-Side-Rendering, Server-Side-Rendering]

permalink: /Web/web-csr-ssr/

toc: true
toc_sticky: true
 
date: 2022-11-08
last_modified_at: 2022-11-08
---
CSR과 SSR의 개념에 대한 포스팅입니다.

***

## ✅ SSR (Server Side Rendering)
### ✔ SSR 이란 무엇인가요?
`SSR`은 **Server Side Rendering**의 약자로, 말 그대로 **서버쪽에서 렌더링 준비를 끝마친 상태로 클라이언트에게 전달**하는 방식입니다.

요청 시 마다 새로고침이 일어나며, **서버에 새로운 페이지에 대한 요청을 하는 방식**으로, **이미 만들어져 있는 DOM**을 받아옵니다.

### ✔ SSR 의 장점
  - **[SEO](#-seo)에 유리**합니다.
  - **초기로딩 성능**이 좋습니다.
        첫 렌더링된 HTML을 클라이언트에서 전달해 주기 때문에 초기로딩 속도를 많이 줄여줍니다.
### ✔ SSR 의 단점
  - 프로젝트가 복잡합니다.
  - 렌더링마다 서버를 거치기 때문에 **속도가 느립니다**.

### ✔ SSR은 어떤 경우에 사용하나요?
- 네트워크가 느릴 때 사용합니다.
네트워크가 느릴 때, 한번에 모든 페이지를 받아오는 CSR보다 각 페이지마다 나누어 받아오는 SSR이 빠를 수 있습니다.
- [SEO](#-seo)가 필요할 때 사용합니다.
- 최초 로딩이 빨라야 하는 사이트를 개발할 때 사용합니다.
- 상호작용이 별로 없는 사이트를 개발할 때 사용합니다.

## ✅ CSR (Client Side Rendering)
### ✔ CSR 이란 무엇인가요?
`CSR`은 **Client Side Rendering**의 약자로, 말 그대로 클라이언트 쪽에서 렌더링을 하는 방식입니다.

즉, 서버는 요청을 받으면 클라이언트에 HTML과 JS를 전달하고, 클라이언트는 전달받은 것으로 렌더링을 시작합니다. 기본 틀만 받고, 브라우저에서 동작으로 DOM을 그립니다.

### ✔ CSR 의 장점
  - 필요한 데이터만 받아오기 때문에 렌더링 속도가 빠릅니다.
  - 첫 로딩만 기다린다면 이후부터는 좋은 UX를 제공합니다.
### ✔ CSR 의 단점
  - 초기 로딩 성능이 느립니다.
  - SEO에 불리합니다. (브라우저에서 빈 화면으로 인식하기 때문)


## 📕 용어 설명
### ✔ SEO
SEO(Search Engine Optimization)는 **검색 엔진 최적화** 라는 말로, 특정 웹 페이지가 검색 결과 상위에 노출 될 수 있도록 하는 작업입니다.

검색 엔진이 이해하기 쉽도록, 기본적으로 특정 검색어를 웹 페이지에 적절히 배치하고 다른 웹 페이지에서 링크가 많이 걸릴 수 있는 등 검색 결과 상위에 노출될 수 있도록 합니다.