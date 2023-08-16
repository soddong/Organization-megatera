## TCP / IP 통신
TCP (Transfer Control Protocol) / IP (Internet Protocol)

3-Layer 와 4-Layer을 합쳐서 일컫는 말 이라고 이해했다.

### TCP와 UDP
전송 계층의 대표적인 프로토콜
* TCP : S<->C간 연결 후 데이터 전달 
* UDP : 일방적으로 데이터 전달

      
### Socket
위 프로토콜은 Socket으로 데이터를 받음으로써 전달이 될수있고,Socket API를 통해 구현할 수 있다.

* Socket : 프로세스 간 통신의 종착점   
* Socket API : 통신에 대한 프로그래밍 하기 위해 사용하는 것


### TCP 통신 순서
Listen -> Connect -> Accept -> Send & Receive -> Close

위 과정을 이제 다음 소챕터에서 구현해 볼 것이다!