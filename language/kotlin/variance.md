## variance (변성)

- 제너릭 클래스의 타입 앞에 `in`을 붙이면 반공변 (contravariance)
- `out`을 붙이면 공변 (covariance)
- 아무것도 붙이지 않으면 무공변(invariance)
- 기저타입(base type)이 같고, 타입 인자(type argument)가 다른 제너릭타입 간의 계층 관계를 설명하는 개념
- `List<String>` 에서 기저타입은 List, 타입 인자는 String

### 하위 타입 (Sub-type)

- 어떤 타입 A에 B를 넣어도 문제가 없는 경우 B는 A의 하위타입
- `String`은 `Any`의 하위타입
- `List<String>`은 `List<Any>`의 하위타입
- `MutableList<String>`는 `MutableList<Any>`의 하위타입이 아님. 변경의 여지가 있어서

### 무공변 (invariance)

- 타입 인자로 다른 클래스를 넣었을 때, 기존 타입의 상관관계가 무의미해지는 것
- 예를들어 `MutableList<String>`와 `MutableList<Any>`

### 공변 (covariance)

- A가 B의 하위타입일 때, `Base<A>`가 `Base<B>`의 하위타입인 경우
- 예를들어 `List<String>`와 `List<Any>`
- out을 븉이면 공변 클래스로선언 가능

```kt
class Head<out T: Animal>
```

### 반공변 (contravariance)

- 공변 클래스의 타입 관계와는 반대
- A가 B의 하위타입일 때, `Base<A>`가 `Base<B>`의 상위타입인 경우
- in을 븉이면 반공변 클래스로선언 가능

```kt
class Head<in T: Animal>
```

### 참고자료

- https://jaeyeong951.medium.com/kotlin-in-n-out-variance-%EB%B3%80%EC%84%B1-69204cbf27a1
