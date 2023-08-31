## 학습 키워드
- CORS 란
    - 동일 출처 정책
    - JSONP
    - Access-Control-Allow-Origin
- `@CrossOrigin`

## CORS (Cross-Origin Resource Sharing)
* 정의 : 현재 출처가 아닌 다른 도메인에 요청을 보내는 것
* 목적 : SOP로 인해 발생하는 문제를 해결하기 위한 정책
* 방법 : HTTP 헤더에 허용/제한 에 대한 정보를 실어서 보내는 것.

        HTTP/1.1 200 OK
        Access-Control-Allow-Origin: https://localhost:8080
* 동작 과정
    1) Request Header에 Origin을 담아 전송   origin: https://~~

    2) 서버는 Response Header에 Access-Control-Allow-Origin을 담아 클라이언트로 전달   
    access-control-allow-origin : https://~~   
    3) 요청 Origin과 서버 a-c-a-o 비교후, 유효하지 않다면 버림
* 추가   
OPTIONS(HTTP METHOD)에 대한 응답(200 OK)이 온 후, 진짜 요청(PUT)-응답(200 OK)을 주고받게 된다.

## SOP (Same-Origin Policy)
* 정의 : 같은 출처 (Protocol, Host, Port)에서만 리소스를 공유할 수 있다는 정책
* 어떤 리소스 요청 (local8080/posts) 얻으려는 이 리소스 출처가 현재 페이지와 다르면 접근할 수 없게한다.
* 두 URL의 호스트와 포트가 같아야 동일한 출처라고 볼 수 있다.

## Access-Control-Allow-Origin
* Access-Control-Allow-Origin: *   
모든 도메인에서 접근 가능
* Access-Control-Allow-Origin: https://foo.example   
위 도메인에서 접근 가능

## `@CrossOrigin`
* 스프링에서 CORS 정책을 설정해 주는 방법!

        @CrossOrigin(originPatterns = "http://localhost:8080")
        @RestController
        public class SoyController {
        }
        