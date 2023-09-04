## 학습 키워드
- 관심사의 분리
- 응집도
- 결합도
- Layered Architecture
- UUID

## 관심사의 분리 (Seperation Of Concerns -- SoC)
* 정의   
각 부문이 각자의 관심사를 갖도록 프로그램을 여러 부문으로 나누는 설계 원칙

* 왜 필요한가   
코드 재사용성, 명료성, 테스트, 유지보수.

* 특징 (또는 장/단점)
응집도는 높이고, 결합도는 낮추는것.
	* 응집도 : 한개의 모듈내에 속한 원소가 얼마나 관련이 있는가.
	* 결합도 : 여러 모듈간의 의존 정도.

## Layered Architecture
* 정의   
소프트웨어 개발시 로직의 관심사(기능)에 따라 계층으로 나누는 아키텍처 -- 관심사의 분리

* 종류
	* 3-Tier Architecture (전통적인 방식 -- 실제로는 더 많은 계층으로 나눠서 사용함)
		1) Presentation (as UI)    		   
		2) Domain (as Business)       
		3) Data   	

	* 4-Tier Architecture
		1) UI Layer
		2) Applcation Layer
		3) Domain Layer
		4) Infrastructure Layer

* 특징
	* 구성하는 계층의 숫자에 따라 N-계층 아키텍처 라고도 함.
	* 각 계층은 어플리케이션 내에서의 역할 / 관심사 별로 구별
	* 상위 레이어는 하위 레이어에 의존, 하위 레이어는 상위 레이어를 모름

* 장점
	* 원하는 계층만 봄으로써, 관심 영역을 줄일 수 있음.
	* 재사용성


## ID 생성
* UUID   
랜덤한 숫자를 생성해주는 것

* ULID   
시간으로 정렬한 랜던함 숫자를 생성해주는 것

* TSID   
TIME 정보를 이용하여 시간으로 정렬한 랜던함 숫자를 생성해주는 것



## 참고
* https://martinfowler.com/bliki/PresentationDomainDataLayering.html
* https://hudi.blog/layered-architecture/
* https://charsyam.wordpress.com/2011/12/04/instagram-%ec%97%90%ec%84%9c-id-%ec%83%a4%eb%94%a9%ed%95%98%ea%b8%b0/