## 학습 키워드
- Aggregate Mapping
- Value Object
- JPA 어노테이션
    - @Entity
    - @Table
    - @Id
    - @Embeddable
    - @Embedded

## Aggregate Mapping
* 정의   
부모 엔터티와 자식 엔터티간에 1:1 관계가 있을때 연결 하는 것. 

## Value Object (VO)   
* 정의   
도메인 객체의 일종으로, 도메인에서 한개 또는 그 이상의 속성들을 묶어서 특정 값을 나타내는 객체

* 주의   
equal, hashcode 메서드 재정의 필요 (속성값을 기준으로 동등성을 비교하기 위하여)

## JPA 어노테이션
- @Entity
    * 정의 : 테이블과 일대일로 매칭하는 클래스에 붙여주는 어노테이션   
    * (name : "student") 와 같이 작성해 줌으로써, 테이블의 이름을 생성 
    * 주의
        * 기본 생성자가 꼭 필요
        * final, enum, interface, innter class에서는 사용 불가
        * 필드(변수)를 final로 선언 불가

- @Table
    * 정의 : 엔터티와 매핑할 테이블을 지정
    * (name : "student") 실제 DB에 붙을 테이블명
    * 요약   
    @Entity만 사용하면 자동으로 @Entity + @Table 기능을 수행하고, 따로 사용하면 각자의 설정 값에 따라 작동한다.

- @Id
    * 정의 : 기본키를 부여하는 어노테이션

- @Column
    * 정의 : 객체 필드를 테이블의 컬럼과 매핑

- @Embeddable
    * 여러 속성을 가지는 클래스를 생성후, 알려주는 어노테이션
    * 목적 : JPA Entity안의 Column을 하나의 객체로 사용하고 싶을때 사용 -> 객체지향적 코딩을 가능하게 함
    * 특징 : 생략 가능
- @Embedded
    * 위 Embeddable Class를 타입으로 사용하고자 할때 상단에 알려주는 어노테이션