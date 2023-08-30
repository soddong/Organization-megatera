## 학습 키워드
- 직렬화(Serialization)
- 마샬링
- JSON

## 직렬화 (Serialization)
* 오브젝트를 다른 프로세스에 전달하기 위하여 포맷을 변환하는 것
* Byte stream으로 변환
* 

## 마샬링 (Marchaling)
* 한 객체의 메모리에서 표현방식을 저장 또는 전송에 적합한 다른 데이터 형식으로 변환하는 과정.
* 직렬화보다 더 큰 개념

## JSON
* human-readable text 포맷
* name/value 형태의 쌍으로 collection 타입
* MIME 타입은 application/json
* java에서는 jackson (Web 의존성 추가하여 사용)
* DTO를 사용예로, B/E <-> F/E 간의 json 스키마로서 사용가능. 
* 구조

		{
		"squadName": "Super hero squad",
		"homeTown": "Metro City",
		"formed": 2016,
		"secretBase": "Super tower",
		"active": true,
		"members": [
			{
			"name": "Molecule Man",
			"age": 29,
			"secretIdentity": "Dan Jukes",
			"powers": ["Radiation resistance", "Turning tiny", "Radiation blast"]
			},
			{
			"name": "Madame Uppercut",
			"age": 39,
			"secretIdentity": "Jane Wilson",
			"powers": [
				"Million tonne punch",
				"Damage resistance",
				"Superhuman reflexes"
			]
			},
			{
			"name": "Eternal Flame",
			"age": 1000000,
			"secretIdentity": "Unknown",
			"powers": [
				"Immortality",
				"Heat Immunity",
				"Inferno",
				"Teleportation",
				"Interdimensional travel"
			]
			}
		]
		}