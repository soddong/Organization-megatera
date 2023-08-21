# 1-4. Java HTTP Server
##
### **Java HTTP Server**
---
* HTTP Server의 high level의 API를 제공해줌 (TLS 등)
* IP address - Port number를 묶어주고, tcp 연결을 listesn
* HttpHandler 객체가 연결이 되어야함 (클라이언트의 요청 처리를 위해) -> 맵핑된 핸들러가 없으면 404 응답
* HttpContext는 HttpServer ~ HttpHandler 사이의 맵핑을 해줌
## 
* 동작 순서   
1) HttpServer 생성 (ip주소와 port를 묶어줌)

    ```
    HttpServer httpServer = HttpServer.create(address, 0);
    ```
2) createContext를 통해 Server의 Handler 생성

    ```
    httpServer.createContext("/", exchange -> {
        ...
    }
    ```
    exchange 자리에 HttpHandler 객체를 넣어주어야 하나, 이 객체는 인터페이스 이므로 Lambda식으로 표현이 가능하다.

3) Handler를 통해 다양한 메서드 접근 가능
##
### **Java NIO**
---
앞서 등장했던 Stream 형식으로 입출력을 다루는 것이 아닌, 채널(Channel)을 통해 입출력을 다룸 -> Stream은 단방향, Channel은 양방향
* 비동기 / non-blocking 방식을 지원
    * Non-Blocking : 프로세스가 중단되지 않음
    * 비동기 : 핸들러에 의해 event시 처리

-> *사실 뭐가 다른건지 와닿지 않는다. 나중에 다시 공부해보기*
    
##

### **Java Lambda Expresttion**
---
메소드를 하나의 식으로 표현한 것
```
(매개변수목록) -> { 함수몸체 }
```
* 하나의 메서드가 선언된 인터페이스의 경우 바꿀 수 있음
* 매개변수가 하나인 경우, 괄호 생략 가능
* return문으로만 이루어지거나 하나의 명령으로 이루어진 경우, 중괄호 생략 가능

```
// before
int min(int x, int y) {

    return x < y ? x : y;

}

// after
(x, y) -> x < y ? x : y;
```