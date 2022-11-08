---
title: "[Web] 브라우저 저장소"
excerpt: "웹 브라우저 저장소의 개념 / 종류 정리"

categories:
  - Web
tags:
  - [Web, Browser-storage, Cookie, WebStorage, LocalStorage, SessionStorage]

permalink: /Web/web-browser-storage/

toc: true
toc_sticky: true
 
date: 2022-11-08
last_modified_at: 2022-11-08
---
웹 브라우저 저장소의 개념과 종류에 대한 포스팅입니다.

***

브라우저 저장소의 종류는 `Cookie`, `WebStorage` 두가지로 나뉘고,

`WebStorage`는 `LocalStorage`와 `SessionStorage`로 나뉩니다.

## ✅ Cookie 란 무엇인가요?
- 웹사이트에서 쿠키를 설정하면, 모든 웹 요청에는 쿠키 정보가 포함됩니다. => **서버 부담 증가**
- 최대 크기: 4KB
- 사용 예시: 팝업창

## ✅ WebStorage란 무엇인가요?
- HTML5 부터 추가된 스펙으로, **웹의 데이터를 클라이언트에 저장할 수 있는 새로운 자료구조** 입니다.
- **key-value 쌍의 구조**로 데이터를 저장하고 key를 기반으로 데이터를 조회할 수 있습니다.
- 쿠키와 달리 **자동 전송의 위험성이 없습니다**.
- 쿠키보다 **큰 저장 용량**을 지원합니다.
    - 모바일: 2.5MB
    - 데스크탑: 5~10MB
- 서버가 **HTTP 헤더를 통해 스토리지 객체를 조작할 수 없습니다**. (웹 스토리지 객체 조작은 JavaScript 내에서만 수행가능합니다.)
- 오직 **문자형**(string) 데이터 타입만 지원
- **로컬 스토리지**(Local Storage)와 **세션 스토리지**(Session Storage)가 있으며, 같은 Storage 객체를 상속하기 때문에 메서드가 동일합니다.

## ✅ localStorage가 무엇인가요?
- 사용자가 데이터를 지우지 않는 이상, 브라우저나 OS를 종료해도, 동일한 브라우저라면 계속 브라우저에 데이터가 남아있습니다. (**영구성**)
- **지속적으로 필요한 데이터** 저장에 사용됩니다. (**자동로그인 등**)

## ✅ sessionStorage가 무엇인가요?
- 데이터가 오리진 뿐만 아니라 브라우저 탭에도 종속되기 때문에, 윈도우나 브라우저 탭을 닫을 경우 제거됩니다.
- **일시적으로 필요한 데이터** 저장 (**일회성 로그인 정보, 입력 폼 저장, 비로그인 장바구니** 등)에 사용됩니다.