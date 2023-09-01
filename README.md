# Pe-chesse

## Peach-Market

Peach-Market은 복숭아를 판매하는 온라인 마켓 웹사이트입니다. <br><br>
우리는 복숭아의 매력을 한 눈에 알아볼 수 있게 다양한 복숭아 관련 상품을 제공하고자 합니다.<br><br>
특히, 농부 및 제작자들과 소비자들 사이의 다리 역할을 하며, 이를 통해 지역적으로 생산된 농산물 소비를 장려하고 소비자들에게 더욱 신선하고 다양하고 풍성한 옵션을 제공합니다.

**Peach-Market**과 함께 복숭아의 세계로 떠나보시는 건 어떨까요? 🍑🛒

![Peach-Market](img/Peach_logo.PNG)

## Repo

#### Be

[Peach-Market](https://github.com/Pe-chesse/Peach-Market)

#### Fe

[Peach-Fe](https://github.com/Pe-chesse/Peach-Fe)

## 배포

## 인원구성

- BE/FE 5명

## 기간

- 2023.08.10. ~ 2023. 09. 04.

## Technologies Used

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
  * Amazon S3
  * GitHub
  * Git
  * DBeaver
- ETC
  - Discord
  * Firebase
  - Notion
  - Postman
  - Figma

## ERD (Entity-Relationship Diagram)

[ERD](https://dbdiagram.io/d/64dd90b402bd1c4a5ee8b16b)

## Design

Figma를 통해 디자인을 구성하고 기획했습니다<br>

[Figma](https://www.figma.com/file/j1pxmegC0PiM2HknjA6Jcs/Peach-Market?type=design&node-id=0%3A1&mode=design&t=6nCqFChKDJod4pcd-1)

## API 명세

## account

### 프로필 조회 API

- **URL**: `GET /api/v1/account/profile/`
- **Description**: 사용자의 프로필 정보를 조회하는 API입니다. 파라미터 없이 호출할 경우 본인의 프로필 정보가 반환됩니다. 다른 사용자의 프로필 정보를 조회하려면 `user` 파라미터에 해당 사용자의 닉네임을 전달합니다.
- **Status Code**:
  - 성공 시 -> 200 OK
  - 존재하지 않는 닉네임인 경우 -> 404 Not Found
- **PARAMS**:
  - user (str): 조회할 사용자의 닉네임 (선택적)

**Example Request (본인 정보 조회)**:

- URL: `{{base_url}}/api/v1/account/profile/`
- Status Code: 200 OK

**Example Request (남의 정보 조회)**:

- URL: `{{base_url}}/api/v1/account/profile/?user=목디스크투병중인사람`
- Status Code: 200 OK (성공) / 404 Not Found (존재하지 않는 닉네임인 경우)

### 프로필 수정 API

- **URL**: `PUT /api/v1/account/profile/`
- **Description**: 사용자의 프로필 정보를 수정하는 API입니다. 프로필의 닉네임, 설명, 이미지를 수정할 수 있습니다.
- **Status Code**:
  - 성공 시 -> 201 Created
  - 닉네임 중복 또는 형식 오류 -> 200 OK
  - 기타 오류 -> 400 Bad Request
  - 권한 오류 -> 403 Forbidden
- **AUTHORIZATION**: Bearer Token
- **Body**:
  - formdata
    - nickname (str): 변경할 닉네임 (선택적)
    - description (str): 변경할 설명 (선택적)
    - image_key (str): 변경할 이미지의 키 (선택적)

**Example Request**:

- URL: `{{base_url}}/api/v1/account/profile/`
- Method: PUT
- Status Code: 201 Created (성공) / 200 OK (닉네임 중복 또는 형식 오류) / 400 Bad Request (기타 오류) / 403 Forbidden (권한 오류)
- AUTHORIZATION: Bearer Token (복숭아 마켓 컬렉션)
- Body (formdata):
  - nickname: 소불고기를 먹어 기분 좋은사람 (변경할 닉네임)
  - description: 반갑소 (변경할 설명)
  - image_key: image:bf7079ec2476b71cf66ca7eb0eebfc5d (변경할 이미지의 키)

### 팔로우 정보 조회 API

- **URL**: `GET /api/v1/account/follow/<str:nickname>/`
- **Description**: 사용자의 팔로잉 또는 팔로워 정보를 조회하는 API입니다. `f` 파라미터에 값을 주어 팔로잉 정보를 받아오거나, 값이 주어지지 않으면 팔로워 정보를 받아옵니다.
- **Status Code**: 성공 시 -> 200 OK
- **PARAMS**:
  - f (str): `true` 값을 주면 팔로잉 정보를 받아옵니다. 값이 주어지지 않으면 팔로워 정보를 받아옵니다.
    - true (팔로잉 정보)
    - null (팔로워 정보)

**Example Request**:

- URL: `{{base_url}}/api/v1/account/follow/소불고기를 먹어 기분 좋은사람/?f=true`
- Method: GET
- Status Code: 200 OK (성공)
- PARAMS:
  - f: true (팔로잉 정보)

##### 팔로우 및 언팔로우 API

- **URL**: `POST /api/v1/account/follow/<str:nickname>/`
- **Description**: 해당 사용자를 팔로우하거나 팔로우를 취소하는 API입니다. 한 메소드로 팔로우와 언팔로우를 모두 처리할 수 있습니다.
- **Status Code**:
  - 팔로우 시 -> 201 Created
  - 팔로우 취소 시 -> 204 No Content
- **AUTHORIZATION**: Bearer Token (Bearer Token을 요구하며, 복숭아 마켓 컬렉션의 Bearer Token을 사용합니다.)

**Example Request for Following**:

- URL: `{{base_url}}/api/v1/account/follow/소불고기를 먹어 기분 좋은사람/`
- Method: POST
- Status Code: 201 Created (팔로우 성공)
- AUTHORIZATION: Bearer Token (복숭아 마켓 컬렉션 Bearer Token)
- Request Body: 없음

**Example Request for Unfollowing**:

- URL: `{{base_url}}/api/v1/account/follow/소불고기를 먹어 기분 좋은사람/`
- Method: POST
- Status Code: 204 No Content (언팔로우 성공)
- AUTHORIZATION: Bearer Token (복숭아 마켓 컬렉션 Bearer Token)
- Request Body: 없음

##### 닉네임 사용 가능 여부 확인 API

- **URL**: `GET /api/v1/account/nickname/`
- **Description**: 입력한 닉네임이 이미 사용 중인지 여부를 확인하는 API입니다.
- **Status Code**:
  - 사용 불가능한 경우 -> 200 OK
  - 사용 가능한 경우 -> 204 No Content
- **PARAMS**:
  - `nickname`: 닉네임 값 (닉네임을 확인하려는 경우, 해당 파라미터에 닉네임 값을 넣어서 요청합니다.)

**Example Request for Unavailable Nickname**:

- URL: `{{base_url}}/api/v1/account/nickname/?nickname=소불고기를 먹어 기분 좋은사람`
- Method: GET
- Status Code: 200 OK (사용 불가능한 닉네임)
- Response Body: 없음

**Example Request for Available Nickname**:

- URL: `{{base_url}}/api/v1/account/nickname/?nickname=목디스크투병중인사람`
- Method: GET
- Status Code: 204 No Content (사용 가능한 닉네임)
- Response Body: 없음

##### 사용자 검색 API

- **URL**: `GET /api/v1/account/search/`
- **Description**: 입력한 닉네임 또는 사용자 정보를 검색하여 사용자 목록을 반환하는 API입니다.
- **Status Code**:
  - 검색 결과가 있는 경우 -> 200 OK
  - 검색 결과가 없는 경우 -> 204 No Content
- **PARAMS**:
  - `user`: 검색어 (검색하려는 사용자의 정보 또는 닉네임을 넣어서 요청합니다.)

**Example Request for Search Results**:

- URL: `{{base_url}}/api/v1/account/search/?user=목`
- Method: GET
- Status Code: 200 OK (검색 결과가 있는 경우)
- Response Body: 검색된 사용자 목록 또는 정보

**Example Request for No Search Results**:

- URL: `{{base_url}}/api/v1/account/search/?user=아무나`
- Method: GET
- Status Code: 204 No Content (검색 결과가 없는 경우)
- Response Body: 없음

## bucket

##### 미디어 조회 API

- **URL**: `GET /api/v1/bucket/media/`
- **Description**: 이미지를 조회하기 위한 API로, 이미지의 `key` 값을 쿼리 파라미터로 제공하여 해당 이미지를 반환합니다.
- **Status Code**:
  - 이미지 조회 성공 -> 200 OK
  - 이미지가 존재하지 않는 경우 -> 404 Not Found
- **PARAMS**:
  - `key`: 이미지의 key 값 (예: `image:abcdef123456`)
    - 이미지 업로드 시 생성된 key 값을 넣어주면 해당 이미지를 조회할 수 있습니다.

**Example Request for Image Retrieval**:

- URL: `{{base_url}}/api/v1/bucket/media/?key=image:abcdef123456`
- Method: GET
- Status Code: 200 OK (이미지 조회 성공)
- Response Body: 이미지 파일 또는 이미지에 대한 정보

**Example Request for Non-existent Image**:

- URL: `{{base_url}}/api/v1/bucket/media/?key=image:nonexistent123456`
- Method: GET
- Status Code: 404 Not Found (이미지가 존재하지 않는 경우)
- Response Body: 이미지가 없음

##### 미디어 업로드 API

- **URL**: `POST /api/v1/bucket/media/`
- **Description**: 이미지를 업로드하기 위한 API로, 유저 프로필에 사용되는 이미지는 1개만, 포스트나 프로덕트 등에 사용되는 이미지는 여러 개 업로드할 수 있습니다.
- **Status Code**:
  - 이미지 업로드 성공 -> 201 Created
  - 이미지 업로드 실패 -> 400 Bad Request
- **AUTHORIZATION**:
  - Bearer Token: 복숭아 마켓 컬렉션에서 제공된 Bearer Token 사용
- **PARAMS**:
  - 이미지 파일: 이미지 파일을 formdata 형식으로 업로드
    - 다중 이미지 업로드 가능
    - `image` 필드에 이미지 파일 첨부

**Example Request for Image Upload**:

- URL: `{{base_url}}/api/v1/bucket/media/`
- Method: POST
- Bearer Token: (Bearer Token from 복숭아 마켓 Collection)
- Body: formdata
  - `image` field: 이미지 파일 첨부 (다중 업로드 가능)
- Status Code: 201 Created (이미지 업로드 성공)
- Response Body: 업로드된 이미지의 정보

**Example Request for Failed Image Upload**:

- URL: `{{base_url}}/api/v1/bucket/media/`
- Method: POST
- Bearer Token: (Bearer Token from 복숭아 마켓 Collection)
- Body: formdata
  - Missing `image` field: 이미지 파일을 첨부하지 않음
- Status Code: 400 Bad Request (이미지 업로드 실패)
- Response Body: 업로드 실패에 대한 메시지 또는 에러 정보

## chat

##### 채팅방 생성 API

- **URL**: `POST /api/v1/chat/create/`
- **Description**: 채팅방을 생성하기 위한 API로, 사용자들 간의 채팅방을 만듭니다.
- **Status Code**:
  - 채팅방 생성 성공 -> 200 OK
  - 채팅방 생성 실패 -> 400 Bad Request
- **AUTHORIZATION**:
  - Bearer Token: 복숭아 마켓 컬렉션에서 제공된 Bearer Token 사용
- **PARAMS**:
  - 닉네임: 채팅방 생성 시 사용할 닉네임 입력
    - `nickname` 필드에 닉네임 정보 입력

**Example Request for Creating a Chat Room**:

- URL: `{{base_url}}/api/v1/chat/create/`
- Method: POST
- Bearer Token: (Bearer Token from 복숭아 마켓 Collection)
- Body: formdata
  - `nickname` field: 채팅방 생성 시 사용할 닉네임 정보 입력
- Status Code: 200 OK (채팅방 생성 성공)
- Response Body: 채팅방 생성에 대한 응답 정보

**Example Request for Failed Chat Room Creation**:

- URL: `{{base_url}}/api/v1/chat/create/`
- Method: POST
- Bearer Token: (Bearer Token from 복숭아 마켓 Collection)
- Body: formdata
  - Missing `nickname` field: 채팅방 생성 시 사용할 닉네임 정보를 입력하지 않음
- Status Code: 400 Bad Request (채팅방 생성 실패)
- Response Body: 채팅방 생성 실패에 대한 메시지 또는 에러 정보

##### 채팅 메시지 불러오기 API

- **URL**: `POST /api/v1/chat/load/`
- **Description**: 채팅방에서 메시지를 불러오기 위한 API로, 지정된 채팅방의 메시지를 가져옵니다.
- **Status Code**:
  - 메시지 불러오기 성공 -> 200 OK
  - 더 이상 메시지 없음 -> 204 No Content
  - 권한 오류 -> 403 Forbidden
  - 채팅방을 찾을 수 없음 -> 404 Not Found
- **AUTHORIZATION**:
  - Bearer Token: 복숭아 마켓 컬렉션에서 제공된 Bearer Token 사용
- **Body**:
  - formdata
    - `chat_room` 필드: 메시지를 불러올 채팅방 이름 (str)
    - `num` 필드: 가져올 메시지의 개수 (int)

**Example Request for Loading Chat Messages**:

- URL: `{{base_url}}/api/v1/chat/load/`
- Method: POST
- Bearer Token: (Bearer Token from 복숭아 마켓 Collection)
- Body: formdata
  - `chat_room` field: 메시지를 불러올 채팅방 이름 입력
  - `num` field: 가져올 메시지의 개수 입력
- Status Code: 200 OK (메시지 불러오기 성공)
- Response Body: 불러온 채팅 메시지에 대한 정보

**Example Request when No More Messages**:

- URL: `{{base_url}}/api/v1/chat/load/`
- Method: POST
- Bearer Token: (Bearer Token from 복숭아 마켓 Collection)
- Body: formdata
  - `chat_room` field: 메시지를 불러올 채팅방 이름 입력
  - `num` field: 가져올 메시지의 개수 입력
- Status Code: 204 No Content (더 이상 메시지 없음)
- Response Body: 없음

## post

##### 게시글 목록 조회 API

- **URL**: `GET /api/v1/post/`
- **Description**: 모든 게시글의 목록을 조회하는 API입니다.
- **Status Code**:
  - 조회 성공 -> 200 OK
- **Response Body**: 조회된 게시글 목록에 대한 정보

**Example Request for Retrieving Post List**:

- URL: `{{base_url}}/api/v1/post/`
- Method: GET
- Status Code: 200 OK (조회 성공)
- Response Body: 조회된 게시글 목록에 대한 정보

##### 게시글 작성 API

- **URL**: `POST /api/v1/post/`
- **Description**: 새로운 게시글을 작성하는 API입니다.
- **Status Code**:
  - 작성 성공 -> 201 Created
- **Authorization**: Bearer Token을 사용하여 인증합니다. 이 요청은 복숭아 마켓 컬렉션에서 Bearer Token을 사용합니다.
- **Request Body**: 게시글 작성에 필요한 정보
  - title: 게시글 제목 (문자열)
  - body: 게시글 내용 (문자열)
  - image_keys: 이미지 키 리스트 (문자열)
- **Response Body**: 작성된 게시글의 정보

**Example Request for Posting a New Post**:

- URL: `{{base_url}}/api/v1/post/`
- Method: POST
- Status Code: 201 Created (작성 성공)
- Authorization: Bearer Token (복숭아 마켓 컬렉션에 정의된 Bearer Token 사용)
- Request Body:
  - title: "111"
  - body: "아무 말"
  - image_keys: "image_keys:iist"
- Response Body: 작성된 게시글의 정보

##### 게시글 좋아요 API

- **URL**: `POST /api/v1/post/like/`
- **Description**: 게시글에 좋아요를 추가하거나 제거하는 API입니다.
- **Status Code**:
  - 좋아요 추가 -> 201 Created
  - 좋아요 제거 -> 200 OK
- **Authorization**: Bearer Token을 사용하여 인증합니다. 이 요청은 복숭아 마켓 컬렉션에서 Bearer Token을 사용합니다.
- **Request Body**: 좋아요 추가 또는 제거에 필요한 정보
  - post: 좋아요를 추가 또는 제거할 게시글의 ID (정수)
- **Response Body**: 없음

**Example Request for Adding Like to a Post**:

- URL: `{{base_url}}/api/v1/post/like/`
- Method: POST
- Status Code: 201 Created (좋아요 추가)
- Authorization: Bearer Token (복숭아 마켓 컬렉션에 정의된 Bearer Token 사용)
- Request Body:
  - post: 2 (게시글의 ID)
- Response Body: 없음

**Example Request for Removing Like from a Post**:

- URL: `{{base_url}}/api/v1/post/like/`
- Method: POST
- Status Code: 200 OK (좋아요 제거)
- Authorization: Bearer Token (복숭아 마켓 컬렉션에 정의된 Bearer Token 사용)
- Request Body:
  - post: 2 (게시글의 ID)
- Response Body: 없음

##### 게시글 조회 API

- **URL**: `GET /api/v1/post/<int:post_id>/`
- **Description**: 특정 게시글의 상세 정보를 조회하는 API입니다.
- **Status Code**: 성공 시 200 OK
- **Authorization**: 없음 (인증 무시)
- **URL Parameter**: 조회할 게시글의 ID (정수)
- **Response Body**:
  - id: 게시글의 ID (정수)
  - title: 게시글의 제목 (문자열)
  - body: 게시글의 내용 (문자열)
  - user: 게시글 작성자 정보 (PublicUserSerializer에 정의된 정보)
  - image_keys: 게시글에 첨부된 이미지의 키 (문자열 배열)
  - created_at: 게시글 작성 일시 (날짜 및 시간)
  - updated_at: 게시글 수정 일시 (날짜 및 시간)
  - comment_set: 게시글의 댓글 목록 (CommentViewSerializer에 정의된 정보)
  - like_length: 게시글의 좋아요 수 (정수)
  - is_like: 현재 사용자가 게시글에 좋아요를 했는지 여부 (부울값)

**Example Request**:

- URL: `{{base_url}}/api/v1/post/1/`
- Method: GET
- Status Code: 200 OK
- Response Body:
  - id: 1
  - title: "게시글 제목"
  - body: "게시글 내용입니다."
  - user: { "id": 123, "nickname": "사용자 닉네임" }
  - image_keys: ["image:key1", "image:key2"]
  - created_at: "2023-08-31T12:34:56.789012Z"
  - updated_at: "2023-08-31T12:34:56.789012Z"
  - comment_set: [ { "id": 1, "body": "댓글 내용", "user": { "id": 456, "nickname": "댓글 작성자 닉네임" }, ... }, ... ]
  - like_length: 10
  - is_like: true (사용자가 게시글에 좋아요를 눌렀을 경우)

##### 게시글 작성 API

- **URL**: `POST /api/v1/post/<int:post_id>/`
- **Description**: 특정 게시글에 대한 댓글을 작성하는 API입니다.
- **Status Code**: 성공 시 201 Created
- **Authorization**: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰 사용)
- **URL Parameter**: 작성할 게시글의 ID (정수)
- **Request Body**:
  - body: 작성할 댓글 내용 (문자열)
- **Example Request**:
  - URL: `{{base_url}}/api/v1/post/1/`
  - Method: POST
  - Status Code: 201 Created
  - Authorization: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰)
  - Request Body:
    - body: "23141"
- **Example Response**:
  - Status Code: 201 Created
  - Response Body: 없음 (빈 응답 바디)

##### 게시글 수정 API

- **URL**: `PUT /api/v1/post/<int:post_id>/`
- **Description**: 특정 게시글을 수정하는 API입니다.
- **Status Code**: 성공 시 201 Created
- **Authorization**: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰 사용)
- **URL Parameter**: 수정할 게시글의 ID (정수)
- **Request Body**:
  - title: 수정할 게시글의 제목 (문자열)
  - body: 수정할 게시글의 내용 (문자열)
- **Example Request**:
  - URL: `{{base_url}}/api/v1/post/29/`
  - Method: PUT
  - Status Code: 201 Created
  - Authorization: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰)
  - Request Body:
    - title: "새로운 제목"
    - body: "새로운 내용"
- **Example Response**:
  - Status Code: 201 Created
  - Response Body: 없음 (빈 응답 바디)

##### 게시글 삭제 API

- **URL**: `DELETE /api/v1/post/<int:post_id>/`
- **Description**: 특정 게시글을 삭제하는 API입니다.
- **Status Code**: 성공 시 204 No Content
- **Authorization**: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰 사용)
- **URL Parameter**: 삭제할 게시글의 ID (정수)
- **Example Request**:
  - URL: `{{base_url}}/api/v1/post/29/`
  - Method: DELETE
  - Status Code: 204 No Content
  - Authorization: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰)
- **Example Response**:
  - Status Code: 204 No Content
  - Response Body: 없음 (빈 응답 바디)

##### 대댓글 작성 API

- **URL**: `POST /api/v1/post/comment/<int:comment_id>/`
- **Description**: 특정 댓글에 대댓글을 작성하는 API입니다.
- **Status Code**: 성공 시 201 Created
- **Authorization**: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰 사용)
- **URL Parameter**: 부모 댓글의 ID (정수)
- **Headers**:
  - Authorization: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰)
- **Body**:
  - formdata:
    - body: 대댓글 내용 (문자열)
- **Example Request**:
  - URL: `{{base_url}}/api/v1/post/comment/11/`
  - Method: POST
  - Status Code: 201 Created
  - Headers:
    - Authorization: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰)
  - Body:
    - formdata:
      - body: "123"
- **Example Response**:
  - Status Code: 201 Created
  - Response Body: 없음 (빈 응답 바디)

##### 댓글 수정 API

- **URL**: `PUT /api/v1/post/comment/<int:comment_id>/`
- **Description**: 특정 댓글을 수정하는 API입니다.
- **Status Code**: 성공 시 201 Created
- **Authorization**: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰 사용)
- **URL Parameter**: 수정할 댓글의 ID (정수)
- **Headers**:
  - Authorization: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰)
- **Body**:
  - formdata:
    - body: 수정할 댓글 내용 (문자열)
- **Example Request**:
  - URL: `{{base_url}}/api/v1/post/comment/29/`
  - Method: PUT
  - Status Code: 201 Created
  - Headers:
    - Authorization: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰)
  - Body:
    - formdata:
      - body: "새로운 댓글 내용"
- **Example Response**:
  - Status Code: 201 Created
  - Response Body: 없음 (빈 응답 바디)

##### 댓글 삭제 API

- **URL**: `DELETE /api/v1/post/comment/<int:comment_id>/`
- **Description**: 특정 댓글을 삭제하는 API입니다.
- **Status Code**: 성공 시 204 No Content
- **Authorization**: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰 사용)
- **URL Parameter**: 삭제할 댓글의 ID (정수)
- **Headers**:
  - Authorization: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰)
- **Example Request**:
  - URL: `{{base_url}}/api/v1/post/comment/29/`
  - Method: DELETE
  - Status Code: 204 No Content
  - Headers:
    - Authorization: Bearer Token (복숭아 마켓 컬렉션에서 얻은 토큰)

##### 게시물 검색 API

- **URL**: `GET /api/v1/post/search/`
- **Description**: 게시물을 검색하는 API입니다.
- **Status Code**: 성공 시 200 OK
- **Parameters**:
  - `search_query` (str): 검색할 내용
- **Query Parameter**:
  - search_query: 검색할 내용 (str)
- **Example Request**:
  - URL: `{{base_url}}/api/v1/post/search/?search_query=목디스크`
  - Method: GET
  - Status Code: 200 OK
  - Query Parameter:
    - search_query: 목디스크 (검색할 내용)

## 기능 설명

### 로그인 및 회원가입

##### 로그인

- 사용자 인증을 통해 계정에 로그인하는 기능입니다
- 'ProtectedApiView' 클래스를 통해 사용자의 정보를 확인하고, 해당 정보를 JSON 형식으로 반환합니다

##### 회원가입

- 사용자가 새로운 계정을 생성하는 기능입니다
- 'UserApiView' 클래스의 'put' 메서드를 사용하여 사용자 정보를 수정하고 저장합니다

##### 닉네임 중복 확인

- 회원가입 시 닉네임 중복 여부를 확인하는 기능입니다
- 'NicknameVerifyApiView' 클래스의 'get' 메서드를 사용하여 입력된 닉네임이 이미 다른 사용자의 닉네임과 중복되는 지 확인합니다

### 프로필 수정

- 프로필 페이지에서 사용자 정보를 수정할 수 있습니다
- 'UserApiView' 클래스의 'put' 메서드에서 사용자가 입력한 수정 정보를 처리하고, 해당 정보를 업데이트합니다

### 채팅 기능

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

<!-- ## 기여

만약 Peach-Market 프로젝트에 기여하고 싶다면, 이슈를 제기하거나 Pull Request를 보내주세요 -->

## Contributor

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
