## 직렬화(Serializable), 역직렬화(Unserializable)

### 직렬화

메모리를 디스크에 저장하거나, 통신에 사용하기 위해 바이트 스트임으로 변경하는 것

### 역직렬화

직렬화된 객체 형식을 객체의 사본으로 다시 바꾸는 것

### 직렬화가 필요한 이유

주소에 있는 값을 참조하고 있는 경우 실제 값이 아닌 메모리 주소를 가지고 있게 된다.
이 때 데이터를 저장하거나 통신하기 위해서는 값이 필요한데
참조하고 있는 주소로부터 값을 가져와서 값 형식 데이터로 변환하기 위함이다.

### Serializable

자바에서 직렬화를 위해서는 Serializable 클래스를 상속받아 toString() 클래스를 오버라이드하면 된다.

```java
import java.io.Serializable;

public class Target implements Serializable {
    private String name;
    private int age = 0;

    public Target(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        // JSON 형태로 출력되게 toString() 재정의
        return String.format("{\"name\"=\"%s\",\"age\"=%d}", name, age);
    }
}
```

#### 참고자료

https://steady-coding.tistory.com/576
https://onlyfor-me-blog.tistory.com/494
