## Spring Bean

### Spring Bean이란?

Spring 컨테이너에 의해 관리되는 자바 객체

### Spring Container

스프링 빈의 생명주기를 관리하며, 생성된 스프링 빈에 추가적인 기능을 제공한다.
IoC, DI 원리가 적용됨

### 스프링 빈 등록 방법

1. **Component Scan**
   클래스에 @Component를 명시하면 스프링 컨테이너에 빈을 등록한다.
   @Controller, @Service, #Repository, @Configuration은 @Component를 상속받고 있으므로 컴포넌트 스캔 대상이 됨
2. **빈 설정파일에서 직접 빈 등록**
   빈 설정파일은 XML 또는 자바로 작성할 수 있음

   ```java
   @Configuration
    public class SampleConfiguration {

        @Bean
        public SampleController sampleController() {
            return new SampleController;
        }
    }
   ```

   자바 설정파일에 @Configuration을 붙이고 메서드에 @Bean을 붙이면 반환되는 객체가 빈으로 등록된다.
   \+ @Configuration에도 @Component가 포함되어 컴포넌트 스캔을 하게되며, 그 때 정의된 빈들이 컨테이너에 등록되는 것

### @Component vs @Bean

`@Bean`

- 개발자가 컨트롤 불가능한 외부 라이브러리들을 Bean으로 등록하고 싶은 경우 주로 사용
- 메소드, 어노테이션에 붙일 수 있음

`@Component`

- 개발자가 직접 컨트롤이 가능한 클래스들의 경우 사용됨
- 클래스, 인터페이스에 붙일 수 있음

### @Configuration

```java
@Configuration
public class AppConfig {

    @Bean
    public OrderService orderService() {
        return new OrderServiceImpl(discountPolicy());
    }

    @Bean
    public FixDiscountPolicy discountPolicy() {
        return new FixDiscountPolicy();
    }
}
```

discountPolicy를 2번 호출하여 싱글톤이 깨질 것 같지만 실행해보면 같은 주소를 가지게 된다.
CGLIB이라는 바이트코드 조작 라이브러리를 이용해 AppConfig 클래스를 상속받은 임의의 클래스를 만들고 그 임의의 클래스를 스프링 빈으로 등록하게 된다.
CGLIB라이브러리는 @Bean이 붙은 메소드마다 이미 스프링 빈이 존재하는지 확인하고, 이미 존재한다면 존재하는 빈을 반환하게 되므로 싱글톤이 보장된다.

### 스프링 빈 스코프

빈이 존재할 수 있는 범위

- Singleton
- Prototype
- web
  - request
  - session
  - application
  - websocket

#### Singleton

- 스프링 컨테이너에서 한 번만 생성되고 컨테이너가 사라질 때 제거됨
- 생성된 인스턴스는 Spring Beans Cache에 저장. 해당 빈에 대한 요청과 참조가 있으면 캐시된 객체 반환
- 하나만 생성되므로 동일 참조를 보장함
- 빈 스코프 기본값은 싱글톤임
- 상태가 없는 공유 객체, 읽기 전용으로만 상태를 가진 객체, 쓰기 가능한 상태를 지니면서도 사용 빈도가 매우 높은 객체에 적합 (but 동기화 전략 필요)

##### 생명주기

<img src='/image/singleton-lifecycle.png'>

#### Prototype

- DI가 발생할 때마다 객체가 새로 생성되어 주입됨
- 빈 소멸에 스프링 컨테이너가 관여하지 않고 GC에 의해 제거됨
- 대상 클래스에 `@Scope("prototype")`을 붙이면됨
- 사용할 때마다 상태가 달라져야하는 객체, 쓰기가 가능한 상태가 있는 객체에 적합

##### 생명주기

<img src='/image/prototype-lifecycle.png'>

#### Singleton 빈 vs Prototype 빈

Singleton은 객체가 한번만 생성되고 Prototype은 매번 새로 생성됨
Singleton은 컨테이너가 사라질 때까지 컨테이너에 의해 관리되고, Prototype은 소멸에 컨테이너가 관여하지 않는 차이가 있음

#### 웹 스코프

- 웹 환경에서만 동작하는 스코프
- 특정 주기가 끝날 때까지 관리해줌
- 종류
  - Request - HTTP 요청 하나가 들어오고 나갈 때까지 유지되는 스코프
  - Session - Session과 동일한 생명 주기를 가지는 스코프
  - Application - 서블릿 컨텍스트와 동일한 생명 주기를 가지는 스코프
  - WebSocket - 웹 소켓과 동일한 생명 주기를 가지는 스코프

### Singleton빈은 Thread-Safe할까?

싱글톤이 상태를 갖게 된다면 멀티 스레드 환경에서 동기화 문제가 발생할 수 있다. 상태를 가질 경우 Prototype빈으로 설정하거나 동기화 처리를 따로 해주어야 한다.

#### 참고자료

https://steady-coding.tistory.com/594
