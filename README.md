<div align='center' id="top">

# 🍑 Peach-Market 🍑

</div>

<br>

<div aligin='center' id="top">
 
<img width="1000" alt="image" src="https://github.com/Pe-chesse/Pe-chesse/assets/131739526/1b711834-bf25-478e-87a3-226f8d516050">
 
</div>

<br>


```
Peach-Market은 복숭아를 판매하는 온라인 마켓 웹사이트입니다. 
우리는 복숭아의 매력을 한 눈에 알아볼 수 있게 다양한 복숭아 관련 상품을 제공하고자 합니다.
특히, 농부 및 제작자들과 소비자들 사이의 다리 역할을 하며,
이를 통해 지역적으로 생산된 농산물 소비를 장려하고 소비자들에게 더욱 신선하고 다양하고 풍성한 옵션을 제공합니다.
```


<br>
<br>

#### **Peach-Market**과 함께 복숭아의 세계로 떠나보시는 건 어떨까요? 🍑🛒 💨

<br>
<br>

## Pe-chesse 소개 🍑

안녕하세요. 저희는 Pe-chesse 입니다! 
|김민기|김여주|김준균|노희연|정승일|
|:---:|:---:|:---:|:---:|:---:|
<img src="" width="400" style="max-width: 100%;">|<img src="https://github.com/Pe-chesse/Pe-chesse/assets/131739526/95f70448-0045-4c79-af1a-103cb26fd569" width="400" style="max-width: 100%;">|<img src="" width="400" style="max-width: 100%;">|<img src="" width="400" style="max-width: 100%;">|

|<a href="https://github.com/Deeklming">🔗 김민기</a>|<a href="https://github.com/kimyeoju">🔗 김여주</a>|<a href="https://github.com/JayG-5">🔗 김준균</a>|<a href="https://github.com/nohheeyeon">🔗 노희연</a>|<a href="https://github.com/SleepyGom">🔗 정승일</a>|


### 프로젝트 기간

> 2023.08.10 ~ 2023.09.04

<br>

## [목차]
1. [기능](#1-기능)
2. [레포 및 배포 URL](#2-레포-및-배포-URL)
3. [기술스택 및 개발환경](#3-기술스택-및-개발환경)
4. [프로젝트 설계 및 과정](#4-프로젝트-설계-및-과정)
5. [API 명세서](#5-API-명세서)
6. [UI 이미지](#6-UI-이미지)
7. [구현 기능 설명 및 동작](#7-구현-기능-설명-및-동작)
8. [링크](#8-링크)
9. [느낀점](#9-느낀점)

<br>

## 1. 기능

### 1.1 주요 기능
<br>

- 회원가입 및 로그인
- Firebase 사용하여 소셜 로그인(Google)
- 사용자 프로필 CRU
- Follow / Unfollow 기능
- 사용자 검색 기능
- 상품 CRUD
- 사용자 게시글 CRUD
- 게시글 댓글 CRUD 및 대댓글
- 게시글 좋아요 기능
- 사용자 간의 1:1 채팅
- 채팅 실시간 알림 기능


<br>

## 2. 배포 URL 🍑

### 2.1 Back-End
 - http://3.37.239.49/
 - [Peach-Market](https://github.com/Pe-chesse/Peach-Market)

### 2.2 Front-End
- 
- [Peach-Fe](https://github.com/Pe-chesse/Peach-Fe)

<br>

## 3. 기술스택 및 개발환경🍑

### 3.1 Technologies Used
- Programing Languages
  - Python
  - JavaScripts(ES6)
  - HTML5
  - CSS3
- Framework / Library
  - Django
  * Django REST framework
- Database
  - PostgreSQL
  * Redis
  * Entity-Relationship Diagram (ERD)

* Server
  - Amazon Web Services (AWS)

- Tooling / DevOps
  - Docker
  * Firebase
  * Amazon S3
  * GitHub
  * Git
  * DBeaver
- ETC
  - Discord
  - Notion
  - Postman
  - Figma
  

### 3.2 requirment.txt
```txt
﻿anyio==3.7.1
asgiref==3.7.2
attrs==23.1.0
autobahn==23.6.2
Automat==22.10.0
boto3==1.28.36
botocore==1.31.36
CacheControl==0.13.1
cachetools==5.3.1
certifi==2023.7.22
cffi==1.15.1
channels==4.0.0
channels-redis==4.1.0
charset-normalizer==3.2.0
click==8.1.7
colorama==0.4.6
constantly==15.1.0
cryptography==41.0.3
daphne==4.0.0
Django==4.2.4
django-cors-headers==4.2.0
django-environ==0.10.0
django-redis==5.3.0
django-storages==1.13.2
djangorestframework==3.14.0
environ==1.0
firebase-admin==6.2.0
google-api-core==2.11.1
google-api-python-client==2.97.0
google-auth==2.22.0
google-auth-httplib2==0.1.0
google-cloud-core==2.3.3
google-cloud-firestore==2.11.1
google-cloud-storage==2.10.0
google-crc32c==1.5.0
google-resumable-media==2.5.0
googleapis-common-protos==1.60.0
grpcio==1.57.0
grpcio-status==1.57.0
gunicorn==21.2.0
h11==0.14.0
httplib2==0.22.0
httptools==0.6.0
hyperlink==21.0.0
idna==3.4
incremental==22.10.0
jmespath==1.0.1
msgpack==1.0.5
packaging==23.1
Pillow==10.0.0
proto-plus==1.22.3
protobuf==4.24.2
psycopg2-binary==2.9.7
pyasn1==0.5.0
pyasn1-modules==0.3.0
pycparser==2.21
PyJWT==2.8.0
pyOpenSSL==23.2.0
pyparsing==3.1.1
python-dateutil==2.8.2
python-dotenv==1.0.0
pytz==2023.3
PyYAML==6.0.1
redis==5.0.0
requests==2.31.0
rsa==4.9
s3transfer==0.6.2
service-identity==23.1.0
six==1.16.0
sniffio==1.3.0
sqlparse==0.4.4
Twisted==23.8.0
txaio==23.1.1
typing_extensions==4.7.1
tzdata==2023.3
uritemplate==4.1.1
urllib3==1.26.16
uvicorn==0.23.2
watchfiles==0.20.0
websockets==11.0.3
zope.interface==6.0
```

## 4. 프로젝트 설계 및 과정


### 4.1 ERD (Entity-Relationship Diagram)

- [ERD](https://dbdiagram.io/d/64dd90b402bd1c4a5ee8b16b) <br>

<img width="400" alt="ERD" src="https://github.com/Pe-chesse/Pe-chesse/assets/130336617/fec669ae-ca6c-4d8e-aac0-476b47709295">

### 4.2 Architecture

![Architecture](https://github.com/nohheeyeon/nohheeyeon/assets/130336617/ec0470df-a892-4010-8b57-d882fa9c2566)

### 4.3 Design

- [Figma](https://www.figma.com/file/j1pxmegC0PiM2HknjA6Jcs/Peach-Market?type=design&node-id=0%3A1&mode=design&t=6nCqFChKDJod4pcd-1)

<img width="935" alt="image" src="https://github.com/Pe-chesse/Pe-chesse/assets/130336617/54aaa0e2-5af3-43f2-93dc-d021b91eb0e0">

### 4.4 폴더트리

<br>

## 5. API 명세서

- [Peach-Market API 명세서 🍑](https://github.com/Pe-chesse/Pe-chesse/wiki/API-Docs)
- [Postman📮](https://documenter.getpostman.com/view/28078969/2s9Y5YRN6j)

<br>

## 6. UI 이미지


<br>

## 7. 구현 기능 설명 및 동작

### 7.1 로그인 및 회원가입

##### - 회원가입

![signup](https://github.com/nohheeyeon/Algorithm/assets/130336617/310c04b0-9260-433f-9043-ee29663477ca) ![auth_signup](https://github.com/nohheeyeon/Algorithm/assets/130336617/649c7ec5-b6ea-4f33-8e4e-f589a3e7c2a3)

- 사용자가 새로운 계정을 생성하는 기능입니다
- 'UserApiView' 클래스의 'put' 메서드를 사용하여 사용자 정보를 수정하고 저장합니다

##### - 로그인

- 사용자 인증을 통해 계정에 로그인하는 기능입니다
- 'ProtectedApiView' 클래스를 통해 사용자의 정보를 확인하고, 해당 정보를 JSON 형식으로 반환합니다

##### - 닉네임 중복 확인

- 회원가입 시 닉네임 중복 여부를 확인하는 기능입니다
- 'NicknameVerifyApiView' 클래스의 'get' 메서드를 사용하여 입력된 닉네임이 이미 다른 사용자의 닉네임과 중복되는 지 확인합니다

### 프로필 수정

- 프로필 페이지에서 사용자 정보를 수정할 수 있습니다
- 'UserApiView' 클래스의 'put' 메서드에서 사용자가 입력한 수정 정보를 처리하고, 해당 정보를 업데이트합니다

### 채팅 기능

![chat](https://github.com/nohheeyeon/Algorithm/assets/130336617/ed973cbb-c96b-4a6d-8f11-c9fc12a32658)

##### 채팅방 생성 및 접속

- 사용자가 다른 사용자와의 채팅방을 생성하고 접속하는 기능입니다
- 'ChatRoomAPIView' 클래스의 'post' 메서드를 통해 새로운 채팅방을 생성하고, 해당 채팅방에 참여하는 사용자들을 등록합니다
- 채팅방의 이름은 사용자들의 정보를 바탕으로 해싱하여 생성되며, 채팅방은 이미 존재할 경우 해당 채팅방을 사용하고, 없을 경우 새로운 채팅방을 생성합니다

##### 채팅 메세지 조회

- 특정 채팅방의 채팅 메시지를 조회하는 기능입니다
- 'ChatMessageListView' 클래스의 'post' 메서드를 통해 채팅방의 이름과 조회할 메세지의 최대 번호를 입력 받습니다
- 해당 채팅방에 권한이 있는 사용자만 메세지를 조회할 수 있습니다
- 조회한 메시지들은 시간 순으로 정렬하여 최근 메시지부터 최대 30개 까지 반환합니다

### 게시판 및 상품 기능

##### 상품 목록 조회

- 'ProductList' 클래스는 모든 상품을 조회하는 기능을 제공합니다
- 특별한 권한이 필요하지 않으며, 모든 사용자가 접근할 수 있습니다

##### 상품 등록

- 'ProductWrite' 클래스는 새로운 상품을 등록하는 기능을 제공합니다
- 요청한 사용자의 정보를 포함하여 상품 정보를 저장합니다

##### 상품 수정

- 'ProductUpdate' 클래스는 기존의 상품을 수정하는 기능을 제공합니다
- 수정하려는 상품의 정보와 변경할 내용을 요청한 사용자의 정보와 함께 업데이트합니다

##### 상품 삭제

- 'ProductDelete' 클래스는 기존의 상품을 삭제하는 기능을 제공합니다
- 삭제하려는 상품의 정보를 찾아 삭제합니다

##### 상품 상세 조회

- 'ProductDetail' 클래스는 특정 상품의 상세 정보를 조회하는 기능을 제공합니다
- 모든 사용자가 접근할 수 있습니다

##### 게시글 목록 조회 및 작성

- 'PostList' 클래스는 모든 게시글을 조회하고 새로운 게시글을 작성하는 기능을 제공합니다
- 코드 속 'Post' 모델과 관련된 기능들입니다

##### 게시글 수정, 삭제 및 댓글 작성

- 'PostAPIView' 클래스는 게시글의 수정, 삭제와 댓글 작성을 담당하는 기능을 제공합니다
- 사용자는 자신이 작성한 게시글만 수정 및 삭제할 수 있습니다

##### 좋아요

- 'LikeAPIView' 클래스는 게시글에 좋아요를 누르거나 취소하는 기능을 제공합니다

##### 댓글 수정 및 삭제

- 'CommentDetailView' 클래스는 댓글의 수정과 삭제를 처리하는 기능을 제공합니다
- 사용자는 자신이 작성한 댓글만 수정 및 삭제할 수 있습니다

### 검색 기능

##### 사용자 정보 조회

- 사용자의 닉네임을 이용하여 해당 사용자의 정보를 조회합니다
- 'UserApiView' 클래스의 'get' 메서드에 입력된 사용자 닉네임을 통해 해당 사용자를 검색하고, 그 사용자의 정보를 프로필 페이지에 출력합니다

##### 사용자 게시글 조회

- 사용자 프로필 페이지에서는 해당 사용자가 작성한 게시글 목록을 조회할 수 있습니다
- 'Post' 모델과 'PostListSerializer'를 활용하여 사용자가 작성한 게시글들을 조회하고, 이를 프로필 페이지에 출력합니다

## 8. 링크

- [🍑 피치마켓 Notion](https://www.notion.so/peacheese/635598748aa74b6686f765dad4b78339)

<br>

## 9. 느낀점

- 김민기
- 김여주
- 김준균
- 노희연
- 정승일


<!-- ## 기여

만약 Peach-Market 프로젝트에 기여하고 싶다면, 이슈를 제기하거나 Pull Request를 보내주세요 -->

## Contributor🍑

- 김민기 [prin6850@gmail.com]
  - GitHub : https://github.com/Deeklming
- 김여주 [yeojoo0031@gmail.com]
  - GitHub : https://github.com/kimyeoju
- 김준균 [jg55552758@gmail.com]
  - GitHub : https://github.com/JayG-5
- 노희연 [heeyeon1213@gmail.com]
  - GitHub : https://github.com/nohheeyeon
- 정승일 [jungsi1217@gmail.com]
  - GitHub : https://github.com/SleepyGom
