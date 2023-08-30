## 학습 키워드
- Jackson ObjectMapper 란
	* DTO <-> JSON (문자열)
- ObjectMapper
- @JsonProperty

## Jackson ObjectMapper
* Java에서 DTO(데이터) <-> JSON(문자열) 변환하기 위해 사용하는 라이브러리
* Spring에서는 SpringBoot의 web 의존성 추가시, Jackson ObjectMapper 사용 가능

## ObjectMapper
* ObjectMapper를 사용하면 직렬화 / 역직렬화가 가능
* 자바 객체 <-> JSON String / 바이트 배열 로 변환
* ObjectMapper는 생성시 비용이 많이 들기 때문에 Bean이나 static으로 생성해서 재사용 하도록 권장

## @JsonProperty
* JSON 직렬화 시 설정할 수 있는 이름을 지정하는 어노테이션