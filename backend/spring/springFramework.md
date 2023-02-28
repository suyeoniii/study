## Spring Framework

### Spring Framework란?

자바 플랫폼을 위한 오픈소스 애플리케이션 프레임워크로서 엔터프라이즈급 애플리케이션을 개발하기 위한 모든 기능을 종합적으로 제공하는 경량화된 솔루션
여러 모듈들을 제공하고, 어플리케이션을 구

특징

- 경량 컨테이너
  - 자바 객체를 직접 관리함 객체의 생성, 소멸과 같은 라이프 사이클을 관리하며 스프링으로부터 필요한 객체를 얻어옴
- IoC, DI
  - 구현체를 개발자가 직접 결정하는 것이 아닌, 스프링 내부에서 이루어짐 (IoC)
  - 의존성 주입. 특정 객체가 필요로 하는 객체를 외부에서 결정하여 연결 (DI)
- POJO
  - POJO란 간단한 자바 오브젝트를 말함
  - 특정 규약, 환경에 종속되지 않고 객체지향 설계를 따름
- AOP
  - 횡단 관심사를 비즈니스 로직과 분리하여 중복 코드를 줄이고 비즈니스 로직에 집중할 수 있음
- WAS에 독립적
  - EJB의 경우 무거운 자바 서버 (WAS) 필요했음. 하지만 스프링은 톰캣, 제티 등에서도 잘 동작함

#### Spring MVC

Spring에서 제공하는 웹 모듈
웹 어플리케이션 개발을 쉽게할 수 있도록 도와줌
Model, View, Controller로 구성된다.

- Model - 데이터를 처리해 정제된 데이터를 넣음
- View - 정제된 데이터를 활용해 사용자에세 보여지는 부분
- Controller - HTTP Request 처리 부분

#### Spring Boot

복잡한 설정을 최소화하여 빠르게 개발하고 배포할 수 있는 장점이 있음

특징

- 자주 사용되는 라이브러리들의 버전 관리 자동화
  - 별도의 버전을 명시하지 않아도 현재 스프링부트 버전에 적합한 버전을 가져와줌
  - starter~ 안에 관련 라이브러리들이 들어있음 - web, test, security 등
- AutoConfig로 복잡한 설정 자동화
  - 별도의 수동 설정없이 바로 실행 가능
  - 설정도 application.yml 파일에서 비교적 간단히 가능함
- 내장 웹 서버 제공
  - 톰캣과 같은 별도의 웹서버를 설치할 필요없음
- 독립적 실행 가능
  - war을 외장 웹서버에 배포할 필요없이 jar를 바로 실행할 수 있음

### Spring vs Spring MVC vs Spring Boot 차이

정리하자면 **Spring Framework**는 자바 어플리케이션 구축에 필요한 포괄적인 기능, 모듈을 제공하고
Spring MVC, Spring Boot 둘다 Spring Framework의 모듈이며
**Spring MVC**는 웹 애플리케이션 구축을 위한 구성요소 및 아키텍처를 제공, Spring Framework위에 구축되므로 Spring이 제공하는 기능들을 사용할 수 있음
**Spring Boot**는 Spring의 복잡한 설정들을 자동화하여 빠르게 개발, 배포할 수 있는 프레임워크

#### 참고자료

https://khj93.tistory.com/entry/Spring-Spring-Framework%EB%9E%80-%EA%B8%B0%EB%B3%B8-%EA%B0%9C%EB%85%90-%ED%95%B5%EC%8B%AC-%EC%A0%95%EB%A6%AC
https://steady-coding.tistory.com/457
https://mangkyu.tistory.com/208
https://kotlinworld.com/326
