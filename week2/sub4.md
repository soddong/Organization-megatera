## 학습 키워드
* Spring MVC의 annotation
---
| First Header | Second Header |
| ------------ | ------------- |
| @RequestMapping | url or method를 전달받아 Mapping |       
| @GetMapping| GET method 요청시 Mapping |
|@PostMapping| POST method 요청시 Mapping |
|@PatchMapping| PATCH method 요청시 Mapping |
|@DeleteMapping | DELETE method 요청시 Mapping |      
| @PathVariable | url의 경로 중 명시되어 들어오는 인자의 변수를 사용하도록 해줌 |
|@RequestBody| 클라이언트로부터 전달되는 body를 받게 해줌|
|@RequestParam| 위와 동일한 역할을 하지만, 이경우 데이터를 저장하는 이름으로 메서드의 변수명을 설정해줘야 함|
| @ExceptionHandler | Controller계층에서 발생하는 에러를 잡아서 메서드로 처리해주는 기능|
| @ResponseStatus | httpStatus를 표현할수 있음.|