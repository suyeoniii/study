## Container

### 스프링 컨테이너란?

자바 객체의 생명 주기를 관리하며, 생성된 자바 객체들에게 추가적인 기능을 제공하는 역할을 합니다
여기서 자바 객체를 빈이라고 부름
개발자가 new 연산자, 인터페이스 호출, 팩토리 호출 방식으로 객체를 생성하고 소멸시킬 수 있는데 이 역할을 대신해줌 (제어 흐름이 외부에 있음)

### 종류

#### BeanFactory

빈을 등록, 생성, 조회하고 돌려주는 빈을 관리하는 역할을 함
getBean() 메소드를 통해 빈을 인스턴스화 할 수 있음

#### ApplicationContext

BeanFactory의 기능을 상속받고 부가 기능을 제공함
주로 ApplicationContext를 사용함

#### 참고자료

https://steady-coding.tistory.com/459
