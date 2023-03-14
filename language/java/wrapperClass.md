## Wrapper 클래스

래퍼 클래스는 기본 타입을 객체로 변환해주는 클래스
기본 타입의 데이터를 객체로 취급해야 하는 경우가 있는데, 이 때 래퍼 클래스로 객체로 변환하여 사용할 수 있음

### 종류

기본 타입 / 래퍼 클래스

- byte / Byte
- short / Short
- int / Integer
- long / Long
- float / Float
- double / Double
- char / Character
- boolean / Boolean

### Boxing / UnBoxing

래퍼 클래스는 인스턴스에 저장된 값을 변경할 수 없음
값을 참조하기 위해 새로운 인스턴스를 생성하고, 생성된 인스턴스의 값만 참조 가능

Boxing: 기본 타입 -> 래퍼 클래스
UnBoxing: 래퍼 클래스 -> 기본 타입

#### AutoBoxing / AutoUnBoxing

JDK1.5부터 박싱, 언박싱이 필요한 경우 자바 컴파일러가 자동으로 처리해줌
이를 통해 래퍼 클래스간 연산도 가능해짐

### 주의점

래퍼 클래스도 객체이므로 동등 연산자(==)를 사용하게 되면 두 인스턴스 값이 아닌 주소를 비교하므로, 값을 비교하고 싶은 경우 equals() 메소드를 사용해야함

#### 참고자료

http://www.tcpschool.com/java/java_api_wrapper
