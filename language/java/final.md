## final 키워드

무언가 제한한다는 의미를 가짐
변수, 메서드, 클래스에 사용할 수 있음

#### 변수

변수에 final을 붙이는 경우 `수정할 수 없음`을 의미
따라서 초기화가 필수임
기본 타입의 경우 변경 불가능하고
객체인 경우 객체 내부 값은 변경 가능하지만, 객체 자체는 변경 불가능

#### 메서드

메서드에 final을 붙이면 override를 제한함
클래스를 상속한 뒤 해당 메서드를 다시 수정(오버라이드)하여 사용할 수 없음

#### 클래스

상속 불가능 클래스
Wrapper class도 여기에 해당함
클래스를 재정의 못하도록 하고싶다면 클래스에 final을 붙이면 됨

#### 참고자료

https://sabarada.tistory.com/148