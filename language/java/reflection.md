## Reflection

구체적인 클래스 타입을 알지 못해도 클래스의 메소드, 타입, 변수에 접근할 수 있게 해주는 자바 API
런타임에 동적으로 객체를 생성하거나 메서드를 호출하는 등의 작업을 할 수 있다.

### 어떤 경우에 사용?

코드를 작성할 시점에는 어던 타입의 클래스를 사용할지 모르지만 런타임 시점에 지금 실행되고 있는 클래스를 가져와서 실행해야 하는 경우
-> 프레임워크, IDE 들에서 주로 사용됨

### 리플렉션 사용하여 할 수 있는 것

- 클래스 조회
- 필드 조회, 변경
- 생성자 조회, 인스턴스 생성
- 메서드 조회, 실행

### 예제

```java
public static void main(String[] args) {
    Class<Person> clazz = Person.class;
    try {
        Constructor<Person> constructor = clazz.getConstructor(String.class, int.class);
        Person newPerson = constructor.newInstance("호호맨", 20);
        Method toString = newPerson.getClass().getDeclaredMethod("toString");
        String result = (String)toString.invoke(newPerson);
        System.out.println(result);
    } catch (NoSuchMethodException | IllegalAccessException | InstantiationException | InvocationTargetException e) {
        e.printStackTrace();
    }
}
```

클래스 타입을 직접 넘기지 않고 어노테이션을 활용하여 특정 어노테이션이 붙은 모든 클래스를 가져오는 것도 가능하다.

#### 참고자료

https://ebabby.tistory.com/4
