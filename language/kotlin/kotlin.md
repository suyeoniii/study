## Kotlin

### Kotlin 이란?

- Jetbrains에서 만든 프로그래밍 언어
- Java가 사용되는 모든 환경에서 사용가능함
- Java로 컴파일되어 실행됨
- 모든 개발언어를 Kotlin으로 대체할 수 있는 것을 목표로 하고 있음

### Kotlin 특징 (Java의 차이점)

- 간결한 문법 (세미콜론 생략, 타입 추론, new 키워드 생략 등)
- Null 안정성
  - Null 체크를 도입하여 런타임에서 Null관련 오류를 줄일 수 있음
- 가변, 불변 변수 구분
  - 가변: `var`
  - 불변: `val`
- 람다 표현식 지원
- 스트림 API 지원
- 암시적 형변환을 지원하지 않음

### Kotlin 기본문법

잘 모르는 것만 정리함

#### is 타입 비교

```kt
fun main(){
    var a: Any = 1

    if(a is Int){
        println("int")
    }

    if(a is String){
        println("string")
    }
}
```

#### when (switch와 유사함)

```kt
fun main(){
    exWhen(2)
}
fun exWhen(a: Any){
    when(a){
        1 -> print(a)
        "awd" -> print(a)
        else -> print(a)
    }
}
```

#### for문

```kt
fun main(){
    for(i in 0..3){
        print(i)
        print(" ")
    }

    println()

    for(i in 3 downTo 0){
        print(i)
        print(" ")
    }

    println()

    for(i in 0..5 step 2){
        print(i)
        print(" ")
    }

    println()

    for(i in 'a'..'e'){
        print(i)
        print(" ")
    }
}

/* 결과
0 1 2 3
3 2 1 0
0 2 4
a b c d e
*/

```

#### @label

@ label : 반복문에 라벨이름@을 달고 break, continue문에 @라벨이름을 달면 break, continue가 라벨이름으로 가 실행

```kt
fun main(){
    awd@for(i in 0..10){
        for(j in 0..10){
            if(i ==0 && j == 3){
                break@awd
            }
            println("$i, $j")
        }
    }
}

/* 출력
0, 0
0, 1
0, 2 */
```

#### 생성자

클래스의 생성자를 따로 만들어주지 않아도 객체 생성 시 속성값을 넣어주면 됨

#### init

생성자를 만들지 않으면 구문을 추가할 수 없음
생성자로 객체를 생성한 뒤 구문이 실행되게 할 수 있음

```kt
fun main(){
    var a = Prs("awd", 23)

}

class Prs(var name:String, val birth:Int){
    init{
        println("${this.name} ${this.birth}")
    }
    init{
        println(1)
    }
}
```

#### contructor (보조 생성자)

오버로딩 생성자 생성

```kt
fun main(){
    var a = Prs("awd")

}

class Prs(var name:String, val birth:Int){
    //this를 사용해 기본 생성자로 값을 넘겨줘야 한다.
    constructor(name:String): this(name, 23)
    init{
        println("${this.name} ${this.birth}")
    }
}
```

#### 상속

- 부모 클래스에 open 키워드가 있어야 상속 가능
- 함수 override 시 override 키워드 사용
- override하는 부모의 메서드에도 open 키워드 필요

```kt
fun main(){
    var dog = Dog("a", 12)
    dog.introduce1()
    dog.introduce()
}

open class Animal(var name:String, var age:Int, var type:String){
    open fun introduce(){
        println("${this.name} ${this.age} ${this.type}")
    }
}
class Dog(var name1: String, var age1: Int) : Animal(name1, age1, "강아지"){
    fun introduce1(){
        super.introduce()
    }

    override fun introduce() {
        println("override")
    }
}
```

#### 인터페이스

- 추상함수뿐아니라 일반함수도 작성할 수 있음

#### 접근제한자

- 자바와 종류는 동일
  아무것도 안쓰면 기본값 - Java는 `protected`, Kotlin은 `public`

#### 고차함수/람다함수

- 함수를 인자로 넘길 수 있음 (::함수이름 으로 넘겨줌)
- 결과값으로 반환받을 수 있음

```kt
fun main(){
    b(::a)	//함수를 넘겨줄때 ::을 붙인다.

    //람다 함수로 작성된 c
    //(입력 타입)->반환 타입 = {변수이름: 입력타입 -> 구문}
    //아래 두개의 c, d처럼 타입 생략 가능
    var c: (String)->Unit = {s -> println(s) }
    var d = {s: String -> println(s) }
    var e = {s: String -> s }		//s를 반환하라는 소리
    var f = {				//인자가 없는 경우
        println("xzcxc")
    }
    var g : (String)->Unit = {println(it)}  //인자가 하나일 경우 it 키워드 사용

    c("zxc")
    d("sss")
    println(e("ccc"))
    f()
    g("qqq")
}

fun a(str: String): String{
    return str
}
//fun이라는 고차함수
//이름: (입력받을 타입)->(리턴타입) 즉, a라는 함수와 같으면 된다.
fun b(funs: (String)->String){
    //가져온 함수에 인자를 넣어 실행
    println(funs("awds"))
}

```

#### 스코프 함수

따로 정리

#### 옵저버(Observer) 패턴

```kt
fun main() {
    EventPrinter().start()
}
interface EventListener{
    fun onEvent(count: Int)
}
class Counter(var listener: EventListener){
    fun count(){
        for(i in 0..20){
            if(i % 5 == 0){
                listener.onEvent(i)
            }
        }
    }
}
class EventPrinter: EventListener{
	//이벤트 함수
    override fun onEvent(count: Int) {
        println(count)

    }
    fun start(){
        var count = Counter(this)
        count.count()
    }
}

/*
출력
0
5
10
15
20
*/
```

#### 타입 캐스팅 (as)

- is는 일시적 캐스팅
- as는 타입을 바꿔버림

```kt
var c = b as Cola
```

#### Generic

```kt
val t: T
```

#### Collection List

- listOf: 수정 불가능
- mutableListOf: 수정 가능

### String function

```kt
fun main() {
    val test = "a.b.c.d"
    println(test.length)

    var spl = test.split('.')
    println(spl)

    //배열 값들을 string 으로 합쳐줌
    println(spl.joinToString())
    println(spl.joinToString("-"))

    println(test.substring(0..2))

    //시작 단어 bool
    println(test.startsWith("a."))
    //끝 단어 bool
    println(test.endsWith(".d"))
    //포함 단어 bool
    println(test.contains("b.c"))
}

/*
출력
7
[a, b, c, d]
a, b, c, d
a-b-c-d
a.b
true
true
true
*/

```

#### Null 처리

- ?, ?:, !! 등으로 처리 가능

```kt
fun main() {
    val a = listOf<String?>("awd", null, "zxc")
    val c = mutableListOf<String>()
    val e = mutableListOf<String>()
    val f = mutableListOf<String>()

    for(b in a){
        //b가 null이면 .let구문을 실행하지 않는다.
        b?.let { c.add(it) }

        //b가 null이면 default값이 대신 추가된다.
        e.add(b?:"default")
    }
    println(c)
    println(e)

    for(b in a){
    	//b가 null인 것을 의도적으로 방치->오류 발생
        f.add(b!!)
    }
    println(f)
}

```

#### infix

함수를 연산자처럼 사용가능

```kt
fun main() {
    println("awd" strSum 1)
    println("awd".strSum(2))

    println(3 mul 4)
    println(3.mul(4))
}

//infix fun (this에 해당되는 타입).함수이름(인자이름: 타입): 반환 = 구문
infix fun String.strSum(x: Int): String = this + x
infix fun Int.mul(x: Int): Int = this * x
```

#### lateinit

기본 자료형 제외 (String은 가능)하고 객체 초기화를 나중에 할 수 있음

```kt
lateinit var a: String
```

#### lazy

변수가 사용될때 초기화 할 수 있게해줌

```kt
fun main() {
    val num: Int by lazy {
        println("초기화")
        7
    }
    println("start")
    println(num)
    println(num)
}
```

#### 참고자료

https://cjw-awdsd.tistory.com/20
