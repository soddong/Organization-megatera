# HTTP Server

---

### **Client (Class Socket)**
---
Socket Class는 소켓 클라이언트로, 서버에 연결을 요청하고 데이터를 전송하는 기능을 담는다. 
### **1) Connection**
```
Socket socket = new Socket("example.com", 80)
```
위와 같이 host ip를 Socekt의 인자로 전달하면 자동으로 connect를 해준다.

### **2) Request**
```
GET http://example.com/HTTP/1.1      ㅉ  /*Start line*/
(빈 줄)
```

위 Start line을 해석해보면 다음과 같다.     
* **GET** (http 메서드 중, get 메서드를 사용 -- 페이지를 read)
* **http** (http 프로토콜을 사용)  
* **example.com** (이 도메인에 쓸 것)
* **HTTTP/1.1** (통신 방식은 HTTP 1.1 버전)

혹은

```
GET /HTTP/1.1                         /*Start line*/
Host: example.com                     /*  Header  */
(빈 줄)
```

위가 더 보편적으로 많이 사용하는 방식이라고 한다. Domain을 따로 정의해준 것 빼고는 차이는 없다.

**이제, 위 명령을 Server에 Write 해주어야 한다.**

```
OutputStream outputStream = socket.getOutputStream();
Writer writer = new OutputStreamWriter(outputStream);

writer.write(message);
writer.flush();

System.out.println("request");
```
writer를 통해 message를 Server로 보낸셈이다.

### **3) Response**
```
InputStream inputStream = socket.getInputStream();
byte[] bytes = new byte[1_000_000];
int size = inputStream.read(bytes);

byte[] data = Arrays.copyOf(bytes, size);
String text = new String(data);

System.out.println("response");
```
text에 Server의 응답이 저장된다.

### **4) Close**
```
try(Socket socket = new Socket("example.com", 80)) {
    ...
}
```
위와 같이 사용하면, close 메서드를 명시할 필요가 없다. try 블록이 완료되면 자동으로 close 메서드 호출이 된다.     

** 참고! try문 없이 close문 메서드를 명시하지 않아도, GC가 자동으로 제거해준다. 다만, 언제 제거될지는 모름 **

### **Server (Class ServerSocket)**
ServerSocket Class는 서버용 소켓으로, 포트를 통해 클라이언트의 연결을 기다리고 데이터를 주고받는 기능을 담는다. 

### **1) Listen**
```
ServerSocket listener = new ServerSocket(8080, 0);
```
ServerSocket을 생성하면, 클라이언트로부터 연결을 기다리는 상태가 된다.
- port_num : 포트 넘버
- backlog : 연결요청을 대기하는 큐의 크기

### **2) Accept (About Connect)**
```
Socket socket = listener.accept();
```
기중인 클라이언트의 요청을 차례로 수락함으로써 데이터를 주고받을 수 있게 된다.

그 후, Request -> Response에 대한 처리는 클라이언트와 동일하다.


## **Blocking vs Non-Blocking**
---
* Blocking   

    요청을 하고 응답을 대기하는 함수를 호출할 때 스레드에서 발생하는 대기 현상.

    즉, 스레드는 Wait 상태.

    ServerSocket의 Listen 상태에서 클라이언트의 Connection이 들어올때가지 다음 작업이 진행되지 않는 상태를 Blocking 상태라고 한다.


* Non-Blocking

    스레드를 block 시키지 않고 요청에 대한 현재상태를 즉시 리턴한다.