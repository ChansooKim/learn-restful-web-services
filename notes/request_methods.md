# Request Methods
***
- **GET** - 리소스의 세부 정보를 조회
- **POST** - 새로운 리소스를 생성
- **PUT** - 기존 리소스를 수정
- **PATCH** - 리소스의 일부를 수정
- **DELETE** - 리소스를 삭제

##### REST API 설계 예시 (SNS 애플리케이션)
Users REST API
1. 전체 유저를 조회
   GET /users
2. 유저를 생성
   POST /users
3. 하나의 유저를 조회
   GET /users/{id} -> /users/1
4. 하나의 유저를 삭제
   DELETE /users/{id} -> /users/1
- Posts REST API
    1. 유저의 모든 게시글을 조회
       GET /users/{id}/posts
    2. 유저의 게시글을 생성
       POST /users/{id}/posts
    3. 게시글의 디테일을 조회
       GET /users/{id}/posts/{post_id}

> 리소스 URL에 복수형을 사용한다.
> -> 복수형을 사용해서 모든 정보를 얻는다는 표현이 직관적이기 때문