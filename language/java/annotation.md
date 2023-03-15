## Annotation

Java 5 이상부터 사용가능함
소스 코드에 @기호를 붙여 사용함
소스 코드에 적용할 수 있는 메타 데이터의 일종임

### 용도

- 컴파일러에게 코드 작성 문법 에러를 체크하도록 정보 제공
- 소프트웨어 개발툴이 빌드나 배치시 코드를 자동으로 생성할 수 있도록 정보 제공
- 실행시(런타임시) 특정 기능을 실행하도록 정보 제공

### 내장 어노테이션

- @Override - 메서드가 오버라이드 됨을 나타냄
- @Deprecated - 더이상 사용되지 않는 메서드
- @SuppressWarning - 컴파일 경고를 무시
- @SafeVarargs - 제너릭같은 가변인자의 매개변수를 사용할 때의 경고 무시
- @FunctionalInterface - 함수형 인터페이스 지정

---

#### 어노테이션에 적용하는 어노테이션

- @Retention - 자바 컴파일러가 어노테이션을 다루는 시점을 결정 (컴파일 전, 클래스 참조시까지, 계속 참조 가능)
- @Documented - 해당 어노테이션을 Javadoc에 포함시킴
- @Target - 어노테이션이 적용할 위치 선택
- @Inherited - 어노테이션의 상속을 가능하게함
- @Repeatable - 연속적으로 어노테이션을 선언할 수 있게함

### 커스텀 어노테이션

```java
@Target({ElementType.METHOD})
@Retention(RetentionPolicy.RUNTIME)
public @interface MyAnnotation {
        String value() default "MyAnnotation : default value"
}
```

#### 참고자료

https://bangu4.tistory.com/199
