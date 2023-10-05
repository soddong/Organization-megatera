## 학습 키워드
- N + 1 problem
- DDD의 Aggregate
- `CascaseType.ALL`
- `orphanRemoval`
- Event Sourcing
- JPA 어노테이션
    - @OneToMany
    - @JoinColumn

## Relationship Mapping
* 정의 : 객체의 참조 column과 참조 테이블의 외래키를 매핑하는 것
* 특징 : 테이블의 PK를 멤버 변수로 갖지 않고 엔티티 객체 자체를 참조
* 종류
    - @OneToMany
    - @JoinColumn

## N + 1 problem
* 문제 : Entity를 조회(select)할때, 결과로 조회된 데이터 개수만큼 연관관계가 있는 데이터를 추가로 조회하는 쿼리 n개가 발생하는 현상
* 참고 : https://velog.io/@jinyoungchoi95/JPA-%EB%AA%A8%EB%93%A0-N1-%EB%B0%9C%EC%83%9D-%EC%BC%80%EC%9D%B4%EC%8A%A4%EA%B3%BC-%ED%95%B4%EA%B2%B0%EC%B1%85

## DDD의 Aggregate
## `CascaseType.ALL`
## `orphanRemoval`
## Event Sourcing
