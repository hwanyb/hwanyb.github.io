---
title: "Github 블로그 만들기 (2)"
excerpt: "Github pages와 jekyll 로 블로그 만들기 대작전"

categories:
  - Github Blog
tags:
  - [Github, Github_Blog, jekll]

permalink: /Github Blog/github-blog-1/

toc: true
toc_sticky: true
 
date: 2022-10-23
last_modified_at: 2022-10-23
---
안녕하세요 😘 (보는 사람 없지만 괜시리 인사해보기)

Github 블로그 만들기 두번째 글입니다!

이번 글에서는 블로그 테마를 적용해 보는 과정을 작성해 보려고 합니다!

잘 봐주세요😁
***
## 1. jekll 테마 선택
jekll 테마는 아래 링크에서 선택할 수 있어요!
- 🔗 [themes.jekyllrc.org](http://themes.jekyllrc.org/)
- 🔗 [jamstackthemes.dev](https://jamstackthemes.dev/ssg/jekyll/)
- 🔗 [jekyllthemes.org](http://jekyllthemes.org/)
- 🔗 [jekyllthemes.io](https://jekyllthemes.io/)
- 🔗 [jekyll-themes.com](https://jekyll-themes.com/)

맨 첫번째에 있는 사이트가 그나마 정렬해서 볼 수 있어서 괜찮은 것 같아요. 저는 가장 인기있는 Minimal Mistakes 로 정했어요.

![image](https://user-images.githubusercontent.com/80311884/223180636-2b9ceeee-a880-4327-a7e1-21214d6bb82a.png)
[🔗 Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes)

## 2. 테마 다운로드
선택한 테마 깃허브 링크로 이동 후 코드 전체 다운로드해주세요.

![image](https://user-images.githubusercontent.com/80311884/223181789-b637cf7a-8e3c-468c-a5f7-e5b45e657325.png)

## 3. 테마 파일 복붙
다운로드받은 후 압축을 풀고 폴더 내 전체 파일을 깃허브 블로그 폴더 내에 붙여넣기 해주세요.

![image](https://user-images.githubusercontent.com/80311884/223182391-6dc21f36-2d56-4f27-9096-6543df2532dc.png)

기존에 있던 파일들과 겹쳐서 이런 창이 뜹니다. 덮어쓰기 해주세요!

## 4. bundle 설치 + 로컬서버
cmd 또는 start command propmt with ruby 창에서 해당 디렉토리로 이동 후 
```
bundle install
```
위 명령어를 입력해 번들을 설치해 주세요.

번들설치가 끝나면
```
bundle exec jekyll serve
```
위 명령어를 입력해 서버를 실행시킵니다.

![image](https://user-images.githubusercontent.com/80311884/223184489-833bd038-bdd0-467a-8bc5-c0800aa651f6.png)

localhost:4000 으로 이동하면 위와 같이 다운로드한 테마로 변경한답니다!

## 5. 블로그 정보 변경
블로그 폴더내의 `_config.yml` 파일을 엽니다.
```
# Site Settings
locale: "ko-KR" #"en-US"
title: "hwanyb Devlog" # 상단 헤더에 보이는 블로그 명
title_separator: "&#124;"
subtitle: # site tagline that appears below site title in masthead
name: "hwanyb" # 블로그 닉네임 설정
description: "this is my blog!" # 블로그 설명
url: "https://hwanyb.github.io" # 블로그 URL
baseurl: # the subpath of your site, e.g. "/blog"
repository: "hwanyb/hwanyb.github.io" # GitHub Repo 이름
teaser: #
```
블로그 정보를 본인의 정보로 바꿔줍니다.
```
# Site Author
author:
  name: "hwanyb" # 블로그 닉네임
  avatar: "/assets/images/avatar.png" # 블로그 프로필 사진
  #   bio              : "hi all!"
  # location         : "Seoul, Korea"
  # email            : "youremailhere@xxxxxx.com"
```
autor 정보와 프로필 정보도 바꿔줍니다.

## 6. 파비콘 변경

파비콘을 바꾸고자 한다면 `assets/imgaes/favicon` 에 파비콘 파일을 넣고

`_layouts/default.html` 의 `head` 부분에 `link`태그를 넣어줍니다.
```
    <link rel="apple-touch-icon" sizes="180x180" href="https://hwanyb.github.io/assets/images/favicon/apple-touch-icon.png">
    <link rel="icon" type="image/png" sizes="32x32" href="https://hwanyb.github.io/assets/images/favicon/favicon-32x32.png">
    <link rel="icon" type="image/png" sizes="16x16" href="https://hwanyb.github.io/assets/images/favicon/favicon-16x16.png">
    <link rel="manifest" href="https://hwanyb.github.io/assets/images/favicon/site.webmanifest">
    <link rel="mask-icon" href="https://hwanyb.github.io/assets/images/favicon/safari-pinned-tab.svg" color="#5bbad5">
    <meta name="msapplication-TileColor" content="#ffc40d">
    <meta name="theme-color" content="#ffffff">
```
## 7. 헤더 네비게이션 변경
`_data/navigation.yml` 파일의 정보를 본인의 정보로 변경해 줍니다.
```
# main links
main:
  - title: "Home"
    url: https://your-blog-url-here/ # 블로그 HOME 바로가기

  - title: "About"
    url: /about/ #_pages/about.md 연결

  - title: "GitHub"
    url: https://github.com/github-account # 깃허브 바로가기 (본인 깃허브로 변경)


  # 카테고리 기능이 필요하면 활성화 하기 (_pages/categories-archive.md 연결)
  # - title: "Categories"
  #   url: /categories/
  ```

## 8. 카테고리 변경
카테고리를 변경할때에는 `_pages/categoried/` 디렉토리 내 md 파일을 수정합니다.
```
title: "Categories1" # 카테고리 이름
layout: category
permalink: /categories/categories1/ # url
author_profile: true
taxonomy: Categories1
sidebar:
nav: "categories"
```
그리고 `_data/navigation.yml` 에 수정한 카테고리를 추가합니다.
```
# sidebar navigation (categories)
categories:
  - title: "Categories1"
    url: /categories/categories1/
  - title: "Categories2"
    url: /categories/categories2/
  - title: "Categories3"
    url: /categories/categories3/
  - title: "Categories4"
    url: /categories/categories4/
```

## 9. 포스트 작성
- 포스트 파일은 `_posts/` 디렉토리 하위에 작성합니다.
- 포스트 파일은 `_posts/YYYY-MM-DD-post-name-here.md` 형식으로 작성합니다.
- 포스트 상단 정보
```
---
title: "[포스팅 예시] 이곳에 제목을 입력하세요"
excerpt: "본문의 주요 내용을 여기에 입력하세요"

categories: # 카테고리 설정
  - categories1
tags: # 포스트 태그
  - [tag1, tag2]

permalink: /categories1/post-name-here/ # 포스트 URL

toc: true # 우측에 본문 목차 네비게이션 생성
toc_sticky: true # 본문 목차 네비게이션 고정 여부

date: 2020-05-21 # 작성 날짜
last_modified_at: 2021-10-09 # 최종 수정 날짜
---
```
- 포스트 내용은 상단 정보 밑에 마크다운 문법으로 작성합니다.
***
이렇게 깃허브 블로그를 만들고 jekll 테마를 적용하고 포스트를 작성하는 법 까지의 과정을 담아보았습니다!

그럼 이만..총총총 ---@