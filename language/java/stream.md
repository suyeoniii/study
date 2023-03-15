## Stream

Java8부터 지원되기 시작했다.
컬렉션에 저장된 엘리먼트들을 순회하면서 처리할 수 있는 코드패턴이다.

```java
ArrayList<String> list = new ArrayList<String>(Arrays.asList("a", "b", "c"));

for (String value : list) {
    if (StringUtils.equals(value, "b")) {
        System.out.println("값 : " + value);
    }
}
```

```java
ArrayList<String> list = new ArrayList<String>(Arrays.asList("a", "b", "c"));

list.stream()
    .filter("b"::equals)
    .forEach(System.out::println);
```

- 스트림을 사용하기 위해 스트림 객체를 생성해야한다.

```java
List<String> list = Arrays.asList("a", "b", "c");
Stream<String> stream = list.stream();
```

- 스트림 데이터 가공
  - filter, map, flatMap, sorted, peek 등
- 스트림 결과 생성
  - .sum(), .count(), reduce(), collect(), foreach() 등

#### 참고자료

https://hbase.tistory.com/171
