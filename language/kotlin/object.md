## object

object 키워드

- 주로 싱글턴 정의하는데 사용됨

**java의 싱글턴**

```java
public class Payroll {
    // 정적인 필드에 객체 저장
    private static Payroll instance = new Payroll();

    // 정적 메서드를 통해 객체 반환
    public static Payroll getInstance() {
        return instance;
    }

    // 생성자 private으로 설정
    private Payroll() {

    }
}
```

인스턴스를 생성해서 private 필드에 넣어두고 사용

**kotlin에서 객체 선언**

```kt
// 객체 선언도 클래스나 인터페이스 상속 가능
// object 키워드를 사용해 클래스 선언과 클래스에 속한 단일 인스턴스 선언
object CaseInsensitiveFileComparator: Comparator<File> {
    override fun compare(file1: File, file2: File): Int {
        return file1.path.compareTo(file2.path, ignoreCase = true)
    }
}

fun main() {
    val file1: File = File("/User")
    val file2: File = File("/User")
    println(CaseInsensitiveFileComparator.compare(file1, file2))

    val files = listOf(file1, file2)
    // 일반 객체를 사용할 수 있는 곳에서 싱글턴 객체 사용 가능
    println(files.sortedWith(CaseInsensitiveFileComparator))
}
```

- 인스턴스가 하나만 필요한 경우 유용하게 사용함
- 기존의 자바에서는 클래스 생성 후, 객체를 생성해서 사용하는 방식이었음
- 코틀린에서는 object키워드로 클래스와 클래스에 속한 단일 인스턴스를 선언할 수 있음

더보기

- [companion object]('./companion-object.md')

#### 참고자료

- https://velog.io/@changhee09/%EC%BD%94%ED%8B%80%EB%A6%B0-object-%ED%82%A4%EC%9B%8C%EB%93%9C
