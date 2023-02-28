## POJO

Plain Old Java Object
특정 환경, 기술 등에 종속되지 않는 순수한 자바객체
필요에 따라 재활용될 수 있게 설계된 객체

### POJO 개념 등장 이유

특정 기술을 직접적으로 사용하는 객체를 설계하게되면 객체지향의 장점이 사라짐

### POJO를 유지하면서 어떻게 특정 기술을 사용할까?

Hibernate를 예로들면 Hibernate를 사용하면서 POJO를 유지하기 위해 JPA라는 표준 인터페이스를 정하고 여러 ORM 프레임워크들이 JPA 아래에 구현되어 실행됨
-> 새로운 기술들을 도입하면서도 POJO를 유지할 수 있게됨

#### 참고자료

https://siyoon210.tistory.com/120
