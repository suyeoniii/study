## Generic

클래스 내부가 아닌, 외부에서 사용자에 의해 타입이 지정되는 것
제너릭에는 기본타입을 넣을 수 없고 Object를 상속한 값(Integer 등)만 넣을 수 있다.

```java
class MyArray<T> {

    T element;
    void setElement(T element) { this.element = element; }
    T getElement() { return element; }

}
```

### C++의 template과 차이점

- C++의 경우 기본 타입도 넣을 수 있다.
- C++은 컴파일 시간에 템플릿에 들어갈 타입을 알 수 있고, 자바의 경우 컴파일 후 실행 전까지 제너릭타입에 어떤 값이 들어갈지 모름
- Java에서는 Generic으로 받을 값을 특정 클래스의 하위 클래스만 입력할 수 있도록 제한하는 것이 가능하다.

#### 참고자료

http://www.tcpschool.com/java/java_generic_concept
https://chchang.tistory.com/entry/C%EC%9D%98-template%EA%B3%BC-Java-generic-method-%EC%99%80%EC%9D%98-%EA%B3%B5%ED%86%B5%EC%A0%90%EA%B3%BC-%EC%B0%A8%EC%9D%B4%EC%A0%90
