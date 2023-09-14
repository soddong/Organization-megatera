## 학습 키워드
- Spring AOP(Aspect Oriented Programming)
- Dependency Injection
- 싱글턴 패턴
- IoC(Inversion of Control)
- Spring Bean
- BeanFactory
## Spring의 세가지 특징
* IOC
* DI
* AOP   
++ DI가 의존성(new)의 주입이라면, AOP는 기능(logic)의 주입   

## Spring AOP (Aspect Oriented Programming)
* 정의 : 스프링 프레임워크에서 제공하는 기능 중 하나로, 로깅 / 보안 / 트랜잭션 관리 / 예외처리 등과 같은 공통적인 관심사를 모듈화 하는 기술
* 특징
	* 기능을 비지니스 로직 / 공통 모듈로 구분
	* 개발자의 코드 밖에서 필요한 시점에 비지니스 로직에 삽입하여 실행
* 왜 사용하는가? 코드의 중복을 줄이고 유지 보수성을 향상하기 위하여
* 예시

|Annotation|역할|
|----|---|
|@Aspect|AOP로 정의하는 클래스를 지정함|
|@Before|메소드 실행하기 이전|
|@After|메소드가 성공적으로 실행 후|



++ AOP는 OOP를 대신하는 새로운 개념이 아닌, 기존 OOP를 더욱 보완하고 확장하여 OOP를 OOP답게 사용할 수 있도록 도와주는 개념


## Dependency Injection
* 정의 : 프레임워크에 의해 객체의 의존관계 주입되는 설계 패턴   
<img src="image.png" width="1500" height="300">
* 특징
	* Bean 설정 정보를 바탕으로 컨테이너가 자동으로 연결
	* 직접 객체를 생성하지 않고, 외부에서 생성후 주입 시키는 방식 (주입자는 스프링 컨테이너)
	* 쉽게 말해 스프링 컨테이너(IoC)에 있는 Bean(객체)을 가져와 사용하는 방식
* 왜 사용하는가?   
	* 단순한 코드, 낮은 결합도, 높은 유연성, 코드 중복 방지, 유지보수 용이

++ IOC 컨테이너는 DI를 통해 주입시킴. (생성자, 메서드의 setter, 멤버변수에 @Autowired 등을 통해)

## 싱글톤 패턴
* 정의 : 객체의 인스턴스가 오직 1개만 생성되는 패턴. 즉, 데이터를 static으로 선언하여 다른 클래스 간에 공유하는 것.
* 장점
	* 메모리 낭비 방지
	* 속도 향상
	* 데이터 공유가 쉬움
* 단점
	* 멀티스레딩 환경에서 동시성 문제 발생할 수 있음 -> yncronized 키워드를 사용해야 함.
	* 클라이언트가 구체 클래스에 의존 (추상 클래스가 아닌) -> SOLID 원칙 중 DIP 위반.   

++ 스프링 컨테이너는 기존의 싱글톤 패턴의 문제점 해결 -> 객체 인스턴스를 스프링 빈에 등록하여 싱글톤으로 관리   

## IoC(Inversion of Control)
* 정의 : 객체의 호출작업을 개발자가 하는것이 아니라 외부에서 결정하는 것
* 특징
	* 오브젝트(빈)의 생성과 의존 관계 설정, 사용, 제거 등의 작업을 애플리케이션 코드 대신 스프링 컨테이너가 담당 -> 즉, 스프링 컨테이너를 IoC 컨테이너 라고 부름


## BeanFactory
* 정의 : 오브젝트에서 빈의 생성과 관계설정 같은 제어를 담당하는 IoC 오브젝트

## 참고
* https://docs.spring.io/spring-framework/reference/core/aop/introduction-defn.html



