# HTTP TCP로 구현하기
그전에 c++로 소켓 구현하는 과정을 포스팅 한적 있다. [참고](https://velog.io/@soddong/%EC%B0%A8%EB%9F%89%ED%86%B5%EC%8B%A0-UDP-TCP-%EC%86%8C%EC%BC%93%ED%86%B5%EC%8B%A0)하자.

Server가 listen을 하고 있고, Client가 Socket Open 후 Connect 해오면 Server와의 연결이 성공 한 것. 이 후 서로 데이터를 주고받을 수 있게 된다.    
하지만 HTTP는 데이터를 주고 받을 수 있는 양방향 프로그램이 아닌, 각각 독립적인 상황을 가정하고 단방향 프로그램을 작성할 것이다.

## Client
--- 
### **1) Connection**
```
Socket socket = new Socket("example.com", 80)
```
위와 같이 host ip를 Socekt의 인자로 전달하면 자동으로 connect를 해준다.

### **2) Request**
```
GET http://example.com/HTTP/1.1        /*Start line*/
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

## Server
--- 


## Java 문법 
--- 
1. unreported exception UnknownHostExeption   
자바에서는 일어날 수 있는 에러에 대한 예외처리가 필요하다. 그렇지 않으면 Compile error가 발생한다. 왜지?   

2. Input / Output  
[[참고](https://velog.io/@soddong/%EC%9E%90%EB%B0%94%EB%A1%9C-%EC%BD%94%ED%85%8C-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0)] 기존에 블로그에 input관련 정리해둔것과 함께 보기
* Output  

    ```
    /* 1. OutputSream 그대로 보내기 */
    OutputStream outputStream = socket.getOutputStream();
    outputStream.write(message.getBytes());
    ```
    OutputStream은 ByteArray로만 보낼 수 있음 -> message를 ByteArray로 변환하여 보내기

    ```
    /* 2. OutputSreamWriter */
    OutputStream outputStream = socket.getOutputStream();
    Writer writer = new OutputStreamWriter(outputStream);

    writer.write(message);
    writer.flush();
    ```
    OutputStreamWriter를 사용하기 위해서는 인자로 outputStream를 넣어주어야 한다.
    return 타입을 다양하게 출력할 수 있도록 인코딩 하기 위해서 통째로 넣어주는듯 하다.

    Writer는 추상화 클래스이고, 문자 기반 출력 스트림의 최상위 클래스이다. 
    OutputStreamWriter 클래스 선언할때 Writer의 상속을 받는 형태이기 때문에 Writer로 받아와도 된다. -> 사실 왜 이렇게 쓰는지, OutputStreamWriter로 받을때랑 어떤 차이가 있는지 와닿지 않는다. 이 부분 공부 필요
    
    위 방식이 Buffer도 존재하며, 효율적으로 동작한다고 한다.

    추가로, 버퍼의 크기를 초과하지 않는한 데이터가 써지지않으므로, flush 해주어야함
* Input

    ```
    1. InputStream
    InputStream inputStream = socket.getInputStream();
    byte[] bytes = new byte[1_000_000];
    int size = inputStream.read(bytes);

    byte[] data = Arrays.copyOf(bytes, size);   /* 사이즈만큼 자르기 */
    String text = new String(data);             /* string으로 변환  */
    ```
    InputStream도 마찬가지로 byteArray로 입력을 받는다. 따라서 임의의 큰배열을 만들어주고, inputStream으로 읽어온다. 이후 사이즈만큼 잘라주고 String으로 변환해준다.

    ```
    2. InputStreamReader
    InputStream inputStream = socket.getInputStream();
    Reader reader = new InputStreamReader(inputStream);
    CharBuffer charBuffer = CharBuffer.allocate(1_000_000);

    reader.read(charBuffer);
    charBuffer.flip();
    String text = charBuffer.toString();
    ```
    reader가 자동으로 크기만큼 잘라주므로, 이방식을 사용할 경우 다시 자를 필요가 없다. 다만, charBuffer로 할당하는 과정에서 문자가 뒤집혀 들어가므로 flip 과정이 필요하다.
    