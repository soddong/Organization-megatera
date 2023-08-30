## 학습 키워드
- CORS 란
    - 동일 출처 정책
    - JSONP
    - Access-Control-Allow-Origin
- `@CrossOrigin`

## CORS (Cross-Origin Resource Sharing)

* 브라우저는 보안의 이유로 HTTP 요청들을 제한하는데, 이 때 HTTP 헤더에 허용/제한 에 대한 정보를 실어서 보내는 것.

        HTTP/1.1 200 OK
        Access-Control-Allow-Origin: https://localhost:8080


## 동일 출처 정책 

* 웹 브라우저 보안을 위해 프로토콜, 호스트, 포트가 동일한 서버로만 요청을 주고 받을 수 있도록 한 정책
* 어떤 리소스 요청 (local8080/posts) 얻으려는 이 리소스 출처가 현재 페이지와 다르면 접근할 수 없게한다.
* 두 URL의 호스트와 포트가 같아야 동일한 출처라고 볼 수 있다.

## Access-Control-Allow-Origin

## `@CrossOrigin`