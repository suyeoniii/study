## CORS (Cross-Origin Resource Sharing)

### Cross-origin, Same-origin(SOP)

cross-origin과 same-origin 정책이 있다.
corss-origin정책은 내 홈페이지와 다른 출처의 리소스를 가져올 수 있고, same-origin정책은 동일한 출처의 리소스만 허용한다.
하지만 항상 같은 출처의 리소스만 가져올 수는 없을 것이다. 외부 API등을 이용하려면 다른 출처의 리소스가 필요한데, 이 때 cors설정을 통해 다른 출처의 리소스도 가져올 수 있게 된다.

### 출처 (Origin)

Origin은 protocol + host + port를 말한다.
예를 들어 http://localhost:3000/users?userId=1 에서 origin은 http://localhost:3000 이다.
protocol, host,port가 같으면 같은 출처(origin)로 판단한다.

### CORS 에러는 왜 발생할까?

출처 비교 및 차단은 브라우저에서 이루어진다.
다른 출처에서 리소스를 가져오는 경우, 교차 출처 허용이 명시되어 있지 않으면 브라우저는 차단을 한다.

### CORS 동작

1. 클라이언트에서 http 요청 헤더에 origin을 담아서 요청
2. 서버는 응답 헤더에 Access-Control-Allow-Origin을 담아서 응답
3. 클라이언트에서 내가 보낸 요청의 origin과 허용된 origin을 비교
4. 허용되지 않은 origin인 경우 응답을 버리고, cors 에러 발생
5. 허용된 origin인 경우 리소스를 가져온다.

### 해결방법

CORS에러 해결을 위해서는 서버에서 응답헤더에 `Access-Control-Allow-Origin`에 허용할 origin을 작성해주면 된다.

#### 참고자료

https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-CORS-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC-%ED%95%B4%EA%B2%B0-%EB%B0%A9%EB%B2%95-%F0%9F%91%8F
