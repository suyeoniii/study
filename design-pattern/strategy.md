## 전략패턴 (Strategy Pattern)

- 객체들이 할 수 있는 행위 각각에 대해 전략 클래스를 생성하고 유사한 행위들을 캡슐화하는 인터페이스를 정의
- 객체의 행위를 동적으로 바꾸고 싶은 경우, 직접 행위를 수정하지 않고 전략을 바꿔주기만 함으로써 행위를 유연하게 확장하는 방법

### 사용하는 이유

- 예를들어 기차, 버스가 있고 기차는 선로, 버스는 도로를 달리도록 move() 함수를 구현하고
- 선로를 달리는 버스가 추가되면 버스 class의 move() 함수를 수정해야함

#### 문제

- OCP 원칙 위배 (기존 move()를 수정하지 않으면서 행위가 수정되어야함)
- 또한, 다른 운송수단도 선로 또는 도로를 달릴 때 각각 move()를 구현해야하는데 코드 중복이 발생함

### 구현 방법

- RailLoadStrategy, LoadStrategy 클래스를 생성하고 move()를 구현
- Client 코드에서 Train, Bus의 부모클래스인 Moving의 setMovableStrategy()를 이용하여 Train, Bus에 해당하는 Strategy를 설정해주면 됨
- 변경 발생 시 Client 코드에서 setMovableStrategy(strategy)의 strategy만 수정해주면 됨
- OCP 문제 해결 및 메소드 중복 문제 해결

예제코드 주소

#### 참고자료

https://victorydntmd.tistory.com/292
