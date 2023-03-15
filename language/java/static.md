## static

### static

- static 멤버는 클래스 멤버이다
- JVM이 실행되어 클래스가 메모리에 올라갈 때부터 프로그램이 종료될때까지 유지된다
- 클래스가 여러번 생성되어도 static변수는 처음 한 번만 생성됨 (static 영역에 올라감)
- 동일한 클래스의 모든 객체들에 의해 공유됨

### non-static

- 인스턴스 멤버
- 클래스 내에서 선언된 변수
- 객체 생성 시마다 매번 새로운 변수가 생성됨
- 클래스 변수와 달리 공유되지 않음
- 생성될 때마다 stack 영역에 매번 새로 생성됨

### 왜 main 메서드는 반드시 static이어야 할까?

메인 메서드는 프로그램 실행 시 가장 먼저 호출되는 메서드이다.
객체를 생성하지 않은 상태에서 바로 실행되어야 하기 때문에 static이어야함

#### 참고자료

https://sujinhope.github.io/2021/03/03/Java-%ED%81%B4%EB%9E%98%EC%8A%A4%EB%B3%80%EC%88%98,-%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4-%EB%B3%80%EC%88%98-%EC%B0%A8%EC%9D%B4(Static%EB%B3%80%EC%88%98%EC%99%80-Non-Static%EB%B3%80%EC%88%98).html
https://jaehoney.tistory.com/37
