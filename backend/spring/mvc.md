## Spring의 MVC패턴

### MVC

어플리케이션 구성요소를 Model, View, Controller 세 가지 모듈로 나누어 구분한 패턴이다.

- Model: 어플리케이션의 정보, 데이터, DB 등
- View: 사용자에게 보여지는 화면, UI
- Controller: Model과 View를 연결해주는 역할

### MVC1

![Alt text](https://i.imgur.com/rzhzcZc.png)

View, Controller를 JSP가 담당
구현이 쉽지만 JSP가 View, Controller역할을 모두 담당해서 유지보수에 어려움

### MVC2

![Alt text](https://i.imgur.com/keastvz.png)
표준으로 사용되는 패턴
Controller, View가 분리됨

### Spring Framework의 MVC2패턴

![Alt text](https://i.imgur.com/blr7x6q.png)

1. 프론트 컨트롤러가 클라이언트로부터 오는 모든 요청을 받는다
2. 요청에 맞는 컨트롤러로 요청을 보낸다
3. 처리 결과를 Model에 담아 프론트 컨트롤러로 보낸다
4. 프론트 컨트롤러는 받은 Model을 전달할 알맞은 View에 반영한다
5. View를 응답 결과로 보낸다.

#### 참고자료

https://chanhuiseok.github.io/posts/spring-3/
https://ss-o.tistory.com/160
