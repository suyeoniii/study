### ETC

#### 레이블

- 람다나 익명함수에서 주로 사용됨
- 특정한 위치에서 바로 빠져나가거나, 특정한 위치에서 값을 반환할 때 사용됨
- `return@레이블`로 중첩된 루프나 함수에서 명시적으로 반환할 수 있음
- `break`, `continue`도 사용가능

```kt
val numbers = listOf(1, 2, 3, 4, 5)

numbers.forEachIndexed { index, value ->
    if (value == 3) {
        // 특정 조건에서 forEachIndexed를 빠져나가고자 할 때
        return@forEachIndexed
    }
    println("Index: $index, Value: $value")
}
```

### static

- 코틀린에서는 자바의 static을 지원하지 않음
- companion object (동반 객체)를 사용하면 정적 메서드, 정적 필드호출 같이 사용할 수 있음
