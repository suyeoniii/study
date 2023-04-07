## 싱글톤 패턴 (Singleton Pattern)

객체의 인스턴스가 오직 1개만 생성되는 패턴

### 예제

```java
public class Singleton {

    private static Singleton instance = new Singleton();

    private Singleton() {
        // 생성자는 외부에서 호출하지 못하도록 private 으로 지정해야 한다.
    }

    public static Singleton getInstance() {
        return instance;
    }

    public void say() {
        System.out.println("hi, there");
    }
}
```

### 사용하는 이유

- 메모리 절약
- 데이터 공유 용이함 - 싱글톤 인스턴스가 전역으로 사용되기 때문에 여러 인스턴스가 접근할 수 있음 (but 동시성 문제 발생할 수 있음)

### 주의할점

- 동시성 문제 - 멀티스레드 환경에서 발생할 수 있음. -> synchronized 키워드를 사용해야함
- 테스트 어려움 - 전역에서 사용되기때문에 테스트마다 초기화해주어야함
- 클라이언트가 구체 클래스에 의존 - new 키워드로 클래스 안에서 객체를 생성하므로

#### 참고자료

https://tecoble.techcourse.co.kr/post/2020-11-07-singleton/
