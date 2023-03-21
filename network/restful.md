## REST, RESTful

Representational State Transfer
자원을 이름으로 구분해 해당 자원의 상태를 주고 받는 것

### REST

자원에 대해 CRUD 연산을 수행하기 위해 URI(Resource)로 GET, POST 등의 방식(Method)을 사용하여 요청을 보내며, 요청을 위한 자원을 특정 형태로 표현된다.

- 자원 - URI
- 행위 - Method(GET, POST, PUT, PATCH, DELETE)
- 표현 - 데이터 형태(JSON, XML, TEXT 등)

### REST API

- REST 특징을 기반으로 API를 구현한 것
- 각 요청이 어떤 동작, 정보를 위한 것인지 요청 모습 자체로 추론 가능

#### 설계 규칙

- URI는 정보의 자원을 표현
- URI는 명사 사용
- 자원에 대한 행위는 Method로 표현 (URI로 표현X)
- 슬래시로 계층 관계 표현
- 마지막 문자로 슬래시 포함 x
- 언더바(\_) 대신 하이픈(-)
- URI는 소문자로 구성
- 파일 확장자 포함하지 않음
- HTTP 응답 상태 코드 사용

### RESTful API

REST 설계 규칙을 잘 지켜 설계된 API

#### 참고자료

https://dev-coco.tistory.com/97
