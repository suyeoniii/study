## Logging

### Request Logging

- API 호출 시 찍히는 로그
- http method, uri, ip, header, content-type, request body, response status code, response body, elasped time 등을 포함할 수 있음

#### 구현 방법

- Filter, Interceptor 등으로 가능
- 주로 Filter로 구현함
- Filter가 가장 바깥 단계이므로, 가장 정확하게 request, response 값을 읽어올 수 있는 장점이 있음
- Interceptor에서 로그를 처리하면, Filter에서 처리하는 로직으로 인해 결과가 다를 수 있음
- 구현 참고자료: https://beaniejoy.tistory.com/97
