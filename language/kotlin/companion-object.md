## companion object

### 개념

- class 내부에서 사용함
- java의 static을 없애고, kotlin에서는 정적 멤버를 정의할 때 사용
- 클래스의 멤버 변수는 인스턴스 생성시에 생성됨. 공통으로 사용되는 경우 companion object 안에 정의하면, 클래스 로딩 시 생성됨
- 클래스 로딩 시 생성되므로, companion object 내부에 멤버변수는 둘 수 없음
- class 별로 1개만 사용 가능
- companion의 이름을 설정할 수 있음
- static과 다르게 객체라서, 변수에 할당할 수 있음
- `클래스이름.변수`, `클래스이름.메서드명` 으로 사용 가능

### 예시

```kt
class Student{
    var id: String? = null
    var name: String? = null

    companion object{
        val national = "korea"

        fun printnational(){
            println(national)
        }
    }
}

fun main(){
    println(Student.Companion.national)
    Student.Companion.printnational()

    val comp = Student.Companion
    println(comp.national)
    comp.printnational()

    val comp2 = Student
    println(comp2.national)
    comp2.printnational()
}
```

#### companion 이름 설정

```kt
class MyClass {
    companion object Factory {
        fun createInstance(): MyClass = MyClass()
    }
}
```

### 참고자료

- https://math-coding.tistory.com/214
- https://www.baeldung.com/kotlin/companion-object
