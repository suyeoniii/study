## Call by value, Call by reference

### Call by value (값에 의한 호출)

함수 호출 시 인자로 전달되는 변수의 값을 복사하여 전달
기본 타입은 call by value에 해당

### Call by reference (참조에 의한 호출)

함수 호출 시 인자로 전달되는 변수의 레퍼런스를 전달
함수 안에서 인자의 값이 변경되면 호출 시 받은 변수의 값도 바뀜
객체는 call by reference에 해당

### Java에서의 특징

- Java에서 Call by reference는 해당 객체의 주소값을 직접 넘기는 것이 아닌, 객체를 보는 주소값을 만들어서 넘김
- 메인 함수에서 객체를 만들어서 다른 함수에 전달한다면, 메인에서의 reference 값과 다른 함수가 가지고 있는 reference 값이 다름
  -> 함수에서 받은 객체의 값을 변경하고 싶다면 객체 자체를 변경하면 안되고, 객체의 값을 변경하는 방식으로 할 수 있다.

#### 참고자료

http://dhplanner.blogspot.com/2009/11/java-%EC%97%90%EC%84%9C%EC%9D%98-call-by-value-%EC%99%80-call-by.html
