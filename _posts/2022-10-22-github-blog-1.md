---
title: "Github 블로그 만들기 (1)"
excerpt: "Github pages와 jekyll 로 블로그 만들기 대작전"

categories:
  - Github Blog
tags:
  - [Github, Github_Blog]

# permalink: /categories1/post-name-here/ # 포스트 URL

toc: true
toc_sticky: true
 
date: 2022-10-21
last_modified_at: 2022-10-21
---
미미..라고 아시나요?..


![공주미미](https://contents.lotteon.com/itemimage/_v031705/LM/88/04/27/51/04/14/0_/00/1/LM8804275104140_001_1.jpg/dims/resizef/720X720)

공주미미 아니고요.

![미미](https://cdn.ppomppu.co.kr/zboard/data3/2021/0616/20210616091301_pugbeusf.png)

요리왕 비룡 미미도 아니고요.

미룰때까지 미루는 인간.. 미미..😖

개발 공부를 시작한 순간부터 (대략 2년) 미뤄온 숙제를 끝맺어 보려고 블로그를 한번 만드리라 마음을 먹었습니다. 🤦‍♀️

티스토리에도 세네개 글이 있고 벨로그에도 몇개 있고 깃헙에도 노션에도 글이 흩어져 있습니다.

한 플랫폼에 꾸준히 글을 올린다는 것 자체가 정말 대단한 일인 것 같아요..

깃허브 블로그를 만들려고 하는데요, 그 이유는 깃헙블로그는 글 작성과 동시에 잔디도 심어지고 기분이 좋을 것 같그등요..

블로그 만드는 과정 글을 첫 글로 작성하면 좋을 것 같아서 과정을 한번 담아보겠습니다.

그럼.. 한번 시작해 보겠습니다.
***
## 1. 새 Repository 생성
![image](https://user-images.githubusercontent.com/80311884/223146927-3aa1849b-82b2-4d15-8f28-af12cca4bd9e.png)
깃허브에서 New 버튼을 눌러 새 레포를 만들어 줍니다.

## 2. Repository 설정
repository name은 꼭 username.github.io 형식으로 만들어야 합니다!

![image](https://user-images.githubusercontent.com/80311884/223147553-87caa69b-fa51-4979-bc7f-14eeab45a294.png)

![image](https://user-images.githubusercontent.com/80311884/223167333-6dfe2057-c704-4ef7-bee5-d25dc48e3f91.png)

Add a README file 체크 안하셔도 됩니다!

## 3. url 확인
repository 생성 후 username.github.io 주소로 이동하면

![image](https://user-images.githubusercontent.com/80311884/223167180-863f93e9-0b62-42ed-a794-a010d1ff53b1.png)
이렇게 나옵니당.

## 4. git remote
![image](https://user-images.githubusercontent.com/80311884/223148516-418e4732-2a88-4bbb-ad4f-99b869a673a3.png)
Code라고 적힌 초록버튼을 누르면 HTTPS 주소를 복사할 수 있습니다.

원하는 디렉토리에 터미널 혹은 git bash를 켠 후

`git remote add origin 복사한 주소`

명령어를 입력하면 됩니다.

## 5. Ruby & Jekyll 설치
[🔗Ruby, Jekyll 다운로드 참고 링크](https://ogaeng.com/jekyll-blog-install/) 를 참고하여 설치를 합니다.

## 6. Jekyll 생성
빈 폴더여야 jekyll 생성이 가능한것같아요. 해당 디렉토리 내의 README.md를 삭제한 후,

jekyll 설치할때 켰던 cmd 또는 start command prompt with ruby 창에 clone 한 프로젝트 디렉토리로 이동 후 아래 명령어를 입력합니다.

`jekyll new ./`

## 7. 로컬 서버
`bundle exec jekyll serve`

명령어 입력하면 

![image](https://user-images.githubusercontent.com/80311884/223173676-3b3944ee-1f5d-4245-8e43-ca8f6f4c2250.png)
로컬서버가 뜹니다!
localhost:4000 으로 이동하면

![image](https://user-images.githubusercontent.com/80311884/223173916-520ef518-9ffc-49ec-8f61-2be237705d7d.png)
이렇게 뜬답니다!!

## 8. github push
git bash에 아래 명령어를 입력합니다.
```
git add *
git commit -m "커밋메세지"
git push origin
```
push 하고 시간이 조금 흐른 후
usename.github.io 로 이동해 보면은!

![image](https://user-images.githubusercontent.com/80311884/223175928-be89bf5a-2663-4deb-8ab3-3a0fc2ce88f1.png)
이렇게 블로그 화면이 뜹니다!!!!

***
후우 힘든 여정입니다..

다음 글에서는 jekll 테마를 블로그에 적용하는 과정을 담아보도록 하겠습니다!

(- -)(_ _) 꾸벅!☺