## 학습 키워드
- Collection Pattern
- CQS(CQRS까진 안 가셔도 됩니다. 추후에 다뤄요)
###
## 1) Collection Pattern
Rest API에서는 Collection Pattern을 따름
####
* Collection   
여러 리소스를 하나의 그룹으로 묶어 표현

        * 1. not collection
        /the-first-post
        /the-second-post

        * 2. collection
        /posts -> 복수형으로 모든 게시물을 URI로 표현
        /posts/first-post
        /posts/secode-post
####     
* 일반적 형태 -- Post ID   
/posts/{id} 또는 /post/:id

    (URI/URL -- resource ID)
####
* 사용 예시

        특정 게시물에 댓글 달기   

        * case1
        /posts/{post_id}/comments : collections
        /post/{post_id}/comments/{id} : element
        
        * case2
        /comments?post_id={post_id}

        case2의 경우, post_id를 이용해 필터링 한다는 의미

        ---

        게시물을 고치는 페이지 표현하기 (사용 권장 x)

        * case1
        /posts/{post_id}/edit

        * case2
        /edit?post_id={post_id}
####
* 페이지를 표현하는 방식은 사용하지 않는것 권장. -> F/E단의 역할 -> 사용하고 싶다면, pages라는 Document 사용     
####
* 그룹이 아닌경우, 단수만 (session 등)
###
## 2) CRUD
### 대표적인 기능
* Create -- GET
* Read -- POST
* Update -- PUT, PATCH
* Delete  -- DELETE
####
### HTTP로 CRUD 작성하기

        GET /comments -> 전체 댓글 목록
        GET /comments?post_id={post_id} -> 특정 게시물에 대한 댓글 목록
        GET /comments/{id} -> 댓글 상세
        POST /comments?post_id={post_id} -> 특정 게시물에 대한 댓글 생성
        PUT /comments/{id} -> 댓글 수정

        POST /session -> 세션 생성 (로그인)
        DELETE /session -> 세션 파괴 (로그아웃)
###
## 3) CQS
CRUD를 특징에 따라 구분하는 것 (Command - Query)
* Command   
Create, Update, Delete : 상태가 변함 (안전 x)

* Query   
Read : 상태가 변하지 않음 (안전 o, 분산, 캐시 등이 안전)
###
