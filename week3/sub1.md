## 학습 키워드

- DTO (Data Transfer Object) 란
    - 프로세스 간 통신(IPC, Inter-Process Communication)
- “무기력한 도메인 모델” 이란 그리고 안티 패턴인 이유
- 자바빈즈(JavaBeans)
- EJB(Enterprise JavaBeans)
- Java의 record
- DAO
- ORM

## DTO (Data Transfer Object)
* 정의 : 프로그램간에 데이터를 교환하기 위해 사용하는 객체
* 장점 : remote 환경에서는 데이터 주고받는것이 비싸므로 DTO를 사용
* 특징
	* 기본 생성자를 가지고 있어야 하며, 로직을 가지지 않는 순수한 데이터 객체(getter, setter)만 가져야 한다. -> Java Bean 의 형태에 가까움
	* 저장, 검색, 직렬화, 역직렬화 로직만을 가져야 한다.
		* 직렬화 : DTO를 byte, json, xml 등의 형태로 변환하는 것 (BE <-> FE)
* 사용
	* java 14 이후에는 record를 활용하여 setter, getter를 반복하는 지루한 작업을 줄임

## IPC (Inter-Process Communication)
* 서로 다른 프로세스간 통신
* 종류
	* file : 파일에 데이터 쓰면 읽는 방식, 원격 환경에서 활용이 어려움
	* socket : 파일과 유사, 원격 환경에서도 활용가능
* RPC (원격 프로시저 호출)을 하기 위해서는 RMI(서로 다른 JVM 상에 있는 객체 메소드 호출 -- 즉, 로컬 객체와 서버 객체를 연결하는 것)
*  B/E, F/E 로 나누면 IPC가 필수적

## “무기력한 도메인 모델” 과 안티 패턴
### 안티 패턴
습관적으로 많이 사용하는 패턴이지만, 성능 등의 측면에서 부정적인 영향을 줄 수 있어 지양하는 패턴.
####
### 무기력한 도메인 모델
* 안티 패턴 중 하나
* 모델 안에서 getter/setter 외에 행동으로 하는 것이 없음
* 즉, 데이터 중심 모델이다 -> 좋지 않은 모델임
## Java Bean
* 자바로 작성된 재사용이 가능한 소프트웨어 컴포넌트
* JSP에서 정보 표현시에 자바빈의 형태를 갖는 클래스를 주로 사용
* 규약
	* 클래스는 직렬화 되어야 함
	* 멤버변수는 property라고 부르며, private으로 선언
	* 외부에서의 접근은 getter, setter로 해야 함
	* 클래스는 필요한 이벤트 처리 메서드들을 포함해야 함
####
## EJB (Enterprise JavaBeans)
* 비즈니스 로직을 가지고 있는 서버 컴포넌트
## DAO (Data Access Object)
* 정의 : DB의 데이터에 접근하기 위한 객체
* 기능 : DB에 직접 접근하여 data를 삽입, 삭제, 조회 등 조작할 수 있는 기능을 수행
## VO (Value Object)
* 정의 : Read-only의 특징을 가져 getter만 가능한 객체
## Java의 record
* 클래스명 앞에 record를 붙이면, 자동으로 인자들 기반의 getter, setter를 생성해줌
* 사용법

		public record Person (String name, String address) {}
* 일반 클래스와의 차이점
	* 레코드는 다른 클래스를 상속 받을 수 없음
	* 레코드에는 인스턴스 필드 선언 불가
	* 레코드를 abstract로 선언 불가, 암묵적으로 final
