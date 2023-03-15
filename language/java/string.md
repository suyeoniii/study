## String, StringBuffer, StringBuilder

3가지 모두 문자열을 다룰 때 사용할 수 있다.

### String

String은 불변값이다.

```java
String str = "hello";   // String str = new String("hello");
str = str + " world";  // [ hello world ]
```

str값이 수정되는 것이 아닌, hello word라는 새로운 값을 가진 새로운 메모리영역을 가리키게 되고 기존 hello는 GC에 의해 사라짐

- 변하지 않는 문자열을 자주 읽어들이는 경우 좋은 성능을 가짐
- 수정, 삭제가 빈번한 경우 String을 사용하게 되면 힙메모리 부족 현상이 생길 수 있음
- String과 달리 StringBuffer, StringBuilder는 가변성을 가짐

### StringBuffer

StringBuffer는 동기화 키워드를 지원하여 멀티스레드 환경에서 안전함

### StringBuilder

동기화를 지원하지 않지만 단일 스레드에서의 성능은 StringBuffer보다 좋음

#### 참고자료

https://ifuwanna.tistory.com/221
