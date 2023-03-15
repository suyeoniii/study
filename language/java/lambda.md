## 람다 (Lambda)

람다 함수는 이름이 없는 익명 함수의 한 종류이다.
함수를 값으로 사용할 수도 있고, 파라미터로 전달 및 변수에 대입하는 것이 가능하다.

- 매개변수 화살표(->)를 함수몸페로 이용하여 사용할 수 있음
- 함수 몸체가 단일 실행문인 경우 중괄호 생략가능
- 함수몸체가 return문으로만 구성되어 있는 경우 중괄호 생략 불가

### 장점

- 코드의 간결성
- 지연연산 수행 (불필요한 연산 최소화)
- 병렬처리 가능 (멀티스레드 사용)

### 단점

- 불필요하게 사용되는 경우 오히려 가독성이 떨어질 수 있음
- 무명함수는 재사용이 불가능
- 재귀로 만들기 부적합

```java
public String hello() {
    return "Hello World!";
}
```

```java
() -> "Hello World!";
```

### 함수형 인터페이스

함수를 변수처럼 선언할 수 있음
함수형 인터페이스 내부에 추상 메서도 1개를 선언하고 `@FunctionalInterface`를 붙여주면 됨

```java
@FunctionalInterface
interface MyLambdaFunction {
    int max(int a, int b);
}

public class Lambda {

    public static void main(String[] args) {

        // 람다식을 이용한 익명함수
        MyLambdaFunction lambdaFunction = (int a, int b) -> a > b ? a : b;
        System.out.println(lambdaFunction.max(3, 5));
    }

}
```

#### 참고자료

https://khj93.tistory.com/entry/JAVA-%EB%9E%8C%EB%8B%A4%EC%8B%9DRambda%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B4%EA%B3%A0-%EC%82%AC%EC%9A%A9%EB%B2%95
https://mangkyu.tistory.com/113
