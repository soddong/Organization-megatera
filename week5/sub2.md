## 학습 키워드
- DAO(Data Access Object)
- List
- Map

## DAO (Data Access Object)
* 정의    
DB의 Data에 접근하기 위한 객체 (조회, 조작, 삭제 등)
* 사용 이유   
DB 접근을 위한 로직과 비지니스 로직을 분리하기 위함 -> 관심사의 분리
* 아키텍쳐   
    * 3-layered에서 Presentation -> Domain -> Data 중 Data영역의 역할을 수행하는 녀석.

    * MVC 패턴의 Model의 역할
## List   
* 형태 : 배열 형태로 [1, 2, 3 ...] 형태로 데이터가 저장
* 특징 : 순서 유지, 중복 허락

|자료형|설명|
|------|---|
|List|인터페이스|
|ArrayList|클래스|
## Map 
* 형태 : key, value 형태로 데이터가 저장
* 특징 : 순서 유지 x, 중복 허락 x

|자료형|설명|
|------|---|
|Map|인터페이스|
|HashMap|클래스|

## 제너릭
제네릭(Generic)은 클래스 내부에서 지정하는 것이 아닌 외부에서 사용자에 의해 지정되는 것을 의미.
```
List<Integer> list = new ArrayList<Integer>();
Map<String, Integer> map = new HashMap<>();
```

